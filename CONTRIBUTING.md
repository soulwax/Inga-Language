# Contributing to Inga

Thank you for your interest in contributing to Inga! We welcome all contributions — from bug reports and documentation improvements to new features and tooling enhancements.

## Table of Contents

1. [Code of Conduct](#code-of-conduct)
2. [Report a Bug](#report-a-bug)
3. [Propose a Feature](#propose-a-feature)
4. [Development Setup](#development-setup)
5. [Coding Style](#coding-style)
6. [Commit Messages](#commit-messages)
7. [Pull Request Process](#pull-request-process)
8. [Testing](#testing)
9. [License](#license)

---

## Code of Conduct

All contributors are expected to uphold our [Code of Conduct](./CODE_OF_CONDUCT.md). Be respectful, collaborative, and inclusive. Violations may result in contribution removal or repository access restrictions.

---

## Report a Bug

1. Search existing issues to see if your bug has already been reported.
2. If not, open a new issue in the [GitHub Issues](https://github.com/your-org/inga/issues) tracker.
3. Include the following details:
   - **Inga version** (`inga --version`)
   - **Platform** (OS, Node.js version)
   - **Steps to reproduce**
   - **Expected vs. actual behavior**
   - **Minimal code sample** that demonstrates the issue

---

## Propose a Feature

1. Check open feature requests to avoid duplicates.
2. Open a new issue labeled **enhancement** with:
   - A clear description of the feature
   - Use cases and motivation
   - API proposal or syntax examples
3. Discuss and refine the proposal with maintainers and the community.

---

## Development Setup

Clone the repository and install dependencies:

```bash
git clone https://github.com/your-org/inga.git
cd inga
npm install
```

Run the development server with hot reload:

```bash
inga dev
```

Lint templates and code:

```bash
inga lint
npm run lint:js
```

Build for production:

```bash
inga build
```

---

## Coding Style

- Follow existing indentation-based formatting for Inga templates.
- In JavaScript/TypeScript files, adhere to the ESLint and Prettier configurations in the repo.
- Keep code modular and well-documented. Add JSDoc/TSDoc comments for public APIs.
- Write clear, concise commit messages (see [Commit Messages](#commit-messages)).

---

## Commit Messages

Use a conventional commit format:

```plaintext
<type>(<scope>): <short summary>

<body>  
[Footer]
```

- **type**: feat, fix, docs, style, refactor, test, chore
- **scope**: optional component or file name
- **body**: more detailed description
- **footer**: references to issues (e.g., `Closes #123`)

Example:

```plaintext
feat(parser): add support for container queries in style blocks

- Implemented @container rule parsing
- Added tests for container query scenarios

Closes #456
```

---

## Pull Request Process

1. Fork the repository and create your branch:

    ```bash
    git checkout -b feat/cool-new-feature
    ```

2. Commit changes to your branch:

    ```bash
    git commit -m "feat(parser): support new syntax"
    ```  

3. Push to your fork:

    ```bash
    git push origin feat/cool-new-feature
    ```

4. Open a Pull Request on the main repo against the `main` branch.
5. The PR will be reviewed; address feedback and iterate until approved.

---

## Testing

- Write unit tests for new features and bug fixes.
- Run tests with:

```bash
npm test
```

- Tests should pass on all supported Node.js versions (see `.nvmrc`).

---

## License

By contributing, you agree that your contributions will be licensed under the project’s [GPLv3 License](LICENSE). That means your changes are available under the same terms as Inga itself.
