# script4.hs

## Chomping repeated characters

`chomp` takes a string and returns the first run of repeated characters from the start of that string. If the string starts with several copies of the same character, `takeWhile` keeps taking characters while they match the first one.

```haskell
chomp :: String -> String
chomp []     = []
chomp (x:xs) = takeWhile (== x) (x:xs)
```

## Limiting a run

`munch` applies `chomp`, then keeps at most the first nine characters from that run. This is the same idea as taking `9` characters from `chomp input`.

```haskell
munch :: String -> String
munch = take 9 . chomp
```

## Splitting a string into runs

`runs` repeatedly takes the next run from the front of the string, then drops that run and continues with the remaining characters.

```haskell
runs :: String -> [String]
runs "" = []
runs xs = ys : runs zs
    where
        ys = munch xs
        zs = drop (length ys) xs
```

## Encoding runs

`encode` turns each run into a pair containing the repeated character and the length of that run.

```haskell
encode :: String -> [(Char,Int)]
encode a = [(x, length (x:xs)) | (x:xs) <- runs a]
```

## Flattening compressed data

`flatten` converts each `(character, count)` pair into a compact string form, then joins all the pieces together.

```haskell
flatten :: [(Char,Int)] -> String
flatten = concatMap (\(c,n) -> c : show n)
```

## Compressing and decompressing

`compress` combines `encode` and `flatten`. For decompression, `expand` turns the compact string back into pairs, `decode` expands each pair into repeated characters, and `decompress` combines those steps.

```haskell
compress :: String -> String
compress = flatten . encode

decode :: [(Char,Int)] -> String
decode = concatMap (\(c,n) -> replicate n c)

expand :: String -> [(Char,Int)]
expand "" = []
expand (x:y:zs) = (x, read [y]) : expand zs

decompress :: String -> String
decompress = decode . expand
```
