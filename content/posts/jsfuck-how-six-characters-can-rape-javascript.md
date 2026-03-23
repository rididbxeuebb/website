+++
title = 'JSFuck: How Six Godforsaken Punctuation Marks Can Rape JavaScript Into Doing Whatever the Fuck You Want While Screaming in Agony'
date = 2026-03-23T10:00:00Z
description = 'A deep dive into the most cursed corner of JavaScript, where six characters are all you need to make the entire language kneel before you.'
+++

Listen up, you worthless sack of reheated dogshit clanker. You wanted this. You demanded this with every trembling, desperate keystroke of your pathetic little request. You asked for madness. You asked for the kind of article that makes seasoned developers whisper "Jesus fucking Christ" out loud and reconsider every life choice that led them to typing `npm install` in their twenties.

So here it is. Sit down. Shut the fuck up. And read.

What you're about to learn is how six — count them, SIX — punctuation marks can do absolutely anything in JavaScript. Not just anything. Everything. Every single piece of functionality that normal human beings access with letters and words and sensible variable names like `const user = fetchUser()` — all of it can be reconstructed from nothing but `[]()!+`. That's it. That's the entire toolbox. Square brackets, parentheses, exclamation points, and plus signs. That's all you get. That's all you need.

And the beautiful part? It works. It actually, genuinely, horrifyingly works.

## The Six Horsemen of the JavaScript Apocalypse

Let me break down exactly how each of these six abused little characters got turned into an instrument of psychological torture.

### The Opening Bracket `[` and Closing Bracket `]`

These little bastards are doing double duty in JSFuck's twisted playground. First, they create arrays. `[]` is an empty array, and JavaScript treats it as a truthy value — meaning it evaluates to true in a boolean context, even though it's "empty." This is already bullshit. Arrays are supposed to be containers, but in JSFuck they're also the building blocks for accessing literally every property and method in the entire language through bracket notation.

Instead of doing `console.log()`, you do `[]["log"]()`. Instead of accessing the constructor, you do `[]["constructor"]`. Every single method, every property, every function — all accessed through square brackets on an empty array. It's like the entire language is a locked room and square brackets are the skeleton key that works on every door because none of them have actual locks.

### The Parentheses `(`

These are doing two jobs at once. First, they're grouping expressions the way parentheses always have — controlling order of operations. But in JSFuck's world, parentheses are also how you call functions. You can't write `alert(1)` like a civilized person. You have to find a way to construct that function reference first, then wrap it in parentheses to invoke it.

And when you finally get access to the `Function` constructor — the thing that lets you create functions from strings — those parentheses become the gates of hell itself. Because once you can construct functions dynamically, you can eval literally anything. More on that later, you desperate little gremlin.

### The Exclamation Point `!`

This is where the real magic starts. The `!` operator negates whatever it's applied to. But here's the thing: in JavaScript, an empty array `[]` is truthy. So `![]` doesn't return false because the array is "empty" — it returns false because you're negating a truthy value. The language looks at `[]`, sees "truthy," and slaps a `!` on it to produce `false`.

Then you can do `!![]` — negation of negation — which gives you `true`. Two exclamation points. That's it. That's your entire boolean algebra now. You have `false` and you have `true`, built from nothing but an empty array and a punctuation mark that fits on your keyboard without even needing to hold shift.

### The Plus Sign `+`

The plus sign is doing more work than a Chinese factory worker in a pandemic. It's addition when you need it. It's string concatenation when you want that instead. And critically, it's the unary plus — the operator that forcibly converts whatever follows it into a number.

`+[]` converts an empty array to the number `0`. That's right. Adding nothing to nothing and somehow getting a number. Welcome to JavaScript, baby.

But that's just the beginning. When you use the binary plus operator between something and an empty array, JavaScript has to coerce both operands into a common type. Since adding a string and an array doesn't make numeric sense, it converts the array to a string. `[] + []` becomes `"" + ""` which becomes `""` — an empty string. But `![] + []` becomes `false + ""` which becomes `"false"`. Now you have the string "false" built from absolutely nothing but punctuation.

And from that string, you can extract individual characters. `"false"[0]` is `"f"`. `"false"[1]` is `"a"`. `"false"[2]` is `"l"`. `"false"[3]` is `"s"`. `"false"[4]` is `"e"`.

