# Haskell Relearning Exercises

Use these with GHCi. For each function, write the type signature first, then the definition, then test it with two or three examples.

## 1. Warm-Up: Expressions and Types

Predict the type of each expression, then check with `:type` in GHCi.

```haskell
True
'x'
"haskell"
[1,2,3]
[[1,2],[3,4]]
(True, 'a')
head [10,20,30]
tail "hello"
zip [1,2,3] "abc"
map (+1) [1,2,3]
```

## 2. Simple Function Definitions

Write these functions.

```haskell
double    -- doubles a number
quadruple -- doubles twice
square    -- squares a number
average   -- average of a list of Ints using div
```

Example behaviour:

```haskell
double 4 == 8
quadruple 3 == 12
square 5 == 25
average [2,4,6,8] == 5
```

## 3. Pattern Matching

Define these using pattern matching.

```haskell
first      -- returns first item of a pair
second     -- returns second item of a pair
swap       -- swaps a pair
isEmpty    -- returns True for [], False otherwise
safeHead   -- returns Nothing for [], Just x otherwise
```

Example:

```haskell
swap ("age", 19) == (19, "age")
safeHead [1,2,3] == Just 1
safeHead [] == Nothing
```

## 4. Guards and Conditionals

Write each function once using guards.

```haskell
abs'       -- absolute value
signum'    -- -1, 0, or 1
grade      -- maps a mark to "Fail", "Pass", "Good", "Excellent"
max3       -- maximum of three values
```

Suggested grade boundaries:

```haskell
< 40   -> "Fail"
< 60   -> "Pass"
< 70   -> "Good"
>= 70  -> "Excellent"
```

## 5. List Comprehensions

Use list comprehensions, not explicit recursion.

```haskell
squares n
evens n
factors n
prime n
primes n
pairs xs
positions x xs
count x xs
```

Expected behaviour:

```haskell
squares 5 == [1,4,9,16,25]
evens 10 == [2,4,6,8,10]
factors 12 == [1,2,3,4,6,12]
prime 7 == True
prime 9 == False
primes 20 == [2,3,5,7,11,13,17,19]
pairs [1,2,3,4] == [(1,2),(2,3),(3,4)]
positions 0 [1,0,0,1,0] == [1,2,4]
count 's' "Mississippi" == 4
```

## 6. Recursion on Numbers

Define these recursively.

```haskell
fac       -- factorial
sumdown   -- sum n + (n-1) + ... + 0
power     -- power x n
euclid    -- greatest common divisor by repeated subtraction
```

Examples:

```haskell
fac 5 == 120
sumdown 4 == 10
power 2 5 == 32
euclid 24 18 == 6
```

## 7. Recursion on Lists

Define these recursively. Do not use the Prelude version of the same function.

```haskell
length'
sum'
product'
and'
concat'
replicate'
(!!!)       -- list indexing
elem'
take'
drop'
reverse'
```

Examples:

```haskell
length' [1,2,3] == 3
and' [True, True, False] == False
concat' [[1,2],[3],[4,5]] == [1,2,3,4,5]
replicate' 3 'a' == "aaa"
[10,20,30] !!! 1 == 20
elem' 3 [1,2,3,4] == True
take' 3 [1,2,3,4,5] == [1,2,3]
drop' 2 [1,2,3,4,5] == [3,4,5]
reverse' [1,2,3] == [3,2,1]
```

## 8. Higher-Order Functions

Use `map`, `filter`, `foldr`, and composition where appropriate.

```haskell
addOneAll
squareAll
onlyEven
sumSquaresEven
allPositive
anyZero
takeUntilSpace
dropLeadingSpaces
```

Examples:

```haskell
addOneAll [1,2,3] == [2,3,4]
squareAll [1,2,3] == [1,4,9]
onlyEven [1..10] == [2,4,6,8,10]
sumSquaresEven [1..5] == 20
allPositive [1,2,3] == True
anyZero [1,2,0,3] == True
takeUntilSpace "abc def" == "abc"
dropLeadingSpaces "   hello" == "hello"
```

## 9. Data Types

Define a `Shape` type with circles and rectangles. Then write `area`.

```haskell
data Shape = Circle Float | Rect Float Float
```

Then define an expression type:

```haskell
data Expr = Val Int | Add Expr Expr | Mul Expr Expr
```

Write:

```haskell
eval
size
```

Example expression:

```haskell
Add (Val 1) (Mul (Val 2) (Val 3))
```

It should evaluate to `7`.

## 10. Mini Exam-Style Questions

1. Define a function `sorted :: Ord a => [a] -> Bool` that checks whether a list is sorted.

2. Define `merge :: Ord a => [a] -> [a] -> [a]` that merges two sorted lists.

3. Define `msort :: Ord a => [a] -> [a]` that implements merge sort.

4. Define `pyths :: Int -> [(Int,Int,Int)]` that returns all Pythagorean triples with components in `[1..n]`.

5. Define `perfects :: Int -> [Int]` that returns all perfect numbers up to `n`.

6. Define `scalarProduct :: [Int] -> [Int] -> Int`.

Example:

```haskell
pyths 5 == [(3,4,5),(4,3,5)]
perfects 500 == [6,28,496]
scalarProduct [1,2,3] [4,5,6] == 32
```

## 11. Stretch: Lazy Lists

Define infinite lists and consume only part of them.

```haskell
ones
nats
evensFromZero
fibs
```

Examples:

```haskell
take 5 ones == [1,1,1,1,1]
take 5 nats == [0,1,2,3,4]
take 5 evensFromZero == [0,2,4,6,8]
take 10 fibs == [0,1,1,2,3,5,8,13,21,34]
```

## 12. Suggested Practice Loop

1. Try the function without looking at notes.
2. Write the type signature first.
3. Test in GHCi.
4. If it fails, read the error message and fix one thing at a time.
5. After it works, rewrite it in a different style if possible.

Good rewrites to practise:

- conditional to guards;
- guards to pattern matching;
- recursion to list comprehension;
- recursion to `foldr`;
- multi-step function to composition.

