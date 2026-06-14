# Condensed Haskell Notes

Sources: [Lecture Slides](<Lecture Slides>)

## 1. Functional Programming

Functional programming is based on applying functions to arguments, rather than updating variables step by step. The key shift is from "how to compute this with assignments" to "what expression describes the result".

```haskell
sum [1..10]
```

This replaces an imperative loop with a direct expression. The wrapup summarises the style as saying what to compute rather than how.

```haskell
sum . map (^2) . filter even
```

This means: keep the even values, square them, then sum them.

## 2. GHCi and Basic Syntax

GHCi is the interactive Haskell environment. Use it to evaluate expressions, load scripts, inspect types, and reload changes.

```haskell
2 + 3 * 4
(2 + 3) * 4
```

Function application uses spaces, not brackets, and has higher priority than operators.

```haskell
f a b + c * d
```

This means `(f a b) + (c * d)`.

Useful Prelude functions:

```haskell
head [1,2,3]        -- 1
tail [1,2,3]        -- [2,3]
[1,2,3,4] !! 2      -- 3
drop 2 [1,2,3,4]    -- [3,4]
length [1,2,3]      -- 3
product [1,2,3,4]   -- 24
[1,2] ++ [3,4]      -- [1,2,3,4]
```

Backticks turn a normal function into an infix operator.

```haskell
average ns = sum ns `div` length ns
```

## 3. Types

A type is a collection of related values. Every well-formed expression has a type, and Haskell checks types at compile time.

```haskell
True        :: Bool
'a'         :: Char
"abc"       :: String
[1,2,3]     :: [Int]
(True,'a')  :: (Bool, Char)
```

Lists contain values of one type. Tuples can contain different types, and their size is part of the type.

```haskell
[False, True]        :: [Bool]
[[1,2], [3,4]]       :: [[Int]]
(False, 'x', 3)      :: (Bool, Char, Int)
```

Function types use `->`.

```haskell
not  :: Bool -> Bool
even :: Int -> Bool
```

Most Haskell functions are curried: they take arguments one at a time.

```haskell
add :: Int -> Int -> Int
add x y = x + y

add1 :: Int -> Int
add1 = add 1
```

Polymorphic functions work for many types.

```haskell
length :: [a] -> Int
fst    :: (a,b) -> a
zip    :: [a] -> [b] -> [(a,b)]
```

Overloaded functions use type class constraints.

```haskell
(+)  :: Num a => a -> a -> a
(==) :: Eq a => a -> a -> Bool
(<)  :: Ord a => a -> a -> Bool
```

## 4. Defining Functions

Conditional expressions must have both `then` and `else`.

```haskell
abs' :: Int -> Int
abs' n = if n >= 0 then n else -n
```

Guards are usually clearer when there are several cases.

```haskell
signum' :: Int -> Int
signum' n
  | n < 0     = -1
  | n == 0    = 0
  | otherwise = 1
```

Pattern matching defines results by the shape of the input.

```haskell
not' :: Bool -> Bool
not' False = True
not' True  = False
```

The wildcard `_` means "match anything, but do not name it".

```haskell
(&&&) :: Bool -> Bool -> Bool
True  &&& b = b
False &&& _ = False
```

List patterns use `:` to split a non-empty list into its head and tail.

```haskell
head' :: [a] -> a
head' (x:_) = x

tail' :: [a] -> [a]
tail' (_:xs) = xs
```

Lambda expressions make unnamed functions.

```haskell
odds n = map (\x -> x * 2 + 1) [0..n-1]
```

Operator sections make small functions from operators.

```haskell
(+1)    -- successor
(*2)    -- double
(1/)    -- reciprocal
```

## 5. List Comprehensions

List comprehensions build lists from generators and guards.

```haskell
[x^2 | x <- [1..5]]
-- [1,4,9,16,25]
```

Multiple generators behave like nested loops. Later generators change more quickly.

```haskell
[(x,y) | x <- [1,2,3], y <- [4,5]]
```

Later generators can depend on earlier ones.

```haskell
[(x,y) | x <- [1..3], y <- [x..3]]
-- [(1,1),(1,2),(1,3),(2,2),(2,3),(3,3)]
```

Guards restrict generated values.

```haskell
factors :: Int -> [Int]
factors n = [x | x <- [1..n], n `mod` x == 0]

prime :: Int -> Bool
prime n = factors n == [1,n]

primes :: Int -> [Int]
primes n = [x | x <- [2..n], prime x]
```

`zip` is useful for adjacent pairs and positions.

