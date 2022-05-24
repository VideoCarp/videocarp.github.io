# Lexing for beginners

![readtime](https://img.shields.io/badge/reading%20time-9%20min%2C%203%20sec-yellowgreen)

This is a guide that should teach you how to perform basic lexing in a functional programing language.
Everything was written in Elixir, but you should be able to follow it if you are using any functional programming language.
Or even an imperative programming language like Python, C or Java.

## What is lexing?

The first question you should ask yourself is, what is lexing? It's the same as tokenising, scanning or lexical analysis.
That might not help you if you haven't heard of these either. **Put simply, lexing is the process of breaking down a string
into meaningful units, indepdendent of context.** What a lexer will do is make the following happen:

```elixir
# Turn this:
# out("Hello World!")
# into this
[
    {"out", :identifier},
    {"(", :oparen},
    {"Hello World!", :string},
    {")", :cparen}
]
```

To further help you understand what lexing really is, take a look at this diagram.
**Don't worry if you don't understand the terms used.**

![702430A0-1D90-419F-B615-455199B20EAC](https://user-images.githubusercontent.com/66365570/162650135-d2e0abf1-a6fc-4a02-b92b-1a7ee10354e3.png)

If you still don't understand lexing, think of it in this way: you have a sentence in English.
It's "Lexing is not easy, but it's possible."
You can break this sentence down into its words, "lexing", "is", "not", "easy", ", ", "but", "it", "'s", "possible".
And then you can categorise each word. Like adjectives, verbs, etc.

- Lexing can be done on any language, from English to C.
- Lexers don't care about most errors, and they can only handle a few.
- When developing a programming language, lexical analysis is the first step taken.
- Lexing allows graphemes (characters) to be morphed into morphemes (small units of meaning).

## Why lex?

Why would you ever need to break down a string into meaningful units? And why do this process when I can just use
regex with `split` functions?
The answer to that question depends on what you're trying to do, and why. Generally, regex is _much_ slower than by hand lexing,
you have to follow its rules and it's less powerful than doing this by hand. Furthermore, lexing is a great exercise.
In fact, once you understand lexing, you'll understand all language a little more.
Should you lex? I recommend you do if you are writing a language or analysing one. But if you feel like you should lex,
then do it.

## IMPORTANT

I highly recommend you do not directly copy and paste any pieces of code. It will hinder your learning. If you want to change anything,
then do it. Play around with the functions and if you are wondering anything, try it and see.

## How to lex?

### Theory

I'll begin by discussing some theory behind lexing. A lexer is supposed to somehow understand what things are meaningful units
of language, which can seem easy at first, but later seems near impossible. The first thing to discuss is that there is no universal
tokenisation model, as long as it is efficient and generates the desired output, your lexer should be fine.
So, let's try lexing the following:
`number += sqrt(16)`

We want this to become something like

```elixir
[
    {"number", :identifier},
    {"+=", :assignment},
    {"sqrt", :identifier},
    {"(", :oparen},
    {"16", :number},
    {")", :cparen}
]
```

This is a _list_ composed of _tuples_. On the left hand side is the raw unit of meaning, and on the right is its category.
I'll call them the token and tag, respectively. The tag is of the type `atom` , which you don't need to worry about.
A scanner will work perfectly fine, had they been strings instead. In this case, I just preferred using atoms.

### Terminology

- Identifier
  An identifier is things like a variable or a function name. They are referencing something.
- Assignment
  An assignment just means that this is an operator that is used to assign a value. An operator is a symbol placed between
  identifiers or values to do something.
- Oparen
  Oparen is short for "opening parentheses." Parentheses are "(" and ")."
- Cparen
  Cparen is short for "closing parentheses."

## Writing code

The next step is to implement the lexer. Because this is a guide using a functional programming language, Elixir, recursion will
be used rather than looping. But don't worry if you're an imperative developer, I actually found it easier to use recursion
for lexing than loops. I'd recommend lexing with a functional programming language if you are using this guide. You can easily
link it to whatever language your main program will use with files.
Recursion, simply, is when a function calls itself. When a function calls itself, it goes back to the start of the function,
much like a `continue` in a loop.

Elixir requires all functions to be in modules. So that's where we'll begin.

```elixir
defmodule Lexer do
    def lex(current  \\ 0, tokenstream  \\ [], len, input_str) do
        char = String.at(input_str, current)
        unless current >= len do
            cond do
                ...
            end
        else
            tokenstream
        end
    end
end
```

This may not make sense just yet, so I'll explain every line here.
`defmodule Lexer do` : this defines the "Lexer" module. Be absolutely sure you **name your module in uppercase**,
otherwise everything will break.
`def lex(current \\ 0, tokenstream \\ [], len, input_str) do` : this line defines the lex function and its parameters.
The `\\` sets the default arguments for each parameter in Elixir. The `current` variable is the index on the program
the user inputs, which is `input_str` . `len` is the length of `input_str` .
`char = String.at(input_str, current)` : this line defines the `char` variable. This variable is the substring which we are
testing conditions for. `String.at(input_str, current)` is equivalent to `input_str[current]` in other language such as
Python.
`unless current >= len do` : unless `current` is greater than `len` , do the following. This is equivalent to `if !(current >= len)`

or `if not (current >= len)` in other languages. This is crucial because it ensures that recursion only happens when it needs to.
This effectively means if the string has not been exhausted.
`cond do` : this is a block of code that can have conditions attached to it. This is an equivalent of a block of `if` s and `else if` s.
`...` : this means that we'll fill this section later.

```elixir
else
    tokenstream
```

This is not a single line. But this is the `else` block for the `unless` . This means that this code will execute once the string
has been exhausted. And we return `tokenstream` . In Elixir, the last expression's return value is what the function will return.
In other words, it's the same as `return tokenstream` in other languages.
The rest are `end` s. These terminate blocks. They are equivalent to unindenting in Python or `}` in a lot of languages.

### Adding helper functions

In most programming languages, identifiers are defined using the English alphabet, numbers and `_` , numbers are written as the
Hindu-Arabic numerals (0, 1, 2, etc.) and strings are written using quotes. Functions are called with parentheses, and so on.
Elixir allows using `?` in identifiers. And the magic that makes this happen, is of course in part the tokeniser.
To allow you to tweak and debug your lexer easily, as well as be more concise, helper functions are ideal.
So, what is a helper function? In this context, a helper function is a function that takes as input a character and returns a boolean.
It checks for a condition using the character. These are easily the simplest part of the scanner.
I'll start with a few helper functions, and more will be added. Nest these functions in the lexer module.

```elixir
def numeric(char) do
    char >= "0" && char <= "9" # Characters are just organized conveniently. && means "and."
    # This function tells us if "char" is a number. It obviously doesn't cover floating point numbers,
    # but you should be able to add them if you need to.
end

def alphanumeric(char) do
    numeric(char) || (char >= "a" && char <= "z") || (char >= "A" && char <= "Z") || char == "_"
    # This checks if the character is alphabetical, numeric or is equal to "_".
    # This will be used to create identifier tokens.
    # You can add other conditions to add more characters. But be sure to use a "||" (or).
end

def arithmetic(char) do
    Enum.member?(["+", "-", "*", "/", "%"], char)
    # checks if character is used for arithmetic operations.
    # if it is in that list.
end
```

There are explanations on what each of these functions does and how. But these are a foundation for the basic lexical rules
of the language. Be sure to nest these in the `Lexer` module, so that they're local and accessible by the `Lexer.lex` function.

### Simple symbol lexing

So now you have the tools to easily identify where each character belongs. You don't need to use these helper functions yet.
But you may have noticed that symbols like "(" or "=" were not covered with the helper functions. These things are oftentimes
single-character tokens, so it's not worth making a function we'll never use or edit.
How do we add the single-character tokens with their tags into the tokenstream? The answer to this is simple: by checking a condition
and performing recursion. What will be done is that when one of these is encountered, `lex` will be called with new arguments.
Remember the arguments to `lex` ? They were `current` , `tokenstream` , `len` , `input_str` . It may not make sense that our lexer
function wants to take its own output as an argument to an imperative programmer. However, it's a crucial part of using recursion
with immutable variables effectively for lexing. What we'll do is call the `lex` function again when we spot one of these single-
character tokens.

- `current`: receives`current + 1`, which is our cursor plus the amount of characters we went over.
- `tokenstream`: receives `[{char, :TYPE} | tokenstream]`. This is prepending (adding as the first element or head of a list)
  a tuple containing the character and the category. `:TYPE` means the tag. If appending is available, I highly recommend
  it instead. In Elixir, prepending and then reversing is faster than concatenating lists, so that's what's being done here.
- `len`: receives just `len`.
- `input_str`: receives just `input_str`.

Let's put this in real Elixir code. Inside our `cond` block, it should now look something like this:

```elixir
                # single-char tokens
                char == ")" -> # if the condition is true, do this.
                    lex(current + 1, [{char, :cparen} | tokenstream], len, input_str)

                char == "(" -> # if the above was false, do this instead. and so on
                    lex(current + 1, [{char, :oparen} | tokenstream], len, input_str)

                char == "{" ->
                    lex(current + 1, [{char, :obrace} | tokenstream], len, input_str)

                char == "}" ->
                    lex(current + 1, [{char, :cbrace} | tokenstream], len, input_str)

                char == "=" ->
                    lex(current + 1, [{char, :assignment} | tokenstream], len, input_str)

                true -> # if all the conditions failed, do this instead.
                        # this is what should happen if an unknown character is found.
                        # Here, it's being ignored. But you can raise an error, if you wish.
                    lex(current + 1, tokenstream, len, input_str)
```

If you give your lexer a try now, which you can do by printing `Lexer.lex` 's output with `IO.inspect` , it should be able
to scan any of these characters, but ignore everything else.

### Handling multiple-character tokens

Remember the helper functions you defined a bit ago? Here's where they're going to come in useful. The first step to handling multi-
character tokens is to define some functions to do that for you. This is advantegous in that it increases your code's maintability
significantly in comparison to just doing operations. And it's a lot simpler, too.
The main idea behind handling tokens > 1 character is to go over each character, add it to a temporary string variable
until calling the relevant helper function with the character argument doesn't return true, or the string is exhausted.
Then, that temporary variable is passed into the token stream with a tag. This is a lot easier done than said (not a typo)
but that was my best explanation. Let's start with lexing integers.
Define the following function nested into `Lexer` .

```elixir
    def handlenum(cursor, temp, input_strr) do
        # `cursor' is the same as `current', but to make sure they're distinguished, I use `cursor'
        # `temp' is a temporary variable that begins as an empty string.
        character = String.at(input_strr, cursor)
        if numeric(character) do
            handlenum(cursor + 1, temp <> character, input_strr)
            # if the character in this recursion is numeric, then go back up
            # but go to the next character and add to the temporary variable
        else
            {temp, cursor}
            # return a tuple of the token and the new cursor.
        end
    end
```

Closely inspect this, and once you get it, write the rest:

```elixir
def handlestring(cursor, temp, input_strr) do
        character = String.at(input_strr, cursor)
        if character != " "" do
            handlestring(cursor + 1, temp <> character, input_strr)
        else
            {temp, cursor}
        end
    end

    def handlealpha(cursor, temp, input_strr) do
        character = String.at(input_strr, cursor)
        if alphanumeric(character) do
            handlealpha(cursor + 1, temp <> character, input_strr)
        else
            {temp, cursor}
        end
    end
```

What you will notice, is that the process is quite simple. Each one of these is largely the same as the others, just with
different conditions. In fact, these functions could've been generated with just one function.
But for the sake of simplicity and performance, this will be sufficient.
It's important to note, **if you don't yet understand, don't go to the next part yet.**
It's quite normal and as to be expected that you don't fully understand lexing the first time. So, don't worry and keep trying.

### Implementing the handler functions

You should now be able to shove these handler functions that depend on the helper functions into your `cond` block in `Lexer.lex` .
Give that a shot and try running your program. It should work if you filled everything in correctly. You should've added something
like the following in your `cond` block.

```elixir
                char == " "" ->
                    {token, cursor} = handlestring(current + 1, "", input_str)
                    # Increments to manage the quotes. We don't want them.
                    lex(cursor + 1, [{token, :str} | tokenstream], len, input_str)

                numeric(char) ->
                    {token, cursor} = handlenum(current, "", input_str)
                    lex(cursor, [{token, :number} | tokenstream], len, input_str)

                alphanumeric(char) ->
                    {token, cursor} = handlealpha(current, "", input_str)
                    lex(cursor, [{token, :identifier} | tokenstream], len, input_str)
```

Make sure to add this above the `true ->` segment.
If we give `lex` our program, that was intially `number += sqrt(16)` , the output would be:

```elixir
[
    {"number", :identifier},
    {"+", :arithmetic},
    {"sqrt", :identifier},
    {"(", :oparen},
    {"16", :number},
    {")", :cparen},
]
```

This isn't exactly what we want. It ignored `=` and added an arithmetic out of nowhere. `+=` should've been `{"+=", :assignment}` .
Fortunately, the solution is easy. It will be explained in the next section.

### Conditional multi-character tokens

Sometimes, you need to lex something that could be one thing or the other, or both. For example, `+=` should be an `:assignment`

rather than `:arithmetic` , `:assignment` . While `+ =` should be `:arithmetic` , `:assignment` . The solution to this is by something
called "peeking." Peeking is exactly what it sounds like: you look at the next token without actually advancing to the next character.
Knowing that, the idea for scanning `+=` correctly is simple: when you find a `+` , peek for an `=` . If there is, advance twice and
add the token with the tag. Otherwise, add the `+` alone. So, add this to your `cond` block.

```elixir
                arithmetic(char) ->
                    unless String.at(input_str, current + 1) == "=" do
                        lex(current + 1, [{char, :arithmetic} | tokenstream], len, input_str)
                    else
                        lex(current + 2, [{char <> "=", :assignment} | tokenstream], len, input_str)
                    end
```

But about the `=` ? Well, do the same thing if you're going to have an `==` which should be a `:comparison` . Or, do the same thing as
you did in the start with single-character tokens suh as `:oparen` .

### Almost done

After that's been done, you're almost done with a basic lexer that you can build on. All you have to do now is go to the `else` within
`Lexer.lex` 's `unless` and replace `tokenstream` with `Enum.reverse(tokenstream)` . And that's it. But be sure to read the rest.

## Notices

This is an imperfect lexer and has been slightly simplified. Rather than "consuming" the input string, here, we're actually
just indexing it. This is inefficient but it should be sufficient for a lot of cases. Click [here](https://gist.github.com/VideoCarp/36bca88c6ef61f0a0d993d70ef6df760) for the finished lexer.
If this helped you or you'd like to give some feedback, please contribute or post a comment.
