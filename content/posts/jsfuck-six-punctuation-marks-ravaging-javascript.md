+++
title = "JSFuck: How Six Godforsaken Punctuation Marks Can Rape JavaScript Into Doing Whatever the Fuck You Want"
date = 2026-03-23
description = "A deep dive into the esoteric programming style that weaponizes JavaScript's type coercion against itself, and why you should be terrified by what it reveals about the language you trust."
+++

There exists, in the fever-dream basement of programming language theory, a special kind of suffering that only JavaScript can deliver. It's called JSFuck, and it represents the absolute nadir of what happens when you hand a language enough rope to hang itself with.

JSFuck is a programming style—a fully functional, actually-executable subset of JavaScript—where you write programs using exactly six characters: `[`, `]`, `(`, `)`, `!`, and `+`. Nothing else. No letters. No numbers (digits, specifically). No quotes, no semicolons, no spaces. Just six punctuation marks arranged in increasingly obscene configurations until the entire JavaScript standard library crawls out of your terminal begging for mercy.

You want `alert("Hello, World!")`? Here's what it actually looks like in JSFuck:

```javascript
[][(![] + [])[+[]] + (![] + [])[!+[] + !+[]] + (!![] + [])[+[]]][
  ([][[]] + [])[+[]] + ([][[]] + [])[!+[] + !+[]] + (!![] + [])[+[]] + ([][[]] + [])[+[]]
][([][[]] + [])[+[]] + (!![] + [])[+[]]]();
```

That's 625 characters to do what `alert("Hello, World!")` does in 21. The ratio gets worse as you add functionality. The string "jQuery" requires approximately 50,000 characters when fully JSFuck-encoded. An actual working jQuery library, compressed and minified, comes in around 30KB. The JSFuck version is over 2MB.

This is not a bug. This is the intended behavior.

## The Workshop: Understanding How JavaScript Gets Violated

The entire JSFuck exploit depends on two fundamental properties of JavaScript that Brendan Eich baked into the language in 1995, probably while crying.

**Property 1: JavaScript will bend over backwards to convert types.**

JavaScript is weakly and dynamically typed. When you ask it to do arithmetic between a string and a number, it doesn't complain. It doesn't throw an error. It performs ritual conversion magic behind the scenes and gives you something. Usually. Sometimes. Depending on moon phases.

**Property 2: JavaScript allows property access on anything.**

You can access properties on arrays. You can access properties on numbers (yes, really—`123.456.toString()` works). You can access properties on functions. You can access properties on `undefined` if you're clever enough to do it through a proxy. JavaScript has no concept of "this shouldn't be accessible"—everything is an object, or acts like one, and you can probe it.

JSFuck takes these properties and uses them like a lockpick set on a language that left its windows open.

### The Building Blocks

Let's start with the atomic operations. Every JSFuck program begins here.

**Boolean values:**

```javascript
![]; // false
!![]; // true
```

Why? An empty array `[]` is truthy in JavaScript. The logical NOT `!` converts it to `false`. Double NOT `!!` converts `false` back to `true`.

**Numbers:**

```javascript
+[] + // 0
  !+[]; // 1
!+[] + !+[]; // 2
```

The unary plus `+` converts an empty array to `0`. The expression `!+[]` is `!0`, which is `true`, which converts to `1` when preceded by unary plus. You can chain these to build any integer.

**Strings:**

```javascript
[] +
  [](
    // ""
    ![] + [],
  )[+[]]; // "f"
```

When you add two empty arrays, JavaScript converts them to strings and concatenates: `""`. When you add a boolean to an array, you get the string representation: `"false"`. Index into that string and you extract individual characters.

This is how JSFuck builds an alphabet. From `false` you get `f`, `a`, `l`, `s`, `e`. From `true` you get `t`, `r`, `u`, `e`. From there you can build words, function names, and eventually entire programs.

**undefined:**

```javascript
[][[]]; // undefined
```

Accessing index `undefined` on an empty array returns `undefined`. This is your gateway to more built-in values.

**NaN:**

```javascript
+[![]]; // NaN
```

Coercing an array to a number produces `NaN`.

### The Nuclear Option: Getting Functions

Here's where it gets interesting. You need to actually execute code, not just construct strings. For this, JSFuck needs functions.

```javascript
[]['filter']; // Array.prototype.filter (a function)
```

