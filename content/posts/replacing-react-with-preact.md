+++
title = 'Replacing React with Preact'
date = 2026-03-17T12:00:00Z
description = 'A practical case for swapping React for Preact when you want less framework weight without abandoning JSX.'
+++

React made component-based UI normal, but many teams keep paying React's full cost long after their interface stops needing that much machinery. I have become increasingly suspicious of front-end stacks that need a long explanation before they can justify rendering a settings screen and a few forms.

I have ended up on more than one small internal tool where React was not exactly the problem, but it was clearly more framework than the job required. After the initial swap to Preact, the code did not suddenly become beautiful, but it did become easier to justify. The bundle was smaller, the runtime story was simpler, and the application still behaved like the same application.

If an application mostly renders forms, lists, dashboards, and ordinary client-side interactions, Preact is often the simpler choice. It keeps the same general component model, supports hooks, and offers `preact/compat` as a compatibility layer for code and libraries that expect React. In other words, it usually lets you keep the habits people actually like while dropping some of the weight they have merely learned to tolerate.

The current Preact guidance remains fairly plain: either build directly with Preact, or alias `react`, `react-dom`, and `react/jsx-runtime` to Preact so an existing React-oriented codebase can run with fewer changes. For many projects, that is enough to cut bundle weight and reduce runtime overhead without rewriting the whole interface. I appreciate that the official advice is mostly configuration and caveats instead of grand promises.

The important phrase there is compatibility layer, not magic. Replacing React with Preact is usually easy when your code stays close to the common API surface. It becomes less easy when the application depends on React-specific edge behavior, framework assumptions, or libraries that lean heavily on the newest React internals.

That has been my practical rule for it: if a codebase mostly consists of components, hooks, and unremarkable UI work, I expect the migration to be boring. If it depends on framework fashion, experimental rendering behavior, or a stack of libraries that assume React is the center of the universe, I expect friction.

JSX is part of why the migration can be smaller than people expect. JSX is not HTML and it is not a template language. It is syntax that a compiler transforms into JavaScript function calls.

```tsx
<button className="save">Save</button>
```

After compilation, that turns into ordinary JavaScript describing a node tree.

```tsx
jsx("button", { className: "save", children: "Save" })
```

In older setups the generated call may look more like `h("button", { className: "save" }, "Save")` or `createElement(...)`, but the idea is the same. The browser never executes raw JSX. A tool transforms it first, then React or Preact consumes the resulting function calls to build virtual nodes.

That matters because most React code is really just JavaScript functions plus JSX. If the runtime behind those generated calls is compatible enough, much of the application can move without a dramatic rewrite. Once that clicks, the framework branding starts to look less sacred than it is usually treated.

In practical terms, the migration usually looks like this:

- keep the existing components
- alias `react` to `preact/compat`
- alias `react-dom` to `preact/compat`
- alias `react/jsx-runtime` to `preact/jsx-runtime`
- update test and TypeScript configuration so module resolution matches the runtime

For Vite projects, Preact support is well-trodden and the path is particularly direct. In older bundler stacks, the work is still mostly configuration: aliases for the application build, aliases for tests, and TypeScript path mapping when needed. That is the kind of migration I like most: not heroic, not ideological, just a series of boring edits that leave the project lighter than it was before.

There are, however, differences worth knowing.

Preact core does not implement React's synthetic event system. It uses the browser's native event model. If you are using Preact without `preact/compat`, some event expectations change. The common example is form handling: in Preact core, `onInput` is the normal event for reacting to text entry, while React commonly teaches `onChange` for that purpose. With `preact/compat`, many of these differences are normalized.

There are a few other distinctions. Preact's `StrictMode` exists for compatibility, but it does not perform React's extra development checks. Preact also follows the DOM more closely in some places, including support for raw attribute names, standard browser events, and custom elements. Those differences are usually manageable, but they should be treated as real engineering constraints, not marketing copy.

So when should React be replaced with Preact?

Use Preact when the goal is a smaller client bundle, a simpler runtime, and continued access to the React-style component model. It is especially sensible for content-heavy products, internal tools, modest interactive applications, and teams that want JSX without accepting a larger framework than the work requires. That covers more projects than the industry likes to admit.

Keep React when the stack depends on React-specific framework behavior, or when a critical library relies on compatibility edges that are not boringly stable in Preact.

That is the standard that matters. If a project can keep components, keep JSX, keep most of its habits, and still ship less code, that is usually an improvement. I do not think every React project should be converted on principle, but I do think too many teams never even ask whether React is still earning its place. Quite often, it is not. For a large class of web software, Preact is enough.
