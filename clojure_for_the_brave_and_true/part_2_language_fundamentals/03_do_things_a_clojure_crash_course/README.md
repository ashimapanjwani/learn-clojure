# Chapter 3: Do Things: A Clojure Crash Course


## Topics Covered

* Syntax
* Data Structures
* Functions


### Syntax

#### Forms

Clojure recognizes two kinds of structures:

* Literal representations of data structures (like numbers, strings, maps, and vectors)
* Operations

The term form (sometimes called expression) is used to refer to valid code. Clojure evaluates every form 
to produce a value. These literal representations are all valid forms:
```clojure
1
"a string"
["a" "vector" "of" "strings"]
```
Literals don’t actually do anything on their own and are generally used in operations. Operations are how 
you do things. All operations take the form opening parenthesis, operator, operands, closing parenthesis:
```clojure
(operator operand1 operand2 ... operandn)
```
Clojure uses whitespace to separate operands, and it treats commas as whitespace. Here are some example 
operations:
```clojure
;; Addition
(+ 1 2 3)
; => 6

;; String concatenation
(str "It was the panda " "in the library " "with a dust buster")
; => "It was the panda in the library with a dust buster"
```
Clojure’s structural uniformity is different from other languages, where different operations might have 
different structures depending on the operator and the operands.
By comparison, Clojure’s structure is very simple and consistent. No matter which operator you’re using or 
what kind of data you’re operating on, the structure is the same.

#### Control Flow
