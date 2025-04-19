# Inga 🎨

## A Modern Indentation-Based Templating Language

[![npm version](https://img.shields.io/npm/v/inga-cli.svg)](https://www.npmjs.com/package/inga-cli) [![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

---

## 🚀 Overview

A first draft.

Inga reimagines how HTML, CSS, and JavaScript come together in templates by combining the clarity of indentation-based syntax with powerful, built‑in styling, state, and Node.js integration. Inspired by Pug/Jade, Inga streamlines your workflow with:

- **Minimalist Syntax** &mdash; Eliminate redundant tags, brackets, and noise.
- **Integrated Styling** &mdash; Write CSS directly within element definitions.
- **Reactive State** &mdash; Native state management and reactivity.
- **Component System** &mdash; Props, slots, lifecycle hooks, and mixins.
- **Node.js Bridge** &mdash; Seamless access to the Node ecosystem.
- **Developer Experience** &mdash; Hot‑reload, clear errors, and VS Code support.

---

## 📦 Installation

```bash
npm install -g inga-cli
```

**Create a new project**:

```bash
inga new my-project
cd my-project
```

**Start dev server**:

```bash
inga dev
```

Build for production:

```bash
inga build
```  

Lint your templates:

```bash
inga lint
```

---

## 🛠️ Quickstart Example

```jade
// index.inga
document HomePage
  head
    title: Welcome to Inga
    meta charset: utf-8
    viewport: width=device-width, initial-scale=1

  body
    header #main-header
      h1: Hello, Inga!

    main
      p: Count: {state.count}
      button @click={state.count++}: Increment

      if state.count > 5
        p .info: 🎉 You reached {state.count}!

  state
    count: 0
```

Run `inga dev` and watch your app hot‑reload as you tweak your template.

---

## ✨ Core Concepts

1. **Significant Whitespace**: Structure your markup via indentation.
2. **Element Definition**:

   ```jade
   div #container .wrapper
     // becomes <div id="container" class="wrapper"></div>
   ```

3. **Inline Styles**:

   ```jade
   div #sidebar
     style
       width: 250px
       background: #f5f5f5
   ```

4. **Components & Mixins**:

   ```jade
   component Button(text, type="primary")
     button .btn .btn-{type}
       span: {text}

   +Button("Click Me", "success")
   ```

5. **State & Reactivity**:
   Built‑in `state`, `computed`, and `effect` blocks for dynamic behavior.

---

## 📐 Responsive & Advanced Features

- **Media Queries & Container Queries** directly in style blocks.
- **Configurable Breakpoints** via a `config` section.
- **Lifecycle Hooks**: `onMount`, `onUpdate`, `onDestroy`.
- **Context & Dependency Injection** for themeing and global stores.
- **Control Flow**: `if`, `else if`, `else`, `each`, and `while`.

---

## 🗺️ Roadmap

1. Enhance performance and bundle size.
2. VS Code extension: syntax highlighting, snippets, and preview.
3. Plugin ecosystem & template marketplace.
4. TypeScript definitions and stricter typing.
5. Community templates, docs, and examples.

---

## 🤝 Contributing

1. Fork the repo on GitHub.
2. Create a feature branch: `git checkout -b feature/foo`.
3. Commit your changes: `git commit -am 'Add foo'`.
4. Push to the branch: `git push origin feature/foo`.
5. Open a Pull Request.

Please read [CONTRIBUTING.md](CONTRIBUTING.md) for details on our code of conduct and the process for submitting pull requests.

## Hints for Contributors

- **Indentation**: Use spaces (2 spaces) for indentation. No tabs.
- **Markdown code blocks**: Use triple backticks (```) for code blocks as usual, but call it `jade`, this is the closest language to Inga.
- **Testing**: Early on testing is crucial, how you do it is at this point up to you. We will provide a testing framework later on.
- **Documentation**: Keep the documentation up to date with your changes. Use the `docs` folder for any new documentation files.

## 📄 License

Distributed under the [GPLv3 License](LICENSE). That means your changes are available under the same terms as Inga itself.
