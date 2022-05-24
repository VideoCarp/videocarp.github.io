# GUI in Rust

The Rust programming language seems like a good fit for GUI programming. C++ developers have access to Qt, wxWidgets and many
more. It's considered that GUI is just not there yet in Rust. I tried using Iced, it seemed like a good option.
But Iced's examples were not working. I didn't bother with other libraries, they were mostly GTK and webview.
I gave it another try.
And at least two options _did_ work!
**egui and Tauri**. You've probably heard of both of them.

## Tauri

You might criticize Tauri for its performance. But you'd be wrong.
Tauri is nowhere near as bloated as Electron and it allows you to use a Rust backend. You can call Rust from the frontend.
One problem might be that Tauri requires you to use web technologies, such as HTML, CSS and JS.
However, you kind of have other options. It's possible to use Fable with F#, ClojureScript or Go with GopherJS.
There're also Pyscript and Brython for Python, which are extremely easy to set up.
The problem here is that you don't get to use Rust for everything. If you're afraid of CSS and not JavaScript, check out SASS.
And some frameworks you can use with to-js compilers might allow you to skip HTML.

## egui

egui is a popular GUI crate for Rust. Contrary to Tauri, you _can_ just use Rust. egui is in "immediate mode" style.
This can be more concise and easier to reason about than you might think. In egui, something like this is possible.

```rust
ui.label(&mut self.labelcontent); // you define this.
if ui.add(Button::new("Click me!")).clicked() {
    self.labelcount = "You have clicked the button!";
}
```

As you can see, you can connect things concisely. This label is bound to `self.labelcontent`. When `self.labelcontent` changes,
it will in the next frame. So it updates in what appears instantly.
I found egui to be quite intuitive and I haven't yet found any problems with it. The only problems with egui that I know of
are that it is not native (but it still looks great) and that updates have breaking changes.

## Other options?

I've only tried Iced, other than these. Unfortunately, examples didn't work. Soon, this may be fixed.
But for now, I suggest you try these out. If you aren't satisfied, perhaps look at [docs.rs](https://docs.rs) and search
for GUI there. Also check out [areweguiyet](https://areweguiyet.com/).
You can also bind libraries from other languages. I strongly suggest giving many libraries a try until one of them works
for you.
