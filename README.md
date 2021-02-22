A TypeScript loader for Cosmiconfig

## Installation

```bash
yarn add cosmiconfig cosmiconfig-ts-loader
```
Don't forget to install `cosmiconfig` as peer dependencies.

## Usage

```typescript
import path from 'path'
import { cosmiconfig, cosmiconfigSync } from 'cosmiconfig';
import typeScriptLoader from 'cosmiconfig-ts-loader';

// via either cosmiconfigSync API
const moduleName = 'myModuleName';
  const explorer = cosmiconfigSync(moduleName, {
    loaders: {
      '.ts': typeScriptLoader(),
    },
  }).load(path.resolve(__dirname, `${moduleName}.config.ts`)); // please use `load` instead of `search` to directly load config file

// or cosmiconfig API
(() => {
  const moduleName = 'myModuleName';
  const explorer = await cosmiconfig(moduleName, {
    loaders: {
      '.ts': typeScriptLoader(),
    },
  }).load(path.resolve(__dirname, `${moduleName}.config.ts`)); // please use `load` instead of `search` to directly load config file
})()
```