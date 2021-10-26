# leac

[![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)](https://github.com/mxxii/leac/blob/main/LICENSE)

Lexer / tokenizer.


## Features

- **Lightweight**. Zero dependencies. Not a lot of code.

- **Well tested** - comes will tests for everything including examples.

- **Compact syntax** - less boilerplate. Rule name is enough when it is the same as the lookup string.

- **No failures** - it just stops when there are no matching rules and returns the information about whether it completed and where it stopped in addition to tokens array.

- **Composable lexers** - instead of states within a lexer.

- **Stateless lexers** - all inputs are passed as arguments, all outputs are returned in a result object.

- **No streaming** - accepts a string at a time.

- **Only text tokens, no arbitraty values**. It seems to be a good habit to have tokens that are *trivially* serializable back into valid input string. Don't do the parser's job. There are a couple of convenience features such as the ability to discard matches or string replacements for regular expression rules but that has to be used mindfully.


## Install

```shell
> npm i leac
```


## Examples

- [JSON](https://github.com/mxxii/leac/blob/main/examples/json.ts);
- [Calc](https://github.com/mxxii/leac/blob/main/examples/calc.ts).

```typescript
const lex = createLexer([
  { name: '-', str: '-' },
  { name: '+' },
  { name: 'ws', regex: /\s+/, discard: true },
  { name: 'number', regex: /[0-9]|[1-9][0-9]+/ },
]);

const { tokens, offset, complete } = lex('2 + 2');
```


## API

- [docs/index.md](https://github.com/mxxii/leac/blob/main/docs/index.md)


## What about ...?

- performance - The code is very simple but I won't put any unverified assumptions here. I'd be grateful to anyone who can provide a good benchmark project to compare different lexers.

- stable release - Current release is well thought out and tested. I leave a chance that some changes might be needed based on feedback. Before version 1.0.0 this will be done without a deprecation cycle.


## Some other lexer / tokenizer packages

- [moo](https://github.com/no-context/moo);
- [doken](https://github.com/yishn/doken);
- [tokenizr](https://github.com/rse/tokenizr);
- [flex-js](https://github.com/sormy/flex-js);
- *and more, with varied level of maintenance.*
