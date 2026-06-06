# script3.hs

## Finding the second item in a list

These three functions all return the second element of a list. In Haskell definitions, the values being introduced go on the left-hand side of the equation, and the returned value goes on the right-hand side.

`second1` and `second2` take the whole list first, then find the second value inside the function body. `second3` uses pattern matching to bind the second value directly on the left-hand side.

```haskell
second1 :: [a] -> a
second2 :: [a] -> a
second3 :: [a] -> a

second1 x = head (tail x)
second2 x = x !! 1
second3 (_:x:_) = x
```

`second1` uses the head of the list returned by `tail x`. `second2` uses list indexing with `!!`. `second3` uses pattern matching.

## Defining operators

If a function name is made only from symbols, Haskell treats it as an operator by default, so it is used infix. For example, `(.&.) :: Bool -> Bool -> Bool` would be treated as an operator.

If a function name contains letters or numbers, Haskell treats it as a normal prefix function by default. For example, `et :: Bool -> Bool -> Bool` would normally be called as `et True True`. To use it infix, write it in backticks: ``True `et` True``.

## Exclusive or

These are three ways to define exclusive or. `xor1` uses pattern matching, `xor2` uses guarded equations, and `xor3` uses the built-in `/=` operator.

```haskell
xor1 :: Bool -> Bool -> Bool
xor2 :: Bool -> Bool -> Bool
xor3 :: Bool -> Bool -> Bool

xor1 False True = True
xor1 True False = True
xor1 _ _ = False

xor2 x y | x == y    = False
         | otherwise = True

xor3 x y = x /= y
```

## Summing squares

`sumsqr` builds a list of the square numbers from `1` to `n`, then uses `sum` to add them together.

```haskell
sumsqr :: Int -> Int
sumsqr n = sum [x^2 | x <- [1..n]]
```

## Coordinate grids

`grid` produces all coordinate pairs from `0` to `n`, excluding pairs where both values are the same.

```haskell
grid :: Int -> [(Int, Int)]
grid n = [(x,y) | x <- [0..n], y <- [0..n], x /= y]
```

## Euclid's algorithm

`euclid` finds the greatest common divisor by repeatedly subtracting the smaller number from the larger one until both numbers are equal.

```haskell
euclid :: Int -> Int -> Int
euclid x y | x == y    = x
           | x < y     = euclid x (y-x)
           | otherwise = euclid (x-y) x
```

## Fast reverse

This reverse function uses two lists: the original list being depleted, and an accumulator list being filled.

`rev` returns the accumulator when the original list is empty. If the original list is not empty, it binds the head and tail as `x` and `xs`, then recursively moves `x` onto the front of the accumulator.

Example trace:

```haskell
rev [1,2,3] []
rev [2,3] [1]
rev [3] [2,1]
rev [] [3,2,1]
```

```haskell
fastrev :: [a] -> [a]
fastrev xs = rev xs []

rev :: [a] -> [a] -> [a]
rev [] ys = ys
rev (x:xs) ys = rev xs (x:ys)
```
