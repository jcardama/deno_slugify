# Deno Slugify [![Build Status](https://travis-ci.org/jcardama/deno_slugify.svg?branch=master)](https://travis-ci.org/jcardama/deno_slugify)

A string validator and formater for case Style

```js
import { validate } from "./mod.ts";

slugify('some string') // some-string

// if you prefer something other than '-' as separator
slugify('some string', '_')  // some_string
```

## Options

```js
slugify('some string', {
  replacement: '-',    // replace spaces with replacement
  remove: null,        // regex to remove characters
  lower: true          // result in lower case
})
```

## Extend

Out of the box `slugify` comes with support for a handful of Unicode symbols. For example the `☢` (radioactive) symbol is not defined in the `charMap` object in [index.js][index] and therefore it will be stripped by default:

```js
slugify('unicode ♥ is ☢') // unicode-love-is
```

However you can extend the supported symbols, or override the existing ones with your own:

```js
slugify.extend({'☢': 'radioactive'})
slugify('unicode ♥ is ☢') // unicode-love-is-radioactive
```

Keep in mind that the `extend` method extends/overrides the default `charMap` for the entire process.