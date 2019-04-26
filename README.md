# PaniLisp
My custom LISP dialect. Named after "Espaço de Vivência Prof Horácio C. Panepucci" at IFSC-USP

## Inspirations

  * Clojure.
  * Mathematica.
  * Haskell.

## Unique features

  * Heavy Unicode usage.
  * Near mathematical treatment for functions. Ex: ```⟼⟼(^(^(x a) b)) ^(x *(a b)))```
  * Supportt for non indo-arabic number systems: ```14i = XIVi = 𓎆𓏽i = 𒌋𒐉i``` (roman numerals only in upper case)
  * Number literals for complex and quaterions: ```5i```, ```3.14E9j```, ```-7E-8k```
  * Functions and lists have separate but similar syntax: ```*(3 2)``` gives 6, ```(* 3 2)```is a list that begins with a function, ```eval(* 1 2)``` gives 6.
  * Separation between pure and impure functions: Ex: ```⧓(...)``` (subroutine with potential side effects, bowtie reminds me of business), ```⟼(...)``` (pure function with no side effects).
  * Keywords (mainly for map keys): ```#number```, ```#real```, ```#my long keyword with spaces#```
  * Sets: ```{1 2 3 4 5}```
  * Maps: ```{#a:1 #b:2 #c:3 #d:4 #e:5}```
  * Pattern matching function definition:
  ```
    ≜(! ⟼(
        0 1
        n<Integer> *(n !(- n 1))
    ))
    ≜(sum ⟼(
        (a<Number> b<Number>) +(a b) // sum two numbers
        (a<Number> b<Number>...) +(a sum(first(b) tail(b)) // sum more than two numbers
    ))
    ⟼⟼(sum(a<Number> b<Number>) sum(b a))
    ⟼⟼(sum(0 b<Number>...) sum(b...))
  ```