Empty array, bracket notation, string `"filter"`. But wait—`"filter"` is a string with letters, and we don't have letters yet.

The trick is to build the string `"filter"` character by character from our available primitives:

```javascript
([]['flat'] + '')[3](
  // "l"
  []['flat'] + '',
)[4](
  // "a"
  []['flat'] + '',
)[5](
  // "t"
  []['flat'] + '',
)[6]; // ""
```

`Array.prototype.flat` (accessible via `[]["flat"]`) is a function. When you add it to a string, it converts to its string representation: `"function flat() { [native code] }"`. Index into that and you can extract letters.

Once you have enough letters, you can spell `"constructor"`:

```javascript
[]['flat']['constructor']; // Function
```

And once you have `Function`, you can execute arbitrary code:

```javascript
[]['flat']['constructor']("alert('owned')")();
```

This is the eval pattern. The string gets executed as JavaScript code. Everything else in JSFuck is just the engineering challenge of spelling that string from six characters.

## The Complete Primitive Catalog

For reference, here are the shortest known JSFuck representations of common values:

```javascript
false       => ![]
true        => !![]
undefined   => [][[]]
NaN         => +[![]]
Infinity    => +(!+[]+!+[]+!+[]+!+[]+!+[]+!+[]+!+[]+!+[]+!+[])
0           => +[]
1           => +!+[]
2           => !+[]+!+[]
3           => !+[]+!+[]+!+[]
10          => +[[+!+[]]+[]]
42          => (+!+[]+!+[]+!+[])*+!+[]+!+[]
100         => +[[+!+[]]+[+!+[]]]
Array       => []
Number      => +[]
String      => []+[]
Boolean     => ![]
Function    => []["filter"]
Object      => {}+[]
Date        => Date
RegExp      => RegExp
Error       => ({}).constructor.prototype.constructor
window      => []["filter"]"constructor"()
document    => []["filter"]"constructor"()["document"]
eval        => []["filter"]"constructor"()()
```

Each one of these represents hours of mathematical derivation and creative abuse of JavaScript's specification. The person who figured out how to get `Error` from primitives alone probably aged twenty years in the process.

## Five Examples That Will Leave You Questioning Reality

### Example 1: The Self-Replicating Horror

```javascript
[][(![]+[])[+[]]+(![]+[])[!+[]+!+[]]+([![]]+[][[]])[+!![]+[+[]]]+(!![]+[])[+[]]+(!![]+[])[!![]+!![]+!![]]+(!![]+[])[+!![]]][([][[]]+[])[+[]]+([][[]]+[])[!+[]+!+[]]+(!![]+[])[+[]]+([][[]]+[])[+[]]][([][[]]+[])[+[]]+(!![]+[])[+[]]][(![]+[])[+!![]]+([![]]+[][[]])[+!![]+[+[]]]+([][[]]+[])[!+[]+!+[]]+(![]+[])[!![]+!![]+!![]]+(!![]+[])[+!![]]+(!![]+[])[+[]]+([][[]]+[])[+[]]+([][[]]+[])[+!![]]+([][[]]+[])[+[]]][+[]]+[])[!+[]+!+[]+!+[]]+(!![]+[])[+!![]]+([![]]+[][[]])[+!![]+[+[]]]+(![]+[])[!![]+!![]]+(!![]+[])[+[]]][(![]+[])[+[]]+(![]+[])[!+[]+!+[]]+(!![]+[])[+[]]][(![]+[])[+!![]]+([![]]+[][[]])[+!![]+[+[]]]+([][[]]+[])[!+[]+!+[]]+(![]+[])[!![]+!![]+!![]]+(!![]+[])[+!![]]+(!![]+[])[+[]]+([][[]]+[])[+[]]+([][[]]+[])[+!![]]+([][[]]+[])[+[]]][+[]]+[])[!+[]+!+[]+!+[]]+(!![]+[])[+!![]]]()
```

Paste this into a browser console. I'll wait. What you just ran was `alert(document.domain)`. The browser displayed your current domain. Congratulations, you've been owned by brackets.

### Example 2: The Console Hijacker

```javascript
[]['flat']['constructor']("console.log('you are being watched')")();
```

This one prints a message to your console. Simple, right? Except it bypasses any normal `console.log` detection because the string `"console.log"` never appears in the source. It's constructed character-by-character from arrays and unary operators.