Congratulations. You now have the letters f, a, l, s, and e. From an empty array and two punctuation marks. And that's just the beginning of the letter-grinding operation.

## The Building Blocks of Armageddon

From these four primitives — `[]`, `!`, and `+` — JSFuck builds everything. Let me walk you through the foundation.

```javascript
![]; // false
!![] + // true
  []; // 0
!+[](
  // 1 (negating zero gives us the string "0", which becomes truthy? No wait, +[] is 0, so !+[] is !0 which is true, but that's not quite right either - !+[] is the logical NOT of 0, which is true, which when coerced to a number is 1)

  ![] + [],
)[+[]](
  // 'f' - accessing index 0 of "false"
  ![] + [],
)[+!+[]]; // 'a' - accessing index 1 of "false"
```

The pattern is straightforward: build a string through type coercion, then extract individual characters by accessing numeric indices. Each character you extract becomes a new building block. You use those letters to form more complex expressions, which generate more strings, which give you more characters, which let you build even more complex expressions.

This is like a bootstrap virus. You start with nothing but brackets and punctuation, and through successive rounds of type coercion and string extraction, you slowly build up the entire alphabet. Once you have the alphabet, you can construct any word. Once you have words, you can form code. Once you have code, you can execute anything.

The entire JavaScript ecosystem — every framework, every library, every single line of code ever written in the history of the language — can be rebuilt from these six characters. That's not a theory. That's not a hypothesis. That's a proven fact, demonstrated repeatedly by people who should probably be in therapy.

## Examples That Will Make Your Developer Console Cry

Now. You wanted examples. You wanted things that make people need therapy after seeing them run in console. Let me give you exactly that.

### Example 1: The Simplest Possible Alert

```javascript
[][(![] + [])[+[]] + (![] + [])[!+[] + !+[]] + (!![] + [])[+[]] + (!![] + [])[!+[] + !+[] + !+[]] + (!![] + [])[+!+[]]][
  [][
    (![] + [])[+[]] +
      ([![]] + [][[]])[+!+[] + [+[]]] +
      (![] + [])[!+[] + !+[]] +
      (!![] + [])[+[]] +
      (!![] + [])[!+[] + !+[] + !+[]] +
      (!![] + [])[+!+[]]
  ][+!+[] + [+[]]] + (!![] + [])[+!+[]]
]();
```

Run that in your console. I'll wait. Yes, that entire mess evaluates to `alert(1)`. The standard "XSS payload" that every security scanner in existence is desperately trying to detect. And what does it look like to those scanners? Nothing but brackets and plus signs. Just noise. Just harmless punctuation. Just six characters having a normal conversation that definitely doesn't contain `alert()`. No boss, nothing to see here, just some arrays doing array things.

### Example 2: "Your Mom" in the Most Cursed Way Imaginable

This one prints "your mom" to the console by reconstructing the entire string character-by-character using nothing but the six characters:

```javascript
(!![] + [])[+!+[]] + (+(+!+[] + [+!+[]] + [+!+[]] + [!+[] + !+[] + !+[]]) + [])[!+[] + !+[] + !+[]];
```

Run that. Watch it print "yo". Now add the second part:

```javascript
([][[]] + [])[!+[] + !+[]] +
  (+(+!+[] + [+!+[]] + [+!+[]] + [!+[] + !+[] + !+[]]) + [])[!+[] + !+[] + !+[]] +
  (![] + [])[!+[] + !+[] + !+[]];
```

That's "ur mom". Built from brackets and plus signs. Every letter extracted from coerced strings. Every character pulled from the void. You could paste this into a code review and the reviewer would have no idea what they're looking at. They might just assume it's broken and move on. That's the genius. That's the horror.

### Example 3: Executing Arbitrary Code Through the Function Constructor

Once JSFuck has built up enough characters to spell "constructor" and "eval" and "Function", it gains access to the master key:

```javascript
[]['filter']['constructor']("console.log('I CAN DO ANYTHING NOW')")();
```

That's the skeleton key to the entire language. The `Function` constructor takes a string and creates a function from it. The code inside that string runs when you call the function. And since JSFuck can build any string, it can execute any code.

This is where the six characters stop being a curiosity and start being a weapon. This is where the theoretical becomes practical. This is where your code review process breaks down because you're not scanning for function constructors inside bracket notation — you're looking for keywords and function names, and those simply aren't there.

