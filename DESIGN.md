# Inga Language Design Document

## Overview

Inga is a modern templating language for web development that reimagines how HTML, CSS, and JavaScript can be integrated. Building on the indentation-based approach of Pug/Jade while addressing its limitations, Inga provides a more intuitive and powerful way to build web interfaces with seamless Node.js integration.

## Core Design Principles

1. **Significant Whitespace**: Use indentation to indicate hierarchical structure
2. **Minimalist Syntax**: Reduce visual noise by eliminating redundant tags and brackets
3. **Integrated Styling**: Directly embed styling within element definitions
4. **Reactive State**: Built-in state management for dynamic interfaces
5. **Node.js Integration**: Seamless access to the Node.js ecosystem
6. **Developer Experience**: Prioritize readability, maintainability, and tooling

## Basic Syntax

### Document Structure

```jade
document MyPage
  head
    title: My Inga Page
    meta charset: utf-8
    viewport: width=device-width, initial-scale=1
  
  body
    header #main-header
      h1: Welcome to Inga
    
    main
      p: This is an example of Inga syntax
    
    footer
      p: Copyright 2025
```

### Element Definition

Elements are defined by their name followed by optional attributes:

```jade
div #container .wrapper
  // This creates <div id="container" class="wrapper"></div>
```

### Content

Text content follows elements after a colon:

```jade
p: This is a paragraph
h1: This is a heading
```

Multiline content uses the pipe syntax:

```jade
p
  | This is a paragraph with
  | multiple lines of text
  | that will be joined together
```

### Attributes

Attributes can be specified in three ways:

1. ID selector: `#elementId`
2. Class selector: `.className`
3. Parenthesized list: `(href="link" target="_blank")`

```jade
a #cta-button .primary(href="/signup" target="_blank"): Sign Up
```

### Styles

Styles are defined in nested `style` blocks:

```jade
div #sidebar
  style
    width: 250px
    background: #f5f5f5
    padding: 1rem
```

## Advanced Features

### Components

Components are reusable templates with props:

```jade
component Button(text, type="primary", disabled=false)
  button .btn .btn-{type}(disabled={disabled})
    span: {text}
    slot
    
    style
      padding: 0.5rem 1rem
      border-radius: 4px
      background: {getColorFromType(type)}

// Usage
+Button("Submit", "success")
  icon: check
```

### State Management

Built-in reactive state:

```jade
state
  count: 0
  user: { name: "", loggedIn: false }

div
  p: Count: {state.count}
  button @click={state.count++}: Increment
  
  if state.user.loggedIn
    p: Welcome, {state.user.name}
  else
    p: Please log in
```

### Lifecycle Hooks

```jade
lifecycle
  onMount
    // Code that runs after component mounts
    fetchData()
  
  onUpdate(prevProps)
    // Runs on prop changes
    if (prevProps.id !== props.id)
      refetchData()
  
  onDestroy
    // Cleanup code
    clearInterval(timer)
```

### Control Flow

```jade
if condition
  p: This will show if condition is true
else if otherCondition
  p: This will show if otherCondition is true
else
  p: This is the fallback

each item in items
  li: {item.name}

while condition
  p: This will repeat
```

### Node.js Integration

```jade
import
  fs from "fs"
  path from "path"
  _ from "lodash"
  myUtil from "./utils"

script
  // Node.js code here
  const data = fs.readFileSync('data.json', 'utf8')
  const items = JSON.parse(data)
  
  function processItems() {
    return _.sortBy(items, 'name')
  }
```

### Mixins

```jade
mixin Avatar(user, size="medium")
  div .avatar .avatar-{size}
    if user.profileImage
      img(src=user.profileImage alt=user.name)
    else
      div .avatar-placeholder: {user.initials}

// Usage
+Avatar(currentUser, "large")
```

### Template Inheritance

```jade
// layout.inga
document BaseLayout
  head
    title: {title || "Default Title"}
    block head
  body
    header
      block header
        h1: Default Header
    
    main
      block content
    
    footer
      block footer
        p: Default Footer

// page.inga
extends layout

block head
  meta description: Page description

block content
  p: This is my page content
```

### Responsive Design

```jade
div #hero
  h1: Responsive Title
    style
      font-size: 3rem
      
      @media (max-width: 768px)
        font-size: 2rem
      
      @media (max-width: 480px)
        font-size: 1.5rem
        text-align: center
```

Or using responsive mixins:

```jade
component ResponsiveContainer
  div
    style
      width: 1200px
      margin: 0 auto
      
      +screen(tablet)
        width: 768px
      
      +screen(mobile)
        width: 100%
        padding: 0 1rem

// Usage
+ResponsiveContainer
  p: Content here
```

## Improvements Over Pug

1. **Integrated Styling**: Unlike Pug, Inga has first-class CSS support built in
2. **State Management**: Native state handling without external libraries
3. **Component System**: More powerful than Pug's mixins with props, slots, and lifecycle
4. **Better Error Messages**: Improved developer experience with clear, helpful errors
5. **Node.js Integration**: Direct access to Node.js APIs rather than just templates
6. **Responsive Design**: Native support for responsive layouts
7. **TypeScript Support**: Better type checking and autocompletion
8. **Performance**: Optimized compile-time and runtime performance

## Implementation Strategy

Inga will be implemented with:

1. **Parser**: Custom parser built on proven indentation-based parsing techniques
2. **Compiler**: Transforms Inga code into optimized HTML/CSS/JS
3. **Runtime**: Light runtime for state management and reactivity
4. **Node.js Bridge**: Secure sandbox for Node.js integration
5. **Development Server**: Hot-reloading for rapid iteration
6. **VS Code Extension**: Syntax highlighting, autocompletion, and diagnostics

## Tooling Ecosystem

1. **VS Code Extension**: All-in-one plugin providing:
   - Syntax highlighting
   - Autocompletion
   - Diagnostics and error checking
   - Formatting
   - Snippets
   - Preview pane
   - Debugging integration

2. **CLI Tools**:
   - `inga build` - Compile Inga to production assets
   - `inga dev` - Development server with hot reloading
   - `inga lint` - Linting and code quality checks
   - `inga new` - Project scaffolding

3. **Build System Integration**:
   - Webpack loader
   - Rollup plugin
   - Vite plugin

## Roadmap

1. **Phase 1**: Core language features and parser
2. **Phase 2**: Component system and state management
3. **Phase 3**: Node.js integration
4. **Phase 4**: VS Code extension and tooling
5. **Phase 5**: Performance optimization and production readiness
6. **Phase 6**: Community building and ecosystem development

## Use Cases

Inga is particularly well-suited for:

1. **Single-page applications**
2. **Static site generation**
3. **Component libraries**
4. **Prototyping and rapid development**
5. **Full-stack JavaScript applications**

## Community and Contribution

Inga will be open source with:

1. **GitHub repository**
2. **Documentation site**
3. **Component library**
4. **Examples and templates**
5. **Community forums and Discord**
6. **Contribution guidelines**
7. **Roadmap and feature requests**

## License

Inga is licensed under the GPL-3.0 License. See the [LICENSE](LICENSE) file for details.