```haskell
pairs :: [a] -> [(a,a)]
pairs xs = zip xs (tail xs)

sorted :: Ord a => [a] -> Bool
sorted xs = and [x <= y | (x,y) <- pairs xs]

positions :: Eq a => a -> [a] -> [Int]
positions x xs = [i | (y,i) <- zip xs [0..], x == y]
```

Strings are lists of characters, so list functions and comprehensions work on strings too.

```haskell
count :: Char -> String -> Int
count x xs = length [y | y <- xs, x == y]
```

## 6. Recursion

Recursive functions call themselves. Always identify the base case first.

```haskell
fac :: Int -> Int
fac 0 = 1
fac n = n * fac (n-1)
```

For lists, the usual pattern is one case for `[]` and one case for `(x:xs)`.

```haskell
product' :: Num a => [a] -> a
product' []     = 1
product' (n:ns) = n * product' ns

length' :: [a] -> Int
length' []     = 0
length' (_:xs) = 1 + length' xs

reverse' :: [a] -> [a]
reverse' []     = []
reverse' (x:xs) = reverse' xs ++ [x]
```

Recursive functions can have multiple arguments.

```haskell
zip' :: [a] -> [b] -> [(a,b)]
zip' []     _      = []
zip' _      []     = []
zip' (x:xs) (y:ys) = (x,y) : zip' xs ys

drop' :: Int -> [a] -> [a]
drop' 0 xs     = xs
drop' _ []     = []
drop' n (_:xs) = drop' (n-1) xs
```

Quicksort is a classic example where the recursive definition follows the specification closely.

```haskell
qsort :: Ord a => [a] -> [a]
qsort []     = []
qsort (x:xs) =
  qsort smaller ++ [x] ++ qsort larger
  where
    smaller = [a | a <- xs, a <= x]
    larger  = [b | b <- xs, b > x]
```

## 7. Higher-Order Functions

A higher-order function takes a function as an argument or returns a function as a result.

```haskell
twice :: (a -> a) -> a -> a
twice f x = f (f x)
```

`map` applies a function to every element.

```haskell
map (+1) [1,3,5,7]
-- [2,4,6,8]

map' :: (a -> b) -> [a] -> [b]
map' f xs = [f x | x <- xs]
```

`filter` keeps elements that satisfy a predicate.

```haskell
filter even [1..10]
-- [2,4,6,8,10]

filter' :: (a -> Bool) -> [a] -> [a]
filter' p xs = [x | x <- xs, p x]
```

`foldr` captures a common recursion pattern over lists.

```haskell
foldr :: (a -> b -> b) -> b -> [a] -> b
foldr f v []     = v
foldr f v (x:xs) = f x (foldr f v xs)
```

Think of `foldr` as replacing `:` with a function and `[]` with a value.

```haskell
sum'     = foldr (+) 0
product' = foldr (*) 1
and'     = foldr (&&) True
or'      = foldr (||) False
```

Function composition combines functions.

```haskell
odd' :: Int -> Bool
odd' = not . even
```

Other useful higher-order functions:

```haskell
all even [2,4,6]            -- True
any (== ' ') "abc def"      -- True
takeWhile (/= ' ') "abc def" -- "abc"
dropWhile (== ' ') "   abc"  -- "abc"
```

## 8. Type and Data Declarations

`type` introduces a synonym for an existing type. It makes signatures easier to read but does not create a new kind of value.

```haskell
type Pos = (Int, Int)

origin :: Pos
origin = (0,0)

left :: Pos -> Pos
left (x,y) = (x-1,y)
```

Type synonyms can have parameters.

```haskell
type Pair a = (a,a)

copy :: a -> Pair a
copy x = (x,x)
```

`data` creates a new type with constructors.

```haskell
data Answer = Yes | No | Unknown

flipAnswer :: Answer -> Answer
flipAnswer Yes     = No
flipAnswer No      = Yes
flipAnswer Unknown = Unknown
```

Constructors can carry data.

```haskell
data Shape = Circle Float | Rect Float Float

area :: Shape -> Float
area (Circle r) = pi * r^2
area (Rect x y) = x * y
```

Parameterized types describe values that contain another type.

```haskell
data Maybe' a = Nothing' | Just' a

safediv :: Int -> Int -> Maybe Int
safediv _ 0 = Nothing
safediv m n = Just (m `div` n)
```

Recursive data types can represent naturals, trees, or expressions.

```haskell
data Nat = Zero | Succ Nat

nat2int :: Nat -> Int
nat2int Zero     = 0
nat2int (Succ n) = 1 + nat2int n

add :: Nat -> Nat -> Nat
add Zero     n = n
add (Succ m) n = Succ (add m n)
```

Expression trees are processed by recursive pattern matching.

