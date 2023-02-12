# Learning Haskell

The purpose of this repo is to keep track of progress learning haskell and provide a resource for others.

My repl.it:
https://replit.com/@OnlyGoBackwards/Haskel-Learning#Main.hs

## Resources

- [haskell downloads](https://www.haskell.org/downloads/)

1. [Learn You a Haskell for Great Good!](http://learnyouahaskell.com/introduction#about-this-tutorial)
2. [Haskell in 100 seconds (Video)](https://www.youtube.com/watch?v=Qa8IfEeBJqk)
3. [Functional programming & Haskell (Video)](https://www.youtube.com/watch?v=LnX3B9oaKzw)
4. [Why isn't functional Programming the Norm? (Video)](https://www.youtube.com/watch?v=QyJZzq0v7Z4)
5. [Haskell Wikipedia](https://en.wikipedia.org/wiki/Haskell)
6. [Haskell for Imperative Programmers (Video Playlist)](https://www.youtube.com/watch?v=Vgu82wiiZ90&list=PLe7Ei6viL6jGp1Rfu0dil1JH1SHk9bgDV)
7. [Haskell Wiki](https://wiki.haskell.org)

## Chapter 1: Introduction

### What is Haskell?

- purely functional, statically typed, and lazy programming language
- released in 1990 and has since become one of the most widely used functional programming languages
- has a strong emphasis on immutability, referential transparency, and compositionality
- pioneered ideas such as Typeclasses
- inspired by mathematical notation/[lambda calculus](https://brilliant.org/wiki/lambda-calculus/)
	- &#955;x.&#955;y.x+y
	- Y combinator - Y = &#955;f.(&#955;x.f(x x)) (&#955;x.f (x x)) - created by `Haskell Curry`, used to define recurssion. 	

### Why Haskell?
- Designed for teaching, research and industrial applications
- type classes, which enable type-safe operator overloading, and monadic IO
- easy to test
- uses in industry from aerospace and defense, to finance, to web startups, hardware design firms and a lawnmower manufacturer
- [Advantages Of Functional Programming](http://wiki.c2.com/?AdvantagesOfFunctionalProgramming)

#### Who uses Haskell?
- Facebook: spam detection
- [Hasura](https://github.com/hasura/graphql-engine): OS graphql engine
- Github: [Semantic](https://github.com/github/semantic) -  a command-line tool for parsing, analyzing, and comparing source code.
- Meta: also one of the biggest sponsors of [The Haskell Foundation](https://haskell.foundation/)
- more.. [wiki.haskell - Hakell in Industry](https://wiki.haskell.org/Haskell_in_industry)

#### Haskell Frameworks?
- [IHP](https://ihp.digitallyinduced.com/) - Integrated Haskell Platform web development framework - [3.8k stars on github](https://github.com/digitallyinduced/ihp)
- [Yesod Web Framework](https://www.yesodweb.com/) - [2.5k stars github](https://github.com/yesodweb/yesod), seems to be popular for fullstack
- [Servant](https://www.servant.dev/) - [1.7k stars on github](https://github.com/haskell-servant/servant) seems to be popular for APIs

### Key features of Haskell
- Functional first
- Immutable data
	- safe multi-threading
	- uses conditional expressions and recursion (no loops)
- Type Inference (`hello = "world" or hello = "world" :: [Char]`)
- Referential Transparency
	-	value output doesn’t depend on a local or global state, only the arguments passed to the function
- Garbage Collector
- 
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

#### Other Examples of Functional Programming Languages
- [Lisp](http://progopedia.com/example/factorial/22/)
```lisp
(defun factorial (n)
  (if (= n 1)
      1
      (* n (factorial (- n 1)))))

(print (factorial 5))
```
- [Scheme](https://vhernando.github.io/factorial-function-scheme)
```scheme
(define (factorial n)
  (if (= n 1)
      1
      (* n (factorial (- n 1)))))

(display (factorial 5))
(newline)
```
- [ML (Meta Language)](https://en.wikipedia.org/wiki/ML_(programming_language))
```ML
fun fac (0 : int) : int = 1
  | fac (n : int) : int = n * fac (n - 1)
```
- [Erlang](https://www.erlang.org/doc/getting_started/seq_prog.html)

```erlang
fac(1) ->
    1;
fac(N) ->
    N * fac(N - 1).
```
- [F#](https://en.wikibooks.org/wiki/F_Sharp_Programming/Recursion#:~:text=Factorial%20in%20F%23Edit,*%202%20*%201%20%3D%20720.)
```f#
open System
 
let rec fact x =
    if x < 1 then 1
    else x * fact (x - 1)

Console.WriteLine(fact 6)		
```

- Scala

```scala
object myObject {

    def factorialRec(n: Int): Int ={
        if(n <= 1)
            return 1
        return n * factorialRec(n-1)
    }
    
    def main(args: Array[String]) {
        val n = 6
        println("The factorial of " + n + " is " + factorialRec(n))
    }
}
```

## Chapter 2: Getting Started with Haskell

- GHC (Glasgow Haskell Compiler), the most widely used Haskell compiler
- `ghci` - interactive mode - exit with `Ctrl+D`
- `:l myfunctions`
- `:r` - reload the script (or run `:l myfunctions` again)
- `cabal init --interactive` 

### Setting up Haskell Development environment

`curl --proto '=https' --tlsv1.2 -sSf https://get-ghcup.haskell.org | sh`
windows:

```
Set-ExecutionPolicy Bypass -Scope Process -Force;[System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; try { Invoke-Command -ScriptBlock ([ScriptBlock]::Create((Invoke-WebRequest https://www.haskell.org/ghcup/sh/bootstrap-haskell.ps1 -UseBasicParsing))) -ArgumentList $true } catch { Write-Error $_ }
```

### Basic syntax and structure

"A little pitfall to watch out for here is negating numbers. If we want to have a negative number, it's always best to surround it with parentheses. Doing 5 * -3 will make GHCI yell at you but doing 5 * (-3) will work just fine." - `learnyouahaskell`

```shell
ghci> 2 + 15  
17  
ghci> 49 * 100  
4900  
ghci> 1892 - 1472  
420  
ghci> 5 / 2  
2.5  
ghci>  
```

```shell
ghci> True && False  
False  
ghci> True && True  
True  
ghci> False || True  
True   
ghci> not False  
True  
ghci> not (True && True)  
False  
```

What about doing `5 + "llama"` or `5 == True`?


"You may not have known it but we've been using functions now all along. For instance, `*` is a function that takes two numbers and multiplies them. As you've seen, we call it by sandwiching it between them. This is what we call an `infix` function. Most functions that aren't used with numbers are `prefix` functions. Let's take a look at them." - `learnyouahaskell`

```shell
ghci> succ 8  
9
```

```shell
ghci> min 9 10  
9  
ghci> min 3.4 3.2  
3.2  
ghci> max 100 101  
101   
```

```shell
ghci> succ 9 + max 5 4 + 1  
16  
ghci> (succ 9) + (max 5 4) + 1  
16 
```

#### If else
- else is mandatory in haskell
```haskell
doubleSmallNumber x = if x > 100  
                        then x  
                        else x*2
```
- if statements are expressions: they return a value
```haskell
doubleSmallNumber' x = (if x > 100 then x else x*2) + 1  
```
- `'` usually denotes a strict version of a function (one that isn't lazy) or a slightly modified version of another function/variable.

#### Functions
- cannot begin with capital letter

#### Lists
- are `homogenous`: stores elements of the same type
```shell
ghci> let lostNumbers = [4,8,15,16,23,42]  
ghci> lostNumbers  
[4,8,15,16,23,42]  
```

```haskell
ghci> [1,2,3,4] ++ [9,10,11,12]  
[1,2,3,4,9,10,11,12]  
ghci> "hello" ++ " " ++ "world"  
"hello world"  
ghci> ['w','o'] ++ ['o','t']  
"woot"  
```
- Using `++` Haskell has to walk through the whole list on the left side of ++.

```haskell
ghci> 'A':" SMALL CAT"  
"A SMALL CAT"  
ghci> 5:[1,2,3,4,5]  
[5,1,2,3,4,5]  
```
- However, putting something at the beginning of a list using the `:` operator (also called the `cons` operator) is instantaneous.
- `[1,2,3]` is actually just syntactic sugar for `1:2:3:[]`

```shell
ghci> "Steve Buscemi" !! 6  
'B'  
ghci> [9.4,33.2,96.2,11.2,23.25] !! 1  
33.2  
```
##### More examples
```haskell
[3,2,1] > [2,1,0]  
[3,2,1] > [2,10,100]  
[3,4,2] > [3,4]  
[3,4,2] > [2,4]  
[3,4,2] == [3,4,2]  

head [5,4,3,2,1]
tail [5,4,3,2,1]
last [5,4,3,2,1]
init [5,4,3,2,1]   
head []  

length [5,4,3,2,1]  

null [1,2,3]  

reverse [5,4,3,2,1]  

take 3 [5,4,3,2,1]  
take 5 [1,2]
take 0 [6,6,6]    

drop 3 [8,4,2,1,5,6]  
drop 0 [1,2,3,4]  
drop 100 [1,2,3,4]

minimum [8,4,2,1,5,6]  

sum [5,2,1,6,3,2,5,7]  
product [6,2,1,2]  
product [1,2,5,6,7,9,2,0]  

4 `elem` [3,4,5,6]  
10 `elem` [3,4,5,6]

replicate 3 10
```

##### Texas ranges
```haskell
[1..20] 
['a'..'z']  
['K'..'Z']  
[2,4..20]  
[3,6..20]  
```
- infinite ranges (lazy)
```haskell
take 24 [13,26..]
```

```haskell
take 10 (cycle [1,2,3])
take 12 (cycle "LOL ")
take 10 (repeat 5)
```

##### List Comprehension
- example of the first ten even natural numbers
![list comprehension](http://s3.amazonaws.com/lyah/setnotation.png)
```haskell
take 10 [2,4..]
```

```haskell
[x*2 | x <- [1..10]]
```
more examples with predicates
```haskell
[x*2 | x <- [1..10], x*2 >= 12]

[ x | x <- [50..100], x `mod` 7 == 3]  

boomBangs xs = [ if x < 10 then "BOOM!" else "BANG!" | x <- xs, odd x]  

[ x | x <- [10..20], x /= 13, x /= 15, x /= 19] 

[ x*y | x <- [2,5,10], y <- [8,10,11]]  

[ x*y | x <- [2,5,10], y <- [8,10,11], x*y > 50]

[adjective ++ " " ++ noun | 
adjective <- ["lazy", "grouchy", "happy"], 
noun <- ["frog", "dog", "cat"]]  

sum [1 | _ <- xs]

[ c | c <- st, c `elem` ['A'..'Z']]   

[ [ x | x <- xs, even x ] | xs <- xxs]  
```





### Writing your first Haskell program

```haskell
main = do
  putStrLn "Hello"
  putStrLn "World"
```


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
