# @voluspalabs/lint

A strict and opinionated linting and formatting configuration for modern TypeScript applications, powered by [Biome](https://biomejs.dev), [Oxlint](https://oxc.rs), and [Oxfmt](https://oxc.rs).

## Installation

Install the package and the tools you want to use:

### Biome (recommended)

```zsh
bun add -D --save-exact @voluspalabs/lint @biomejs/biome
```

### Oxlint + Oxfmt

```zsh
bun add -D --save-exact @voluspalabs/lint oxlint oxfmt
```

### All tools

```zsh
bun add -D --save-exact @voluspalabs/lint @biomejs/biome oxlint oxfmt
```

## Setup

### Biome

Create a `biome.jsonc` (or `biome.json`) with:

```json
{
  "$schema": "https://biomejs.dev/schemas/2.4.1/schema.json",
  "extends": ["@voluspalabs/lint"]
}
```

### Oxlint

Create a `.oxlintrc.json` with:

```json
{
  "$schema": "./node_modules/oxlint/configuration_schema.json",
  "extends": ["./node_modules/@voluspalabs/lint/.oxlintrc.json"]
}
```

> **Note:** Oxlint does not support Node.js package exports in `extends`. The explicit `./node_modules/` path is required.

### Oxfmt

Oxfmt does not support an `extends` mechanism. Copy the provided config into your project root:

```zsh
cp node_modules/@voluspalabs/lint/.oxfmtrc.jsonc .oxfmtrc.jsonc
```

## VS Code

### Biome

Install the extension and configure format-on-save:

```zsh
code --install-extension biomejs.biome
```

```json
{
  "editor.defaultFormatter": "biomejs.biome",
  "editor.formatOnSave": true,
  "editor.codeActionsOnSave": {
    "source.fixAll.biome": "explicit",
    "source.organizeImports.biome": "explicit"
  },
  "[typescript]": { "editor.defaultFormatter": "biomejs.biome" },
  "[typescriptreact]": { "editor.defaultFormatter": "biomejs.biome" },
  "[javascript]": { "editor.defaultFormatter": "biomejs.biome" },
  "[json]": { "editor.defaultFormatter": "biomejs.biome" },
  "[jsonc]": { "editor.defaultFormatter": "biomejs.biome" }
}
```

### Oxlint + Oxfmt

```zsh
code --install-extension oxc.oxc-vscode
```

```json
{
  "editor.defaultFormatter": "oxc.oxc-vscode",
  "editor.formatOnSave": true,
  "[typescript]": { "editor.defaultFormatter": "oxc.oxc-vscode" },
  "[typescriptreact]": { "editor.defaultFormatter": "oxc.oxc-vscode" },
  "[javascript]": { "editor.defaultFormatter": "oxc.oxc-vscode" }
}
```

## Usage

### Biome

```zsh
biome check           # lint + format check
biome check --write   # lint + format + fix
```

### Oxlint + Oxfmt

```zsh
oxlint                # lint
oxfmt --check         # format check
oxfmt --write         # format + fix
```

## License

This project is licensed under the MIT License. See the LICENSE file for more details.
