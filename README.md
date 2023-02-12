# Learning Haskell

The purpose of this repo is to keep track of progress learning haskell and provide a resource for others.

## Resources

- [haskell downloads](https://www.haskell.org/downloads/)

1. [Learn You a Haskell for Great Good!](http://learnyouahaskell.com/introduction#about-this-tutorial)
2. [Haskell in 100 seconds (Video)](https://www.youtube.com/watch?v=Qa8IfEeBJqk)
3. [Functional programming & Haskell (Video)](https://www.youtube.com/watch?v=LnX3B9oaKzw)
4. [Why isn't functional Programming the Norm? (Video)](https://www.youtube.com/watch?v=QyJZzq0v7Z4)
5. [Haskell Wikipedia](https://en.wikipedia.org/wiki/Haskell)
6. [Haskell for Imperative Programmers (Video Playlist)](https://www.youtube.com/watch?v=Vgu82wiiZ90&list=PLe7Ei6viL6jGp1Rfu0dil1JH1SHk9bgDV)

## Chapter 1: Introduction

### What is Haskell?

- purely functional, statically typed, and lazy programming language
- released in 1990 and has since become one of the most widely used functional programming languages
- functional nature means that it supports the use of mathematical functions
- has a strong emphasis on immutability, referential transparency, and compositionality.
- pioneered ideas such as Typeclasses

### Key features of Haskell

- Immutable data
- Referential Transparency
- Lazy: `doubleMe(doubleMe(doubleMe(xs)))`
  - contrived example: assume that func1, func2, func3 are functions that take 1 year to evaluate
  - lazy version will take 2 years, strict version will take 3 years

```haskell
func arg = 
 let z = func1 arg
  y = func2 arg
  z = func3 arg
 in
 if z then x else y
```  

```java
public int func(int arg) {
 int x = func1(arg);
 int y = func2(arg);
 int z = func3(arg);

 if (z) {
  return x;
 } else {
  return y;
 }
}
```

- Declarative

### Applications and use cases of Haskell

- designed to handle a wide range of computing tasks, from simple scripts to large-scale software development

#### What is functional programming?

- No side effects
- Declarative

```haskell

sum [] = 0
sum (x:xs) = x + sum xs

or

sum = foldr (+) 0
```

(vs imperative)

```java
public int sum(int[] input) {
 int sum = 0;
 for (int i = 0; i < input.length; i++) {
  sum += input[i]
 }
 return sum;
}
```

#### Benefits of functional programming

Performance: two functions will not interfer and so can be easily run in parallel

Security: functional programming often gives you better tools to write more "hack proof" code

- more easily verifiable: informally, formally, referential transparency
- static type checking
-

#### Differences between functionla programming and other programming paradigms

## Chapter 2: Getting Started with Haskell

- GHC (Glasgow Haskell Compiler), the most widely used Haskell compiler
- `ghci` - interactive mode
- `:l myfunctions`
- `:r` - reload the script (or run `:l myfunctions` again)

### Setting up Haskell Development environment

`curl --proto '=https' --tlsv1.2 -sSf https://get-ghcup.haskell.org | sh`
windows:

```
Set-ExecutionPolicy Bypass -Scope Process -Force;[System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; try { Invoke-Command -ScriptBlock ([ScriptBlock]::Create((Invoke-WebRequest https://www.haskell.org/ghcup/sh/bootstrap-haskell.ps1 -UseBasicParsing))) -ArgumentList $true } catch { Write-Error $_ }
```

### Basic syntax and structure

### Writing your first Haskell program

## Chapter 3: Data Types and Types in Haskell

### Primitive data types (Integers, Floating-point numbers, Characters, Strings)

### User-defined data types (Tuples, Lists, Arrays)

### Type inference and type signatures

## Chapter 4: Functions and Higher-Order functions in Haskell

### Defining and calling functions

### Anonymous functions (Lambda expressions)

### Higher-order fuctions (Passing functions as arguments, returns functions as values)

## Chapter 5: Lazy Evaluation in Haskell

### What is lazy evaluation?

### Benefits of lazy evaluation

### Implementing lazy evaoluation

## Chapter 6: Modules and Libraries in Haskell

### What are modules and libraries in Haskell?

### Importing modules and libraries

### Writing and using custom modules and libraries

## Chapter 7: Advanced Topics in Haskell

### Monads and IO

### Concurrency and parallelism in Haskell

### Dynamic programming with Haskell

## Chapter 8: Conclusion

### Applications and use cases of Haskell

### Future outlook for Haskell
