# markdown-toc [![NPM version](https://badge.fury.io/js/markdown-toc.svg)](http://badge.fury.io/js/markdown-toc)

> Generate a markdown TOC (table of contents) with Remarkable.

## Install with [npm](npmjs.org)

```bash
npm i markdown-toc --save
```

## Usage

```js
var toc = require('markdown-toc');

toc('# One\n\n# Two').content;
// Results in:
// - [One](#one)
// - [Two](#two)
```

To allow customization of the output, an object is returned with the following properties:

 - `content` **{String}**: The generated table of contents. Unless you want to customize rendering, this is all you need.
 - `highest` **{Number}**: The highest level heading found. This is used to adjust indentation. 
 - `tokens` **{Array}**: Headings tokens that can be used for custom rendering


### toc.insert

Insert a table of contents immediately after an _opening_ `<!-- toc -->` code comment, or replace an existing TOC if both an _opening_ comment and a _closing_ comment (`<!-- tocstop -->`) are found. (This strategy works well since code comments in markdown are hidden when viewed as HTML, e.g. on GitHub README's for example).

**Example**

```markdown
<!-- toc -->
- old toc 1
- old toc 2
- old toc 3
<!-- tocstop -->

## abc
This is a b c.

## xyz
This is x y z.
```

Would result in something like:

```markdown
<!-- toc -->
- [abc](#abc)
- [xyz](#xyz)
<!-- tocstop -->

## abc
This is a b c.

## xyz
This is x y z.
```

## Options


### options.bullet

Type: `String|Array`

Default: `*`

The bullet to use for each item in the generated TOC. If passed as an array (`['*', '-', '+']`), the bullet point strings will be used based on the header depth.


### options.maxDepth

Type: `Number`

Default: `3`

Use headings whose depth is at most maxDepth.


### options.firsth1

Type: `Boolean`

Default: `true`

Exclude the first h1-level heading in a file. For example, this prevents the first heading in a README from showing up in the TOC.


## Run tests

```bash
npm test
```


## Contributing
Pull requests and stars are always welcome. For bugs and feature requests, [please create an issue](https://github.com/jonschlinkert/markdown-toc/issues)

## Author

**Jon Schlinkert**
 
+ [github/jonschlinkert](https://github.com/jonschlinkert)
+ [twitter/jonschlinkert](http://twitter.com/jonschlinkert) 

## License
Copyright (c) 2014 Jon Schlinkert  
Released under the MIT license

***

_This file was generated by [verb](https://github.com/assemble/verb) on December 21, 2014._