```haskell
data Expr = Val Int | Add Expr Expr | Mul Expr Expr

eval :: Expr -> Int
eval (Val n)   = n
eval (Add x y) = eval x + eval y
eval (Mul x y) = eval x * eval y
```

## 9. The Countdown Problem

The Countdown problem is a search problem: use source numbers at most once, combine them with arithmetic operators, and reach a target. Intermediate results must be positive natural numbers.

Represent operators and expressions as data.

```haskell
data Op = Add | Sub | Mul | Div
data Expr = Val Int | App Op Expr Expr

apply :: Op -> Int -> Int -> Int
apply Add x y = x + y
apply Sub x y = x - y
apply Mul x y = x * y
apply Div x y = x `div` y
```

Use `valid` to reject invalid intermediate results.

```haskell
valid :: Op -> Int -> Int -> Bool
valid Add _ _ = True
valid Sub x y = x > y
valid Mul _ _ = True
valid Div x y = y /= 0 && x `mod` y == 0
```

Evaluate expressions using lists to represent success or failure.

```haskell
eval :: Expr -> [Int]
eval (Val n)     = [n | n > 0]
eval (App o l r) =
  [apply o x y | x <- eval l, y <- eval r, valid o x y]
```

The brute force version generates candidate expressions, evaluates them, then filters to target values. The optimized version fuses generation and evaluation so invalid expressions are rejected earlier.

```haskell
type Result = (Expr, Int)

combine' :: Result -> Result -> [Result]
combine' (l,x) (r,y) =
  [(App o l r, apply o x y) | o <- [Add,Sub,Mul,Div], valid o x y]
```

Further speedups come from using arithmetic properties to avoid duplicate work, such as commutativity of addition and multiplication and identity values like `1`.

## 10. Interactive Programming and IO

Pure Haskell expressions have no side effects. Interactive programs need side effects, so Haskell separates pure values from actions using the `IO` type.

```haskell
getChar :: IO Char
putChar :: Char -> IO ()
return  :: a -> IO a
```

`do` notation sequences actions.

```haskell
act :: IO (Char, Char)
act = do
  x <- getChar
  y <- getChar
  return (x,y)
```

Derived actions can be defined recursively.

```haskell
getLine' :: IO String
getLine' = do
  x <- getChar
  if x == '\n' then
    return []
  else do
    xs <- getLine'
    return (x:xs)

putStr' :: String -> IO ()
putStr' []     = return ()
putStr' (x:xs) = do
  putChar x
  putStr' xs
```

An interactive program is an action whose evaluation performs side effects.

```haskell
strlen :: IO ()
strlen = do
  putStr "Enter a string: "
  xs <- getLine
  putStr "The string has "
  putStr (show (length xs))
  putStrLn " characters"
```

## 11. Lazy Evaluation

Lazy evaluation means expressions are evaluated only when their values are needed. It combines outermost evaluation with sharing of arguments.

```haskell
square :: Int -> Int
square n = n * n
```

In `square (1+2)`, lazy evaluation avoids duplicating work by sharing the result of `1+2` when needed.

Lazy evaluation can terminate when strict evaluation would not.

```haskell
infinity :: Int
infinity = 1 + infinity

fst (0, infinity)
-- 0
```

The second component is not needed, so it is not evaluated.

Infinite lists are possible because only the demanded part is computed.

```haskell
ones :: [Int]
ones = 1 : ones

take 5 ones
-- [1,1,1,1,1]
```

This lets control and data be separated. `ones` describes infinite data; `take 5` controls how much is consumed.

The prime sieve is a compact example.

```haskell
primes :: [Int]
primes = sieve [2..]

sieve :: [Int] -> [Int]
sieve (p:xs) = p : sieve [x | x <- xs, x `mod` p /= 0]

take 10 primes
-- [2,3,5,7,11,13,17,19,23,29]
```

Twin primes can then be described as a transformation of the infinite prime list.

```haskell
twin :: (Int, Int) -> Bool
twin (x,y) = y == x + 2

twins :: [(Int, Int)]
twins = filter twin (zip primes (tail primes))
```

## 12. Exam-Level Takeaways

Haskell revision should focus on:

- Reading and writing type signatures.
- Pattern matching on lists and custom data types.
- Knowing when to use guards, conditionals, lambdas, and sections.
- Using list comprehensions for generation plus filtering.
- Writing recursive functions with clear base cases.
- Recognising `map`, `filter`, `foldr`, composition, `all`, `any`, `takeWhile`, and `dropWhile`.
- Understanding `type` versus `data`.
- Explaining how `IO a` separates pure expressions from side-effecting actions.
- Explaining lazy evaluation, infinite lists, and why only demanded values are computed.

