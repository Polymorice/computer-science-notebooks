# introduction to Scheme programming

lecture source

content creator: [Andy Balaam](https://www.youtube.com/channel/UCSOmE2-jMaw8EKvxGpoBsww)

[Scheme series of 7 videos](https://www.youtube.com/playlist?list=PLgyU3jNA6VjRMB-LXXR9ZWcU3-GCzJPm0)

notes written by Horace Z.

from 2022/03/09 to 2022/03/

# 1. feel the cool

## features

### simple

designed for teaching: "a language for describing processes"

almost minimally simple syntax

only one thing you can do

`(operator operand1 operand2 ...)`

example

```scheme
; arithmetics
(+ 3 4)
(* 3 4)
; nested arithmetics
(+ 5 (* 2 2))
; variable
(define foo 3)
(* foo 4)
; function
(define (square x) (* x x))
(square 4)
(+ (square 2) (square 3))
; flow control
(define (abs x)
  (if ( < x 0)
    (- x)
    x))
(abs -3)
(abs 3)
```

only one data structure

lists

`(list value1 value2 value3 ...)`

example

```scheme
(sort (list 4 6 5))
(length (list 1 2))
```

both of the above are the same

### weird

functional (sort of)

example

```scheme
; list functions
(define my-list (list 1 2 3 4 5))
(car my-list) ; returns 1
(cdr my-list) ; returns (2 3 4 5)

; recursion
(define (sum list-of-values)
  (if (= 1 (length list-of-values))
    (car list-of-values)
    (+ (car list-of-values)
      (sum (cdr list-of-values)))))
(sum (list 5 6 7))
```

dynamic typing

example

```scheme
(define (improved-code q) (* q 2))
(define code-quality 4)
(improved-code code-quality)
(define code-quality "poor")
(improved-code code-quality) ; error message: expects type as 1st argument
```

functions are values

example

```scheme
(define (double value) (* 2 value))
(define (apply-twice fn value) (fn (fn value)))
(apply-twice double 2) ; returns 8
```

code is data, data is code

example

```scheme
(define (swap-2-3 x)
  (list (car x)
    (caddr x)
    (cadr x)))

(swap-2-3 (list 1 2 3)) ; returns (1 3 2)
(swap-2-3 (list "a" "b" "c")) ; returns ("a" "C" "b")

(define four-over-two (list '/ 4 2))
four-over-two ; returns (/ 4 2)
(eval four-over-two) ; returns 2
(define switched (swap-2-3 four-over-two))
switched ; returns (/ 2 4)
(eval switched) ; returns 1/2
```

### cool

generics without all that syntax

example

```scheme
(sort (list 5 4 3 2 1) <) ; returns (1 2 3 4 5)
(sort (list "abc" "a" "ab") string<?) ; returns ("a" "ab" "abc")
```

generating code is easy

example

```scheme
(define (d-zero name)
  (list 'define (string->symbol name) 0))
(d-zero "a") ; returns (define a 0)
(define (d-zero-list names) (map d-zero names))
(define mycode (d-zero-list (list "a" "b" "c")))
mycode ; returns ((define a 0) (define b 0) (define c 0))
(for-each eval mycode)
a ; returns 0
b ; returns 0
c ; returns 0
```

metaprogramming is just ... programming

example

```scheme
(define (double x) (* x 2))
(define (square x) (* x x))
(define (apply-twice fn x)
  (fn (fn x)))
(define (quadruple x) (apply-twice double x))
(define (pow-4 x) (apply-twice square x))
(quadruple 3) ; returns 12
(pow-4 3) ; returns 81
```

macros are (almost) just more code

macros - write your own language

there are a lot of brackets

you much acknowledge the power of the brackets

# 2.pairs, lists and recursion

## pairs

example

```scheme
(cons 1 2)
(cons (cons 1 2) 3)
(define foo (cons 1 2))
foo ; returns (1 2)
(car foo) ; returns 1
(cdr foo) ; returns 2
```

## lists

`cons` constructs lists

example

```scheme
(cons 1 null) ; returns (1)
(define bar (cons 1 null))
bar ; returns (1)
(car bar) ; returns 1
(cdr bar) ; returns (), which is null
null ; returns ()
(con 1 (cons 2 null)) ; returns (1 2)
(cons 1 (cons 2 (cons 3 null))) ; returns (1 2 3)
(define mylist (cons 1 (cons 2 (cons 3 null))))
mylist ; returns (1 2 3)
(car mylist) ; returns 1
(cdr mylist) ; returns (2 3)
(cadr mylist) ; returns 2, it does a cdr then car
(caddr mylist) ; returns 3, it does cdr twice then car
(equal? (list 1 2 3) mylist) ; returns #t
(list-ref (list "a" "b" "c") 1) ; returns "b"
(list-ref (list "a" "b" "c") 2) ; returns "c"
```

## "loops"

using recursion to recreate loop

example

```scheme
; how do we implement `list-ref`
(define (my-list-ref lst n)
  (if zero? n)
    (car lst)
    (my-list-ref (cdr lst) (- n 1))
  )
)
(my-list-ref (list "a" "b" "c") 1) ; returns "b"

```

## map

map applies procedure to all elements of a list

example

```scheme
(define baz (list 1 2 3))
(define (double x) (* x 2))
(map double baz) ; returns (2 4 6)
(define (double-all x) (map double x))
(double-all baz) (2 4 6)
; how do we implement map
(define (my-map fn lst)
  (if (null? lst)
    null
    ; using cons to construct list
    (cons (fn (car lst)) (my-map fn (cdr lst)))
  )
)
```

## fold

`foldr` applies the function with `ar1` and each element of the list from the last to the first

example

```scheme
(define qux (list 1 2 3 4))
(foldr + 0 qux) ; returns 10
(foldr + 2000 qux) ; returns 2010
(foldr * 1 qux) ; returns 24
(foldr * 0 qux) ; returns 0
; how do we implement foldr
(define (my-foldr fn start lst)
  (if (null? lst)
    start
    (fn (car lst) (my-foldr fn start (cdr lst)))
  )
)
(my-foldr + 0 qux) ; returns 10
(my-foldr * 1 qux) ; returns 24
```

# closure

## functions in functions

example

```scheme
(define (sum-of-square x y)
  (define (square a)
    (* a a))
  (define (sum b c)
    (+ b c))
  (sum (square x) (square y)))

```

## using outer symbols

example

```scheme
; assert-equal function
(define (assert-equal a b)
  (define (print-error)
    (display a)
    (display " is not equal to ")
    (display b)
    (newline))
    (if (not (equal? a b)) (print-error) null))
(assert-equal 3 (+ 1 2)) ; returns null
(assert-equal 3 (+ 2 2)) ; returns 3 is not equal to 4
; circle-details function
(define (circle-details r)
  (define pi 3.14)
  (define (area) (round (* pi r r)))
  (define (circum) (round (* 2 pi r)))
  (list (area) (circum))
)
(circle-details 3) ; returns (28.0 19.0)
```

## returning functions

example

```scheme
(define (make-add-one)
  (define (inc x) (+ 1 x))
  inc) ; returns inc
(make-add-one) ; returns #<procedure:inc>, returns the function inc
(define myfn make-add-one)
(myfn 2) ; returns procedure make-add-one: expects no arguments, given 1
; it actually defines the symbol myfn to be the symbol make-add-one
(define myfn (make-add-one)) ; now myfn can call function make-add-one
(myfn 2) ; returns 3
```

## closures

example

```scheme
(define (make-add-x x)
  (define (add-x y) (+ x y))
  add-x)
```

## uses

## discussion
