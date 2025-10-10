# edm115-lint
My very own sensible lint and style configs to reuse across my repos

## Usage
```pwsh
pnpm add -D edm115-lint
```

### ESLint
```ts
// eslint.stylistic.config.ts
import stylistic from "@stylistic/eslint-plugin"
import tsParser from "@typescript-eslint/parser"
import edm115Lint from "edm115-lint/eslint-stylistic.json"

export default [
  { ignores: [ "**/dist/", "**/node_modules/" ] },
  {
    files: ["**/*.ts"],
    linterOptions: { reportUnusedDisableDirectives: false },
    languageOptions: {
      ecmaVersion: "latest",
      sourceType: "module",
      parser: tsParser,
      parserOptions: {
        ecmaVersion: "latest",
        tsconfigRootDir: import.meta.dirname,
      },
    },
    plugins: { "@stylistic": stylistic },
    rules: edm115Lint,
  },
]
```

### OxLint
```json
// .oxlintrc.json
{
  "$schema": "./node_modules/oxlint/configuration_schema.json",
  "extends": ["./node_modules/edm115-lint/.oxlintrc.base.json"],
  "plugins": [ "vue" ],
  "env": {
    "es2025": true,
    "browser": true,
    "shared-node-browser": true
  },
  "ignorePatterns": [
    "**/.nuxt/",
    "**/.output/",
    "**/dist/",
    "**/node_modules/"
  ]
}
```
