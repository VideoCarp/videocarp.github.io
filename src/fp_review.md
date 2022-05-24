# Reviewing functional programming

Here, I'll cover review functional programming according to my experience when I tried it. I'll cover what advantages there are
and what disadvantages there are. My struggles, and what I found easier, and finally a conclusion. This is not a scientific
paper, and is based solely on developer experience, it's more useful if you're trying to understand developer experience.
Hopefully, this will help you decide whether or not to try functional programming.  
So, I originally started programming in general procedurally, with Python. It's important to note that functional programming
and object oriented programming are not the only two paradigms -- contrary to popular belief.
Procedural programming is largely very different to functional programming, so do keep that in mind.

When I started functional programming, I started with F#. I was careful to avoid imperative structures like control flow. And when I began, it was
obviously quite difficult, but I felt the same way as when I started programming in general. It changed my thinking.
And it will most likely change yours. If the well of programming seems dry to you, functional programming can be like rain.

Initially, functional programming was significantly harder to me than imperative programming, because I honestly didn't
understand functional programming and my mind hadn't yet adapted. I found it difficult to deal with there being no variables
-- there are immutables, but I find using 'variable' misleading when they cannot be varied. And it seemed impossible to iterate
when I shouldn't use loops.

After some practice, I caught the idea of using recursion to repeat and the parameters of a function as control
"variables." Things started becoming a lot clearer, and immutability wasn't so much a burden anymore. It felt different to
writing imperative code... but what's the point?

I decided to write a lexer -- not important for you to understand -- functionally, because I had always used them to learn
new programming languages. This task was always hard for me to do, until I tried doing it functionally.

I explored other functional programming languages like Haskell, and Haskell was a lot easier than most people call it out
to be. And I explored the Lisp language family. I didn't have any practical uses for these, but they were still nice.

It also filled a lot of gaps I had when doing imperative programming. A lot of imperative or multi-paradigm languages,
like Rust, Python or CoffeeScript had functional features I didn't know about, that were quite useful. It helped me
understand `None` and `Some`, `map` and `filter`.

Nonetheless, some tasks _were_ harder in functional programming, like using a hashmap or dictionary to keep track of things.
And I had a concern: the memory cost of recursion. But this was _never_ a limitation. The CPU usage was lower, though
and you might chalk this up to language, but in most benchmarks, functional programming can be slightly slower, but use
significantly less of the CPU.

## Summary

### The good

- Rejuvenating and eye-opening
- Often easier to reason about
- Interesting

### The bad

- Sometimes more complicated
- Recursion RAM usage (which was never necessary to worry about)

## Should you try functional programming?

Yes, you should. Unless you have time constraints, functional programming can be enlightening. And it's not like you _have_
to use it. You can learn the philosophy, at the very least.
I'm not here to claim it's superior or inferior to _use_, I'm here to voice my opinion on whether it's worth a try.