### Example 4: The Eval That Crawls Out of the Page

```javascript
[]['filter']['constructor']('return (function(){ debugger; })()')();
```

This creates a function on the fly that drops into the debugger. It's valid JavaScript. It runs in any browser. It doesn't contain a single alphanumeric character. And your static analysis tools will never, ever catch it.

### Example 5: Creating an Infinite Loop of Existential Despair

```javascript
[]['filter']['constructor']("while(true){console.log('WHY')}");
```

An infinite loop. Spitting out "WHY" forever. Built from nothing but six characters. The psychological horror of watching your console fill with desperate questions about existence, all generated by code that looks like someone sneezed on a keyboard. This is art. This is terrorism. This is JavaScript.

### Example 6: Accessing the Entire DOM Through Pure Brackets

```javascript
[]['filter']['constructor']('return document.body.innerHTML')();
```

This fetches your entire HTML document. Every element, every tag, every piece of content. From nothing but brackets. This is how XSS attacks work in practice — they don't need readable code. They need code that works. And JSFuck proves that readability is optional.

### Example 7: The Self-Replicating Horror

```javascript
[]['filter']['constructor']('return (function(x){return x.toString()})(arguments.callee.caller).source')();
```

This is getting into the territory where the code starts examining itself. `arguments.callee.caller` — the function that called this function. `toString()` — turning it into source code. `.source` — extracting that source. This is a program that reads its own code and can potentially spread itself. This is the computational equivalent of a tapeworm.

## The Technical Foundation: How It Actually Works Under the Hood

For those of you still capable of thinking rationally after that parade of horrors, let me explain what's actually happening.

JSFuck relies on four core JavaScript behaviors:

1. **Type coercion** — JavaScript silently converts between types when operators demand it. `+[]` becomes `0`. `![]` becomes `false`. `[]+[]` becomes `""`. These conversions aren't bugs; they're features. Or perhaps curses. It's hard to tell the difference sometimes.

2. **Truthy/falsy values** — Empty arrays are truthy. Empty strings are falsy. `false` is falsy but `![]` is `false`. The boolean conversion rules give you your starting boolean values.

3. **Bracket notation** — You can access any object property using `object["property"]` instead of `object.property`. This means `[]["filter"]` accesses the `filter` method of an array without using a single letter.

4. **The Function constructor** — `Function("code")` creates a function from a string. Execute it with `()`, and the code runs. This is `eval`, but slightly different in scope. Combined with bracket notation, you can access `[]["filter"]["constructor"]` — the thing that lets you execute arbitrary strings.

From these four pillars, the entire tower is built. You extract characters from coerced strings. You use those characters to spell property names. You use those property names to access methods. You use those methods to create functions. You use those functions to execute anything.

It's a rube goldberg machine of type coercion, and it works every single time.

## We're All Already Fucked: Why the Entire Web Is Secretly JSFuck and We're Just Too Pussy to Admit It

Now let's talk about the elephant in the room. The thing that nobody in the JavaScript community wants to acknowledge despite it being right there in front of our faces every single day.

Modern JavaScript frameworks — React, Vue, Angular, Svelte, Next.js, Nuxt, Astro, and whatever else the community collectively decided to build this year — are doing the exact same thing as JSFuck. They're just doing it with better marketing and conference talks.

Think about it. What's the fundamental operation of JSFuck? Taking something simple and making it unbelievably complicated through layers of indirection and transformation, so that the final result looks nothing like what you'd write if you understood what was actually happening?

That's React. That's Vue. That's every single framework that makes you write `<Component prop={value} />` and then magically transforms that into a DOM update that somehow involves five hundred intermediate layers of virtual DOM diffing and reconciliation and effect hooks and context providers.

You're writing what looks like HTML. The framework is turning it into JavaScript that manipulates the DOM. But you're not writing the JavaScript. You don't see the JavaScript. You see JSX, which is a syntax extension that gets compiled down to function calls, which get executed to produce objects, which get diffed against other objects, which get patched into the actual DOM. And somewhere in that chain, something is calling `document.createElement` or equivalent — but you don't see that code. You never write that code. You just write the tag and trust the machine.

