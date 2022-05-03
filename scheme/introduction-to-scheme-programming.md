# introduction to Scheme programming

lecture source

content creator: [BP Learning](https://www.youtube.com/c/BPLearningTV/videos)

[Introduction to Scheme Programming](https://www.youtube.com/watch?v=6k78c8EctXI)

notes written by Horace Z.

from 2022/03/02 to 2022/03/09

# introduction

everything in scheme is a function

there is no basic mathematical operations, addition and subtraction are all functions

all functions are wrapped in parenthesis `()`

function name and function definition are separate entities

example, factorial function

```scheme
(define factorial
	(lambda (x)
		(if (< x 1)
			1
			(* x (factorial (x - 1)))
		)
	)
)
```

## why Scheme is a great language

- Scheme is a perfect language to test out new ideas in programming style or programming languages
- Scheme attempts to remove syntax as much as possible
- Scheme attempts to remove everything as much as possible
  Scheme is very minimalistic, equips users with small number of powerful tools
- Scheme attempts to equivocate between code and data
  reflection is part of lot of languages, there are a lot of custom functions and data structures comes with it
  in Scheme, code and data are the same structure, lists of items, thus easier to make programs that manipulate and generate other programs
- Scheme attempts to put only a few tools in your hands, but verifies that they are the most powerful tools possible
- Scheme is the inspiration for most modern programming practices and ideas
  Scheme doc is very short

## short history of Scheme

- in the beginning it was ... LISP!
  - one of the oldest high-level programming languages (1958)
  - based on the Lambda Calculus instead of Turing Machines
    conceptual difference, functional thinking and
- Scheme originated as a tiny LISP interpreter
- developed through a series of papers from MIT’s Artificial Intelligence Lab on topics such as
  - developing cheaper mechanisms for function calls
  - developing simplified mechanisms for complex control flow
  - rethinking the way that compliers process languages constructs
- Scheme straddles the fence between functional, declarative and procedural models
- Scheme is standardized through a series of ‘reports’ on language, RNRS
- the current Scheme is R7RS, but the most implemented is R5RS

## JavaScript and Scheme

- Brendan Eich was originally hired by Netscape to build Scheme into the browser
- the introduction of Java into Netscape meant that Netscape needed its extension language to be more Java-like
- Eich then built the first version of JavaScript in 10 days, using many concepts of Scheme
- if someone of these concepts seem familiar to you, it is because they were borrowed from Scheme

## why you should learn Scheme

- if will enable you to read great classic books about computer programming:
  - how to design programs
  - structure and interpretation of computer science
  - programming languages: an interpreter based approach
  - the little schemer
  - the seasoned schemer
- it will help your computer programming imagination
  - what is the relationship between code and data
  - what is the purpose of syntax
  - what can we do to pare down features to a minimal set?
  - how do we make things powerful without making them cluttered?
- it will help you understand modern languages better

# Scheme syntax

the goal of Scheme syntax is to have as little of it as possible

## procedure call

basic procedure call

`(procedure-name arg1 arg2 arg3)`

parentheses starts and end call

arguments separated by spaces

dashes can be part of names

most things in Scheme are procedure calls, even arithmetic

`(* (- 5 3) (+ 1 9))`

the interior function calls are evaluated first

these are then used as arguments to the outer function

## if statement

if statements have the same look as procedure calls, but are simply evaluated differently

basic if statement syntax (spacing is just for demonstration):

```scheme
(if
	condition-check-procedure
	then-procedure
	else-procedure
)
```

example

```scheme
(if (< x 3)
	(display "I am a small number")
	(display "I am a big number")
)
```

## lists of values

everything in Scheme is a list, even the code

to interpret a group of values as a list (instead of as a procedure call), to put a single quote in front of them → this is called quoting

lists can contain any data type

example

```scheme
'(1 2 3) ; returns the list (1 2 3)
'(aa bb cc) ; returns the list (aa bb cc)
; list of different data types
'(1 bb "hello")
; list can contain lists
'(1 (aa bb ("hello" "there") 23))
```

individual values can also be quoted

```scheme
a ; evaluates a according to the active variables
'a ; returns the symbol a
```

## list operations

define x to be a list of values

`(define x ‘(1 2 3))`

get the first element of x

`(car x) ; returns 1`

get all values of x except the first

`(cdr x) ; returns (2 3)`

construct a list from individual values

`(cons 1 (cons 2 (cons 3 ‘()))) ; returns the list (1 2 3)`

## local variables

local variables are defined with `let` commands

most common `let*`

```scheme
(let*
	(
		(var1 23)
		(var2 55)
		(var3 (+ var1 var2))
	)
	(display "variable var3 is ")
	(display var3)
)
```

if you want to allow your variable initializations to be parallelized, just use `let`

if you want to be able to recursively refer to your variable name during initialization, use `letrec`

the value of the whole `let` expression is the value of the last evaluated procedure

## create a function

the keyword lambda creates a function

```scheme
(lambda
	parameter-list
	function-body
	more-function-body
)
```

the last expression evaluated is the return value of the function

lambda functions are born anonymous, but can be given names with `let`, `set!` or `define`

example

```scheme
; example using define
(defien double-me (lambda (x) (* x 2))
(double-me 23) ; yields 46

; example using let
(let* (
		(double-me (lambda (x) (* x 2)))
		(my-value 23)
		(result (double-me my-value))
	)
	(display "doubling yields:")
	(display result)
)
(double-me 23) ; throws an error because double-me is not defined here
```

## miscellaneous syntax

booleans `#t` and `#f`

`‘()` is the empty list

functions that yield side-effects are marked with a `!`

example: `set!` modifies a variable

`;` are used for single-line comments, `#|...|#` are used for multi-line comments

# recursion

## Scheme wants you to use recursion

many (actually all) routines can be written either procedurally (while loop) or recursively

procedural routines talk about the method of how something is done

recursive routines talk about the logic of how something is done

Scheme wants you to focus on the logic, and make everything recursive

## recursion vs. procedure

in a Scheme program, you usually write code that does three things:

check to see if we are done

perform a single task well

narrow a bigger task to a smaller task

by encapsulating into a recursive program, we can

eliminate problems with variables that we left and forgot to set (every variable of every iteration is explicitly set)

explicitly mark control-handling vs. task-handling even for non-standard flows

create a function that is easier to prove correctness, since all of the in-and outflows are marked

example

```scheme
(letrec
	(
		(eat-apples (lambda (apple-index num-apples)
			(if (>= apple-index num-apples)
				#f ; do nothing
				(begin
					(eat-single-apple apple-index)
					(eat-apples (+ apple-index 1) num-apples)
				)
			)
		)
	)
	(eat-apples 0 100)
)
```

## recursion in Scheme is not expensive

Scheme was the first language to introduce tail-call elimination

in tail-call elimination, a function that ends with a recursive call does not eat stack space

this is done by converting the last function call in a function into a variable rename + GOTO

thus, tail-calls are not expensive

this eliminates many distinctions between writing elegant code and writing optimized code

tail-call makes debugging harder, because it removes stack frames

## tail call optimization support in various languages

| support | none      | it depends  |
| ------- | --------- | ----------- |
| Scheme  | C#        | Lisp        |
| Scala   | Java      | C           |
| F#      | Python    | Objective-C |
| Lua     | JS(<=ES5) | JS(>=ES6+)  |

# closure

## what are closures?

closures allow for function-generating functions

if a function is created in a local context, all calls (present and future) to that function will be performed in the same local context

this is true even if that context has been returned from

essentially, a function retains a pointer to the stack frame that originally created it

example

```scheme
(define make-counter
	(lambda (starting-number)
		(let (
					(next-value ()
						(lambda ()
							(set! starting-number (+ starting-number 1)
							starting number
						)
					)
				)
				next-value
			)
	)

(define my-counter(make-counter 10))
(define my-otherocounter (make-counter 100))
(my-counter) ; returns 11
(my-other-counter) ; returns 101
(my-other-counter) ; returns 102
(my-counter) ; return 12
```

## objects are just closures

example

```scheme
(define  make-counter-object
	(lambda (starting-number)
		(let* (
						(original-value starting-number)
						(next-value
							(lambda ()
								(set! starting-number (+ starting-number 1))
								starting-number
							)
						)
						(reset-value
							(lambda ()
								(set!  starting-number original-value)
							)
						)
					)
					(list (list 'next next-value) (list 'reset reset-value))
			)
		)
)

(define c (make-counter-object 10))
((cadr (assoc 'next c))) ; returns 11
((cadr (assoc 'next c))) ; returns 12
((cadr (assoc 'next c))) ; returns 13
((cadr (assoc 'reset c))) ; resets counter
((cadr (assoc 'next c))) ; returns 11
```

# macro

## extending the language

since Scheme syntax is so bare, syntax in Scheme usually refers to special list orderings

example, define, lambda, set!, let

```scheme
; syntax = having customized meanings for parentheses
(let
	(
		(x 3)
		(y 4)
	)
	(+ x y)
)

; let is a special syntax for the following
(
		(lambda (x y)
			(+ x y)
		)
		3 4
)

```

## Scheme macros

Scheme allows language extension via macros

Scheme macros are hygienic - they are guaranteed not to cause accidental overlap of identifiers

- i. e. if my macro expanded to include a temporary variable `x`, even if the things being expanded included an `x`, everything would be renamed to avoid unintentional collisions

macros can be used to modify Scheme to essentially work like any other programming language

however, macros can't generally be used to do things like type safety

macros allow for specialized, domain-specific language to be built

## adding classes to Scheme

example

```scheme
; class definition
(class Counter
  (
    (attr value 0)
    (attr skip 1)
  )
  (
    (method (next)
      (set! value (+ value skip))
      value
    )
    (method (set-value newval)
      (set! value newval)
    )
    (method (set-skip  newskip)
      (set! skip newskip)
    )
  )
)

; class usage
(let
  (
    (c (Counter))
  )
  (display ((c 'next)))
  (newline)
  (display ((c 'next)))
  (newline)

  ((c 'set-value) 10)
  ((c 'set-skip) 5)

  (display ((c 'next)))
  (newline)
  (display ((c 'next)))
  (newline)
  )
```

## creating custom syntax

example

```scheme
(define-syntax class
  (syntax-rules (attr method)
    (
      (class class-name
        ((attr attr-name initial-val) ...)
        ((method (meth-name meth-arg ...) body...) ...)
      )
      (define class-name
        (lambda ()
          (let*
            (
              (attr-name initial-val)
              ...
              (vtable
                (list
                  (cons (quote meth-name) (cons (lambda (meth-arg ...) body ...) '()))
                  ...
                )))
              (lambda (methname)
                (cadr (assoc methname vtable))
              )))))))
```

## building a language with Scheme

Scheme does not have a real syntax

- its syntax is just lists-of-lists
- you are just writing your own parse trees

Scheme allows you to write your own macro customizations

parse tree + macros + functions = the ability to build any languages

## Python as Scheme macros

example show Python implemented in Racket

## Scheme options

Chicken Scheme - compiles to native (or C) (twice as fast as Ruby 2.3, twice as slow as C++)

Guile - focuses on being an extension language

Racket - very nice GUI for development, lots of extensions

Chibi - ultra-small static library

Wisp - gets rid of the parentheses

# summary

minimalist but powerful

focus on recursion (tail-call elimination)

closures for encapsulation

code and data are treated equivalently

coherent macro system for language customization

Scheme is a language where just a few parts lend to a powerful bag of tools
