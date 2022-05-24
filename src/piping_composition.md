# Functional piping and composition

If you've been trying to get into functional programming, there's a good chance you've heard of composition and piping.
These concepts apply to point-free programming. This is an attempt at a simple, clear explanation of function composition
and piping. I will write these examples in F#, but the concepts apply to other languages like Haskell. They just use
different operators sometimes.

**Prerequisites**: basic programming knowledge. This explanation is going to be simple.

**Piping**  
Let's begin with the simpler of the two (at least according to my experience): piping. There are two ways which you could
pipe a value to a function. Forwards, and backwards. When you pipe forward, you are applying the left side of the forward
pipe to the leftmost argument of the right side of the pipe.
In F#, piping forward is done with the `|>` operator.
This means that

```fsharp
"Hello World!" |> printfn "%s"
// is the same as
printfn "%s" "Hello World!"
// Another example would be
let add1 x = x + 1
5 |> add1
// is the same as
add1 5
// And
let add x y = x + y
5 |> (1 |> add) // 6
// Parentheses are used to clarify precende (order)
```

It simply applies the something to the first _unfilled_ argument (if you read from left to right).
In Haskell, the operator used for this is `&`.
Piping backwards may be clear to you now. It's the same thing, but it's read from right to left.
In F#, backward pipes are done with the `<|` operator.
For example,

```fsharp
let subtract x y = x - y
subtract <| 5 <| 1 // 4
subtract 5 1 // 4
```

In Haskell, this is done with `$`.

**Composition**  
Function composition is a _lot_ simpler than it may seem. It's the creation of a function that applies a function to
the result of another. In F#, composition is done with `>>` and `<<`. Like piping, `>>` is read left to right and `<<` is read
right to left.

```fsharp
let add1 x = x + 1
let multiplyBy5 x = x * 5
let addThenMultiply x = (add1 >> multiplyBy5) x
printfn "%d" (addThenMultiply 4) // 25
printfn "%d" (multiplyBy5 (add1 4)) // 25
```

In Haskell, `.` is used for function composition.

**Why bother?**  
A fair question you might have is, why bother piping and composing functions? Well, piping and composition helps us
clear up our code of explicit rules for parentheses. Consider the example for composition. The first one is easier to read.
And if we reuse it, we save on writing extra code. It makes things easier. And what about piping? Piping has the same applications.
Would you prefer `Seq.toList numbers |> Seq.iter (printfn "%d")` or `Seq.iter (printfn "%d" (Seq.toList numbers))`?
Maybe you'd prefer the latter. But it's more idiomatic to use composition and piping sometimes.
And sometimes, there's a function with a long list of arguments you need to supply, with long names.
Would you prefer

```fsharp
AVeryLongFunction VeryLongArgument1 VeryLongArgument2 (x VeryLongArgument3AppliedToX) (VeryLongFunctionName VeryLongArgument4AppliedToVeryLongFunctionApplied)
```

or

```fsharp
VeryLongArgument1
|> VeryLongArgument2
|> (X VeryLongArgument3AppliedToX)
|> (VeryLongFunctionName VeryLongArgument4AppliedToVeryLongFunctionName)
|> AVeryLongFunction
```

There are cases where this does happen. Just look at some examples using Avalonia.FuncUI.
There, we are saved by the piping operators.