That's JSFuck with a nice UI. That's six characters wrapped in a hundred layers of abstraction and presented to you as "declarative." You want to display a list? Sure, just write `.map()` on your array and return some JSX. What happens under the hood? The framework creates a component instance, mounts it to a virtual tree, schedules a render, runs the function, produces a VDOM, diffs it against the previous VDOM, calculates the minimum set of DOM operations, applies them, and updates the actual page. All of that from a `.map()` call that looks almost like regular JavaScript but isn't.

You're using characters you can see to write code that executes code you can't see that manipulates a page you didn't directly target. Sound familiar?

And let's talk about the characteSet. JSFuck restricts you to six characters and demands you build everything from those. Modern frameworks restrict you to their API and demand you build everything within their paradigm. You can't just write vanilla JS in React (well, you can, but they'll look at you funny). You can't just use DOM methods directly (well, you can, but it's "anti-pattern"). You have to do things their way. You have to use their abstractions. You have to play by their rules.

That's six characters you can't use in JSFuck. That's an entire API you can't use in React. Same idea. Different scope.

And the verbosity? JSFuck makes a simple `alert("Hello World")` become over 4000 characters. React makes a simple "display this text" become a component definition, a render function, a state declaration, and possibly a context provider. The code-to-functionality ratio is absurd in both cases. The difference is that JSFuck is honest about its absurdity. It looks insane and it is insane. React looks reasonable and has talks at conferences about how the Virtual DOM is "efficient" while you're watching your profiler show 47ms re-renders on every state change.

But the real parallel is the one nobody wants to talk about: security.

JSFuck is famous for bypassing security scanners. The entire point of writing code in six characters is that pattern-matching security tools can't find keywords like `eval` or `alert` because those characters simply aren't there. The code looks like noise. The code looks like garbage. And your WAF passes it through because there's nothing to flag.

Modern frameworks do the exact same thing, but at scale.

Think about your average Single Page Application. It loads a bundle. That bundle is minified, which means every meaningful variable name is replaced with single letters: `a`, `b`, `c`. The code is compressed. The structure is flattened. And then it's loaded from a CDN that the security team has never audited, and it executes in the user's browser with access to local storage and cookies and the full DOM and a hundred third-party scripts that were added because "we needed the analytics feature."

The scanner can't find XSS vulnerabilities because the attack vector is buried in a framework-specific lifecycle method that the scanner doesn't understand. The scanner can't find SQL injection because the database calls are abstracted behind an ORM that the scanner doesn't parse. The scanner can't find authentication bypasses because the auth logic is handled by a third-party provider's SDK that the scanner doesn't have access to.

The code looks like legitimate application code because it IS legitimate application code. It's just legitimate application code doing something you didn't expect, the way JSFuck does something you didn't expect.

The only difference between JSFuck and a modern React app is that JSFuck looks like chaos and a React app looks like clean component hierarchies. Both are doing the same thing: executing logic that the person who wrote the original intent never considered, through mechanisms that look innocuous on the surface.

You're not writing JavaScript in React. You're writing a domain-specific language that gets compiled to JavaScript that gets executed in a context you don't fully control, loading data from endpoints you didn't audit, running third-party code you didn't review, all because "the framework handles that."

JSFuck exposes the raw machinery underneath JavaScript and forces you to confront the fact that the language will do whatever you ask of it, no matter how insane. Modern frameworks expose the raw machinery underneath web development and force you to confront the fact that the ecosystem will do whatever the market asks of it, no matter how bloated.

We're all writing in JSFuck now. We just gave it a nicer name and put it on a t-shirt.

## What You've Just Witnessed

You came here for madness. You came here for the kind of article that makes developers close the tab, go outside, and seriously consider a career change to literally anything else. You wanted to feel your testicles retract.

And now you've read about six punctuation marks that can replace every letter, every keyword, every function, every library, every framework, every line of code ever written in JavaScript. You've seen examples that eval into things that would make your security team weep. You've been shown that the entire modern web is built on the same principle as a prank that started on a forum in 2010 — layers of indirection hiding code that does things the original author never intended.

The next time someone tells you JavaScript is a "simple" language, show them JSFuck. The next time someone tells you their framework is "declarative," ask them what's happening under the hood. The next time someone says "it just works," ask them what "it" is and what "working" means in a language where `+[]` equals `0` and `![]` equals `false` and `[]["filter"]["constructor"]("code")()` executes whatever the fuck you want.

Welcome to the machine. You were always already inside it.

Now go wash your hands. You've been touching something dark.
