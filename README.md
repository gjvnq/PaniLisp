# paniLISP
My custom LISP dialect. Named after "Espaço de Vivência Prof Horácio C. Panepucci" at IFSC-USP

## Inspirations

  * Clojure.
  * Mathematica.
  * Haskell.

## Unique features

  * Heavy Unicode usage.
  * Near mathematical treatment for functions. Ex: ```⟺(^(^(x a) b)) ^(x *(a b)))```
  * Support for non indo-Arabic number systems: ```14i = XIVi = ��i = 𒌋𒐉i``` (Roman numerals only in upper case)
  * Number literals for complex and quaternions: ```5i```, ```3.14E9j```, ```-7E-8k```
  * Functions and lists have separate but similar syntax: ```*(3 2)``` gives 6, ```(* 3 2)```is a list that begins with a function, ```eval(* 1 2)``` gives 6.
  * Separation between pure and impure functions: Ex: ```⧓(...)``` (subroutine with potential side effects, bow tie reminds me of business), ```⟼(...)``` (pure function with no side effects).
  * Keywords (mainly for map keys): ```#number```, ```#real```, ```#my long keyword with spaces#```
  * Sets: ```{1 2 3 4 5}```
  * Maps: ```{#a:1 #b:2 #c:3 #d:4 #e:5}```
  * Uncertainties: ```6.67408(31)E-11 = ⌇(6.67408E-11 0.00031E-11)```
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
    ⟺(sum(a<Number> b<Number>) sum(b a))
    ⟺(sum(0 b<Number>...) sum(b...))
  ```

## Built-in Values

  * ```PI = π = 3.14159265359```
  * ```EULER = 𝑒 = 2.71828182845```
  * ```EULER-MASCHERONI = ℇ = 0.57721566490```
  * ```GRAVITATIONAL-CONSTANT = 𝐺 = 6.67408(31)E-11```
  * ```BOOLEANS = 𝔹 = (⓿ ❶)``` list of boolean values.
  * ```NATURALS = ℕ = (0 1 2 3 ...)``` list of natural numbers, including zero.
  * ```INTEGERS = ℤ = (0 1 -1 2 -2 3 -3 ...)``` list of integer numbers.
  * ```PRIMES = ℙ = (2 3 5 7 11 ...)``` list of (positive) prime numbers.
  * ```RATIONALS = ℚ = (0 1 -1 2 -2 3 -3 ...)``` list of rational numbers in Cantor's diagonal.
  * ```REALS = ℝ = (0 0.001 -0.001 0.002 -0.002 0.003 -0.003 ...)``` list of "real" numbers, i.e. floats in order just like ```ℤ``` (in this example, our "float" data type is limited to three decimal places).
  * ```COMPLEXES = ℂ``` list of complex numbers just like ```ℝ```.
  * ```QUATERNIONS = ℍ``` list of quaternions numbers just like ```ℂ```.
  * ```procedure = ⧓``` returns a procedure (impure function).
  * ```function = ⟼``` defines a function.
  * ```identity = ⟺``` defines a function identity.
  * ```define = ≜``` gives a name for a value.
  * ```in = ∈``` returns a boolean telling if the value is in a list.
  * ```subset = ⊂``` returns a boolean telling if a list is contained in another list.
  * ```apply = Ⓐ``` applies a function individually over a list of values.
  * ```reduce = Ⓡ``` applies a two-array function over a list of values reducing the list to a single value.
  * ```filter = Ⓕ``` given a binary function and a list, returns a list with the values that pass such a function.
  * ```root = √``` return a the n-th root of the input. Ex: ```√(-100) = 10i```, ```√(2 -100) = 10i```, ```√(3 -8i) = 2i```
  * ```roots = √s``` return a list of n-th roots of the input. Ex: ```√(2 100) = (10; -10)```, ```√(3 -8i) = (2i +(-(√(3)) -1i) +(√(3) -1i))```
  * ```# = nth```