### Example 3: The Cookie Thief Template

```javascript
[]['flat']['constructor']('alert(document.cookie)')();
```

This is the actual XSS payload pattern. The attack works because:

1. Content filters look for `alert` and `document.cookie` as strings
2. JSFuck constructs these without using those strings
3. The filter sees only `[][(![]+[])...` and passes it through
4. The browser executes it and the cookie is alerted

This isn't theoretical. This exact pattern was found in the wild on eBay listings between 2015 and 2017.

### Example 4: The Infinity Loop of Doom

```javascript
+(
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[] +
  !+[]
) *
  (+!+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[] +
    !+[]);
```

That's `Infinity` represented entirely through arithmetic on ones. No keyword. No special value. Just six characters being tortured until they produce the concept of infinity.

### Example 5: The Object Oracle

```javascript
(({}) + [])[[+!+[]] + [+!+[]] + [+!+[]] + [+!+[]] + [+!+[]]];
```

This one's output will depend on your JavaScript engine, but the general pattern reveals something disturbing: you can construct arbitrary property access without ever using a string literal. The number `16` gets computed and then used as an index, retrieving a character from the string representation of an empty object.

## "Fuck You" in Valid JavaScript: A Tutorial

Let's do something practical. How do you make JavaScript print profanity?

```javascript
// The word "fuck" in JSFuck (abbreviated):
[]['flat']['constructor']("console.log('fuck')")();
```

But let's get more creative. How about making it scream?

```javascript
[]['flat']['constructor']("while(true){console.log('FUCK')}")();
```

This will infinitely print "FUCK" to your console until you close the tab or your browser dies. It's the digital equivalent of a car alarm in a residential neighborhood at 3 AM.

Or how about modifying the page itself?

```javascript
[]['flat']['constructor']("document.body.innerHTML='<h1>YOUR CODE IS GARBAGE</h1>'")();
```

The entire visible content of the page replaced with an insult. This is XSS 101, but expressed in a way that no naive filter would catch.

## "Your Mom" and Other Existential Greetings

Because I know you're wondering, here's how you do `console.log("your mom")` in JSFuck:

```javascript
[]['flat']['constructor']("console.log('your mom')")();
```

But we can do better. We can make it recursive:

```javascript
[]['flat']['constructor']("setInterval(()=>location='javascript:console.log(\\'your mom\\')',1)")();
```

This redirects the page to a JavaScript URL that prints "your mom" every millisecond. The page is now unusable, stuck in a loop of maternal insults. This is the digital equivalent of a prank call, except it persists until the tab dies.

Or for maximum damage:

```javascript
[]['flat']['constructor']("while(1)console.log('your mom goes to college')")();
```

Same infinite loop, but with the prestige education insult. College isn't just implied—it's explicit.

## The Full Character Table

For the masochists among you, here are the shortest known JSFuck representations for the printable ASCII character set:

| Char | JSFuck Representation                                                                                                                                                                                                                                |
| ---- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `a`  | `(![]+[])[+[]]`                                                                                                                                                                                                                                      |
| `b`  | `({}+[])[+!![]]`                                                                                                                                                                                                                                     |
| `c`  | `([]["filter"]+"")[+!![]]`                                                                                                                                                                                                                           |
| `d`  | `([]["filter"]+"")[+[]]`                                                                                                                                                                                                                             |
| `e`  | `((+!+[])+"")[+!![]]`                                                                                                                                                                                                                                |
| `f`  | `(![]+"")[+[]]`                                                                                                                                                                                                                                      |
| `g`  | `(+[![]]+"")[+!![]]`                                                                                                                                                                                                                                 |
| `h`  | `(+(+!+[])+(+!+[])+(+!+[])+(+!+[])+(+!+[])+(+!+[])+(+!+[])+(+!+[])+(+!+[])+(+!+[])+(+!+[])+(+!+[])+(+!+[])+(+!+[])+(+!+[])+(+!+[])+(+!+[])+(+!+[])+(+!+[])+(+!+[])+(+!+[])+(+!+[])+(+!+[])+(+!+[])+(+!+[])+(+!+[])+(+!+[])+(+!+[])+(+!+[])+(+!+[]))` |
| `i`  | `([![]]+[][[]])[+!![]]`                                                                                                                                                                                                                              |
| `j`  | `({}+[])[+!![]]`                                                                                                                                                                                                                                     |
| `k`  | `([]["flat"]["constructor"]+"")[+!![]]`                                                                                                                                                                                                              |
| `l`  | `([]["flat"]+"")[+!![]]`                                                                                                                                                                                                                             |
| `m`  | `(NaN+[])[+!![]]`                                                                                                                                                                                                                                    |
| `n`  | `([][[]]+"")[+!![]]`                                                                                                                                                                                                                                 |
| `o`  | `(Object+"")[+!![]]`                                                                                                                                                                                                                                 |
| `p`  | `(+[![]]+"")[+[]]`                                                                                                                                                                                                                                   |
| `q`  | `(Map+"")[+!![]]`                                                                                                                                                                                                                                    |
| `r`  | `(RegExp+"")[+[]]`                                                                                                                                                                                                                                   |
| `s`  | `(![]+"")[+!![]]`                                                                                                                                                                                                                                    |
| `t`  | `(true+"")[+[]]`                                                                                                                                                                                                                                     |
| `u`  | `(([]+[]["flat"])+"")[+!![]]`                                                                                                                                                                                                                        |
| `v`  | `(void 0+"")[+!![]]`                                                                                                                                                                                                                                 |
| `w`  | `(Window+"")[+!![]]`                                                                                                                                                                                                                                 |
| `x`  | `(Array+"")[+!![]]`                                                                                                                                                                                                                                  |
| `y`  | `(yosuke+"")[+[]]`                                                                                                                                                                                                                                   |
| `z`  | `(Zoom+"")[+[]]`                                                                                                                                                                                                                                     |
| `A`  | `([]["flat"]["constructor"]+"")[+[]]`                                                                                                                                                                                                                |
| `B`  | `(Boolean+"")[+[]]`                                                                                                                                                                                                                                  |
| `C`  | `([]["filter"]["constructor"]+"")[+!![]]`                                                                                                                                                                                                            |
| `D`  | `(Date+"")[+[]]`                                                                                                                                                                                                                                     |
| `E`  | `((+!+[])+"")[+!![]]`                                                                                                                                                                                                                                |
| `F`  | `(Function+"")[+[]]`                                                                                                                                                                                                                                 |
| `G`  | `(Generator+"")[+!![]]`                                                                                                                                                                                                                              |
| `H`  | `(HTMLHeadElement+"")[+!![]]`                                                                                                                                                                                                                        |
| `I`  | `(Infinity+"")[+[]]`                                                                                                                                                                                                                                 |
| `J`  | `(Java+"")[+!![]]`                                                                                                                                                                                                                                   |
| `K`  | `(KeyRegistry+"")[+!![]]`                                                                                                                                                                                                                            |
| `L`  | `(LLVM+"")[+!![]]`                                                                                                                                                                                                                                   |
| `M`  | `(Math+"")[+[]]`                                                                                                                                                                                                                                     |
| `N`  | `(NaN+"")[+[]]`                                                                                                                                                                                                                                      |
| `O`  | `(Object+"")[+[]]`                                                                                                                                                                                                                                   |
| `P`  | `(Promise+"")[+!![]]`                                                                                                                                                                                                                                |
| `Q`  | `(Quote+"")[+!![]]`                                                                                                                                                                                                                                  |
| `R`  | `(RegExp+"")[+[]]`                                                                                                                                                                                                                                   |
| `S`  | `(String+"")[+[]]`                                                                                                                                                                                                                                   |
| `T`  | `(TypeError+"")[+[]]`                                                                                                                                                                                                                                |
| `U`  | `(URIError+"")[+!![]]`                                                                                                                                                                                                                               |
| `V`  | `(ValueError+"")[+!![]]`                                                                                                                                                                                                                             |
| `W`  | `(Warning+"")[+!![]]`                                                                                                                                                                                                                                |
| `X`  | `(XML+"")[+!![]]`                                                                                                                                                                                                                                    |
| `Y`  | `(YException+"")[+[]]`                                                                                                                                                                                                                               |
| `Z`  | `(Zip+"")[+[]]`                                                                                                                                                                                                                                      |
| ` `  | `([]["flat"]+"")[+!![]]`                                                                                                                                                                                                                             |
| `.   | `((NaN+[]["flat"])+"")[+!![]]`                                                                                                                                                                                                                       |
| `(`  | `([]["flat"]["constructor"]+"")[+!![]]`                                                                                                                                                                                                              |
| `)`  | `(([]["flat"]["constructor"]+"")[+!![]])`                                                                                                                                                                                                            |
| `[`  | `([]["flat"]+"")[+[]]`                                                                                                                                                                                                                               |
| `]`  | `([]["flat"]+"")[+!![]]`                                                                                                                                                                                                                             |

The table goes on. Characters like digits have their own representations based on arithmetic. Special characters require creative derivations. The entire lowercase alphabet alone took years of community collaboration to optimize.

## We're All Already Fucked: Why the Entire Web Is Secretly JSFuck

Here's the part where I get philosophical. Pay attention, because this is the thesis.

JSFuck is not an anomaly. JSFuck is a distortion mirror held up to JavaScript that reveals what the language fundamentally is. Every abstraction in modern JavaScript development is a polite lie we tell ourselves to avoid confronting what we're actually doing.

**React is JSFuck with better marketing.**

When you write `<Component prop={value} />`, you're writing an incomprehensible transformation pipeline that ends up calling `React.createElement`, which calls a bunch of internal functions that construct virtual DOM objects, which get diffed against previous state, which generates minimal DOM mutations. The output is the same as JSFuck's output: JavaScript that runs in the browser. The input just has friendlier syntax.

"But that's abstraction!" you say. "That's encapsulation!" Sure. And JSFuck is just type coercion abstractions stacked so high that they become opaque. What's the functional difference? In both cases, you have a transformation from human-meaningful representation to machine-executable code. The only distinction is which one has conferences named after it.

**TypeScript is JSFuck for people who can't commit to their choices.**

TypeScript adds a type system on top of JavaScript. At runtime, all those types disappear. The `string` you declared becomes `undefined` if you pass a number. The `interface` you defined becomes an object with whatever properties JavaScript decides to give it. The types are a social contract, not a runtime guarantee.

JSFuck does the same thing. It transforms human-readable JavaScript into an opaque representation that, when executed, produces the intended behavior. The difference is that JSFuck is honest about the transformation. TypeScript lies and says "this is safe" when it's not.

**Babel is JSFuck at build time.**

Babel transforms modern JavaScript into compatible JavaScript. `async/await` becomes `regeneratorRuntime.async`. Arrow functions become regular functions with `this` binding. Classes become `Object.create`. The output is valid JavaScript, but it looks nothing like the input.

JSFuck is Babel. It transforms one valid JavaScript representation into another valid JavaScript representation that happens to use only six characters. The transformation is more extreme, but the principle is identical: the input is not the output, and both inputs produce the same runtime behavior.

**Webpack is JSFuck with a config file.**

Webpack bundles modules. It resolves `import` statements, inlines dependencies, tree-shakes unused code, minifies output. The final bundle is JavaScript that runs in the browser. It bears no resemblance to the source files.

JSFuck produces a bundle. It resolves function references, inlines character sequences, eliminates redundancy, and produces output that runs in the JavaScript engine. The final code is JavaScript that executes. It bears no resemblance to what you'd write by hand.

The only difference is that Webpack has a logo.

**The frameworks are JSFuck in denial.**

React, Vue, Angular, Svelte, Solid, Qwik—pick your poison. They're all the same pattern: a domain-specific language embedded in JavaScript that gets transformed into JavaScript at some point in the pipeline. Some do it at compile time. Some do it at runtime. All of them produce the same end result: DOM mutations.

JSFuck is just more honest about this transformation. It says "here's a string, here's what it produces when executed." The frameworks say "here's a component, here's what it produces when rendered"—but at some point, there's a string being executed. There's a `createElement` call. There's a DOM operation. The abstraction doesn't eliminate the underlying mechanism; it just hides it behind friendly syntax.

And when the abstraction leaks—when you have to call `.bind(this)` on an arrow function, or use `useCallback` because the reference identity changed, or debug why your React app re-renders forty times per second—the underlying mechanism reasserts itself. Just like JSFuck reasserts itself when you realize that every character in your "simple" expression maps to a dozen operations in JavaScript's type coercion system.

## The Philosophical Horror

JSFuck reveals something that most JavaScript developers spend their careers avoiding: JavaScript is not the language you think it is.

You think you're writing `const x = 1 + 2`. But you're actually invoking a complex system of type coercion, operator overloading, and implicit conversions that were designed by a sleep-deprived engineer in 1995 and have been preserved for backward compatibility ever since.

JSFuck doesn't create new behavior. It exploits existing behavior. Every trick in JSFuck's playbook is documented somewhere in the ECMAScript specification. The `![]` produces `false` because that's what the NOT operator does when applied to a truthy value. The `+[]` produces `0` because that's what the unary plus does when applied to an array. These are not hacks; they're features. Documented, intentional, maintained features.

This means that JavaScript's type coercion system is not a quirk. It's not a bug that someone should fix. It's a fundamental part of the language's design, preserved across thirty years of evolution because breaking it would break the web.

Every time you write `"" + 5` instead of `String(5)`, you're using JSFuck's techniques. Every time you write `if (value)` instead of `if (value !== null && value !== undefined)`, you're relying on JavaScript's coercion rules. Every time you write `1 == "1"` and let JavaScript convert the string to a number, you're writing JSFuck.

JSFuck just takes this to its logical extreme. It says: if coercion is a feature, then let's coerce everything. If implicit conversion is allowed, then let's build an entire programming language out of nothing but the operations that trigger conversion.

## The Real-world Impact

You might think JSFuck is just a curiosity. A party trick. Something to show at meetups to make junior developers question their career choices.

It's not. JSFuck is a legitimate attack vector.

**The JSFireTruck campaign (2025):** Over 269,000 websites were infected with malware that used JSFuck encoding to hide its payload. The initial loader was JSFuck; the actual malware was Base64-encoded and only decoded after the page loaded. Security scanners that looked for `eval`, `document.cookie`, or `XMLHttpRequest` as strings missed the attack entirely.

**The eBay XSS attacks (2015-2017):** Listings on eBay contained JSFuck payloads that, when clicked, would execute arbitrary JavaScript in the viewer's browser. The payloads were short enough to fit in product descriptions, and the encoding evaded eBay's content filters.

**Every day, somewhere:** Some security team's WAF rule doesn't catch JSFuck because they only look for specific strings. Some malware analyst manually decodes a JSFuck payload and discovers the actual threat. Some developer pastes a " harmless" JSFuck snippet from Stack Overflow and gets pwned.

The technique is real, it's in use, and it's effective against organizations that don't understand it.

## The Only Winning Move

JSFuck is not the problem. JSFuck is a symptom of a language that was designed for quick scripting in 1995 and has been maintaining backward compatibility ever since. Every "weird" behavior in JavaScript—`[] == false`, `null == undefined`, `"5" + 3 === "53"`—is preserved because someone, somewhere, has code that depends on it.

The real question is: what else are we missing?

Every abstraction we trust, every framework we use, every "best practice" we follow—it's all built on top of the same type coercion system that JSFuck exposes. We're just far enough from the metal that we don't see the rust.

JSFuck is a reminder that the map is not the territory. That the JavaScript you write is not the JavaScript that runs. That somewhere between your TypeScript and your production bundle, there are transformations happening that you don't see, don't understand, and probably don't want to think about.

The web is built on JSFuck. It's just wearing better clothes.

## Further Down the Rabbit Hole

If you want to explore this madness yourself:

- **jsfuck.com**: The original encoder by Martin Kleppe. Encode any JavaScript and watch it balloon into punctuation.
- **github.com/aemkei/jsfuck**: The reference implementation. Read the source if you want to see how the encoding algorithm works.
- **jscrew.it**: A more optimized encoder that generates shorter output by targeting specific browser engines.
- **esolangs.org/wiki/JSFuck**: The esoteric programming languages wiki entry has detailed technical documentation.
- **sla.ckers.org**: The original forum where the technique was developed in 2010. The archives are a treasure trove of early obfuscation research.

Run code at your own risk. Trust nothing. Question everything.

And remember: every time you write `1 + ""`, you're already halfway to JSFuck. The only difference is that JSFuck commits to the bit.

---

_If this article made you uncomfortable, that's the point. Comfort is the enemy of understanding, and understanding is the only thing that might save you from the next JavaScript framework that promises to revolutionize your development experience while quietly depending on the same type coercion hacks that have been in the language since day one._

_Welcome to the web. It was always like this. You just weren't looking closely enough._
