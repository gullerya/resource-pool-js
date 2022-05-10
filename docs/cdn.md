# CDN provisioning

CDN provisioning is a general convenience feature, which also provides:
- security:
  - __HTTPS__ only
  - __intergrity__ checksum provided, see below
- performance
  - highly __available__ (with many geo spread edges)
  - agressive __caching__ setup

## Usage

Import `resource-pool` directly from CDN:
```js
import {  } from 'https://libs.gullerya.com/resource-pool/x.y.z/resource-pool.min.js';
```

> Note: regular and minified resouces are available.

> Note: replace the `x.y.z` with the desired version, one of the listed in the [changelog](changelog.md).

## Integrity (SRI)

Security feature `integrity` was introduced specifically to fortify a consumption of a CDN delivered modules.
`resource-pool` adheres to this effort and provides integrity checksums per release (starting from version `4.2.4`).

### Usage example

To begin with, detailed description on SRI (Subresource Integrity) [found here](https://developer.mozilla.org/en-US/docs/Web/Security/Subresource_Integrity).

Since `resource-pool` provides ES6 module syntax, the approach described in the documentation above and elsewhere is not applicable.
In this case, and until a better way available (like [this proposal](https://github.com/tc39/proposal-import-assertions/issues/113) of myself), one is required to use `<link rel="modulepreload">` in __addition__ to the regular `import` in order to enforce integrity validation.

Thus, please add the below HTML piece in your HTML, when willing to enforce the module's integrity:
```html
<link rel="modulepreload" 
  href="https://libs.gullerya.com/resource-pool/x.y.z/resource-pool.min.js"
  integrity="hash">
```

> Note: version (to be put instead of `x.y.z`) and resource kind (regular/minified) should be the same as you use in the application. Accordingly, replace the `hash` with the relevant value as per version and resource, see below.

> Note: `modulepreload` in general and `integrity` attribute with it in particular are still having a limited support.

### Integrity checksums

Checksums provided per version for both, regular and minified resources.

From version `0.0.1` SRI hashes provided via Git and NPM, by `sri.json` file:
- Git: check out version tag, then find `sri.json` file in the repo root
- GitHub: visit the file via GitHub UI at version tag, eg [this link](https://github.com/gullerya/resource-pool-js/blob/v4.6.6/sri.json) (pay attention to the version tag in the URL)
- NPM: do install `resource-pool` via `npm install...`, then find `sri.json` file in your `node_modules/@gullerya/resource-pool` folder

Below are SRI hashes of the pre-`4.6.6` version:

| Version | Resource | Integrity checksum (hash) |
|---------|----------|---------------------------|
|<!--INSERT-MARKER-->
