# @voluspalabs/lint

@voluspalabs/lint is a strict and opinionated linting configuration for modern TypeScript applications, powered by [Biome](https://biomejs.dev). It enforces maximum type safety and code quality, ensuring a clean and consistent codebase. Once set up, it automatically lints, fixes, and formats your code on save.

## Installation

Install the package via npm:

```zsh
pnpm add -D --save-exact @voluspalabs/lint @biomejs/biome
```

Or via Bun:

```zsh
bun add -D --save-exact @voluspalabs/lint @biomejs/biome
```

If you’re using VS Code, ensure these extensions are installed:

```zsh
code --install-extension biomejs.biome
code --install-extension bradlc.vscode-tailwindcss
```

## Setup

Create a biome.json file with the following content:

```json
{
  "$schema": "https://biomejs.dev/schemas/1.9.4/schema.json",
  "extends": ["@voluspalabs/lint"]
}
```

@voluspalabs/lint is optimized for VS Code. To enable full formatting and fixing on save, create a .vscode/settings.json file with the following content:

```json
{
  "typescript.tsdk": "node_modules/typescript/lib",
  "editor.defaultFormatter": "biomejs.biome",
  "editor.formatOnSave": true,
  "editor.formatOnPaste": true,
  "emmet.showExpandedAbbreviation": "never",
  "editor.codeActionsOnSave": {
    "source.fixAll.biome": "explicit",
    "source.organizeImports.biome": "explicit"
  },
  "[typescript]": {
    "editor.defaultFormatter": "biomejs.biome"
  },
  "[json]": {
    "editor.defaultFormatter": "biomejs.biome"
  },
  "[javascript]": {
    "editor.defaultFormatter": "biomejs.biome"
  },
  "[jsonc]": {
    "editor.defaultFormatter": "biomejs.biome"
  },
  "[typescriptreact]": {
    "editor.defaultFormatter": "biomejs.biome"
  }
}
```

Finally, make sure your tsconfig.json (if present) has strictNullChecks enabled.

```json
{
  "compilerOptions": {
    "strictNullChecks": true
  }
}
```

## Usage

@voluspalabs/lint automatically lints, fixes, and formats your code on save. To run it manually, use the following command:

```zsh
biome check
```

Or with changes:

```zsh
biome check --write
```

You can disable specific rules per line by appending a [comment at the end](https://biomejs.dev/linter/#ignore-code).

## License

This project is licensed under the MIT License. See the LICENSE file for more details.
