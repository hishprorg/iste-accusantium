# @hishprorg/iste-accusantium <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

`Array.prototype.concat`, but made safe by ignoring Symbol.isConcatSpreadable

## Getting started

```sh
npm install --save @hishprorg/iste-accusantium
```

## Usage/Examples

```js
var safeConcat = require('@hishprorg/iste-accusantium');
var assert = require('assert');

assert.deepEqual([].concat([1, 2], 3, [[4]]), [1, 2, 3, [4]], 'arrays spread as expected with normal concat');
assert.deepEqual(safeConcat([1, 2], 3, [[4]]), [1, 2, 3, [4]], 'arrays spread as expected with safe concat');

String.prototype[Symbol.isConcatSpreadable] = true;
assert.deepEqual([].concat('foo', Object('bar')), ['foo', 'b', 'a', 'r'], 'spreadable String objects are spread with normal concat!!!');
assert.deepEqual(safeConcat('foo', Object('bar')), ['foo', Object('bar')], 'spreadable String objects are not spread with safe concat');

Array.prototype[Symbol.isConcatSpreadable] = false;
assert.deepEqual([].concat([1, 2], 3, [[4]]), [[], [1, 2], 3, [[4]]], 'non-concat-spreadable arrays do not spread with normal concat!!!');
assert.deepEqual(safeConcat([1, 2], 3, [[4]]), [1, 2, 3, [4]], 'non-concat-spreadable arrays still spread with safe concat');
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@hishprorg/iste-accusantium
[npm-version-svg]: https://versionbadg.es/ljharb/@hishprorg/iste-accusantium.svg
[deps-svg]: https://david-dm.org/ljharb/@hishprorg/iste-accusantium.svg
[deps-url]: https://david-dm.org/ljharb/@hishprorg/iste-accusantium
[dev-deps-svg]: https://david-dm.org/ljharb/@hishprorg/iste-accusantium/dev-status.svg
[dev-deps-url]: https://david-dm.org/ljharb/@hishprorg/iste-accusantium#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@hishprorg/iste-accusantium.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@hishprorg/iste-accusantium.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@hishprorg/iste-accusantium.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@hishprorg/iste-accusantium
[codecov-image]: https://codecov.io/gh/ljharb/@hishprorg/iste-accusantium/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/ljharb/@hishprorg/iste-accusantium/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/ljharb/@hishprorg/iste-accusantium
[actions-url]: https://github.com/hishprorg/iste-accusantium/actions
