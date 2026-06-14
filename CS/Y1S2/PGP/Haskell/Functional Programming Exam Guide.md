# Functional Programming - Exam Guide

Transcribed from: `C:\Users\Alex\Downloads\Functional Programming - Exam Guide.htm`

## Functional Programming Exam Guide

Please read this guide carefully if you are sitting the Programming Paradigms exam in 2026, as it contains important information and resources to help you with your revision.

Graham Hutton, University of Nottingham

## Assessment Format

The exam this year is an in-person, ExamSys exam that must be completed in a 2-hour period. It is a closed book exam, i.e. no materials can be taken into the exam.

The functional programming component of the exam will be an essay question.

## Examinable Material

The essay question will be based on the lecture slides, lecture videos, and summary of the Haskell standard prelude that was provided, and will involve writing Haskell code.

Electronic copies of all of these materials are also available on Moodle.

Links from the original guide:

- [Lecture slides](http://people.cs.nott.ac.uk/pszgmh/PGP-Haskell.zip)
- [Lecture videos](https://t.co/rk0n19cV3q)
- [Haskell standard prelude](http://people.cs.nott.ac.uk/pszgmh/prelude-new.pdf)

## Study Advice

Work through the lecture slides and lecture videos, and make sure that you are able to understand and reproduce most of the examples, as these or variations on them often come up in the exam in some form. However, you can't learn Haskell just by reading. Trying out examples for yourself in GHC should be a key part of your revision process.

Review your solutions to the exercise sheets and coursework. The three one-page exercise sheets are designed to emphasise the most important aspects of Haskell, while the main coursework is designed to give experience of using several features of Haskell in combination.

The module is based directly on the book *Programming in Haskell*, and the slides follow the same structure and content. Reading the book in combination with the slides would be helpful to your revision. Trying out some of the exercises in the book is also recommended.

The core of the module is the first half of the course, up to the lecture on recursion, which is covered in chapters 1-6 of the book. Make sure that you know this material well, and are able to write simple functions using list comprehensions and recursion, as these are the fundamental skills for the module.

A sound knowledge of this material should be sufficient to obtain a pass mark in the functional programming component of the exam, but to obtain a good mark you will need to be familiar with all of the examinable material.

Moreover, a number of other modules and programming languages build upon the foundations laid in this module, so it is important to understand all the concepts rather than just aiming to pass the exam.

## Past Paper

Exam paper for the last academic year:

- [Haskell question for 2024/25](http://people.cs.nott.ac.uk/pszgmh/pgp-exam-25.txt)
- [Haskell model answer](http://people.cs.nott.ac.uk/pszgmh/pgp-answers-25.txt)

## Guidance: What Might Come Up This Year

This is not a prediction of the exact paper. It is the highest-probability revision focus based on the guide's wording and the Haskell lecture slides.

### Highest Priority

The guide explicitly says chapters 1-6 are the core. Expect to be able to write small Haskell functions from scratch using:

- type signatures;
- basic Prelude functions;
- conditionals and guards;
- pattern matching;
- list patterns such as `[]` and `(x:xs)`;
- list comprehensions;
- recursion.

The most likely code-writing tasks are variations on slide and exercise examples.

```haskell
factors :: Int -> [Int]
factors n = [x | x <- [1..n], n `mod` x == 0]

prime :: Int -> Bool
prime n = factors n == [1,n]
```

```haskell
length' :: [a] -> Int
length' []     = 0
length' (_:xs) = 1 + length' xs
```

### Very Likely

Be ready to explain and use list comprehensions. They are specifically named in the guide and appear heavily in the slides.

```haskell
pairs :: [a] -> [(a,a)]
pairs xs = zip xs (tail xs)

sorted :: Ord a => [a] -> Bool
sorted xs = and [x <= y | (x,y) <- pairs xs]
```

Also revise recursive list functions. The exam can easily ask for a Prelude-style function without using the Prelude version.

```haskell
concat' :: [[a]] -> [a]
concat' []       = []
concat' (xs:xss) = xs ++ concat' xss
```

### Likely for Better Marks

For higher marks, revise all examinable material beyond chapters 1-6:

- higher-order functions: `map`, `filter`, `foldr`, `(.)`, `all`, `any`, `takeWhile`, `dropWhile`;
- `type` declarations versus `data` declarations;
- recursive data types;
- `Maybe`-style safe functions;
- `IO` and `do` notation;
- lazy evaluation and infinite lists;
- the Countdown problem as an integrated example.

```haskell
sumSquaresEven :: [Int] -> Int
sumSquaresEven = sum . map (^2) . filter even
```

```haskell
data Expr = Val Int | Add Expr Expr | Mul Expr Expr

eval :: Expr -> Int
eval (Val n)   = n
eval (Add x y) = eval x + eval y
eval (Mul x y) = eval x * eval y
```

### Essay Question Strategy

Because the functional programming component is described as an essay question involving Haskell code, prepare to do more than just output code. A strong answer should:

- give the type first;
- define the function clearly;
- explain the base case and recursive case;
- mention why guards, pattern matching, or comprehensions are appropriate;
- use examples to show the function works;
- avoid relying on library functions if the question asks you to define them.

For example, if asked to define a recursive function, structure the answer like this:

```haskell
elem' :: Eq a => a -> [a] -> Bool
elem' _ [] = False
elem' x (y:ys)
  | x == y    = True
  | otherwise = elem' x ys
```

Explanation: the empty list contains no elements, so the base case is `False`. For a non-empty list, compare the target with the head. If it matches, return `True`; otherwise continue recursively on the tail.

### Quick Revision Order

1. Chapters 1-3: syntax, Prelude, types, polymorphism, type classes.
2. Chapter 4: conditionals, guards, pattern matching, list patterns, lambdas, sections.
3. Chapter 5: list comprehensions, guards, `zip`, strings as lists.
4. Chapter 6: recursion over numbers and lists.
5. Chapter 7: `map`, `filter`, `foldr`, composition.
6. Chapter 8: `type`, `data`, recursive types.
7. Chapters 9-10 and 15: Countdown, IO, lazy evaluation.

