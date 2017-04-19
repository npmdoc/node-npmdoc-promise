# npmdoc-promise

#### api documentation for  [promise (v7.1.1)](https://github.com/then/promise)  [![npm package](https://img.shields.io/npm/v/npmdoc-promise.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-promise) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-promise.svg)](https://travis-ci.org/npmdoc/node-npmdoc-promise)

#### Bare bones Promises/A+ implementation

[![NPM](https://nodei.co/npm/promise.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/promise)

- [https://npmdoc.github.io/node-npmdoc-promise/build/apidoc.html](https://npmdoc.github.io/node-npmdoc-promise/build/apidoc.html)

[![apidoc](https://npmdoc.github.io/node-npmdoc-promise/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-promise/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-promise/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-promise/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "ForbesLindesay"
    },
    "bugs": {
        "url": "https://github.com/then/promise/issues"
    },
    "dependencies": {
        "asap": "~2.0.3"
    },
    "description": "Bare bones Promises/A+ implementation",
    "devDependencies": {
        "acorn": "^1.0.1",
        "better-assert": "*",
        "istanbul": "^0.3.13",
        "mocha": "*",
        "promises-aplus-tests": "*",
        "rimraf": "^2.3.2"
    },
    "directories": {},
    "dist": {
        "shasum": "489654c692616b8aa55b0724fa809bb7db49c5bf",
        "tarball": "https://registry.npmjs.org/promise/-/promise-7.1.1.tgz"
    },
    "gitHead": "90757a38c86975f36893012581b72315b352d482",
    "homepage": "https://github.com/then/promise",
    "license": "MIT",
    "main": "index.js",
    "maintainers": [
        {
            "name": "forbeslindesay"
        },
        {
            "name": "nathan7"
        }
    ],
    "name": "promise",
    "optionalDependencies": {},
    "repository": {
        "type": "git",
        "url": "git+https://github.com/then/promise.git"
    },
    "scripts": {
        "coverage": "istanbul cover node_modules/mocha/bin/_mocha -- --bail --timeout 200 --slow 99999 -R dot",
        "prepublish": "node build",
        "pretest": "node build",
        "pretest-extensions": "node build",
        "pretest-memory-leak": "node build",
        "pretest-resolve": "node build",
        "test": "mocha --bail --timeout 200 --slow 99999 -R dot && npm run test-memory-leak",
        "test-extensions": "mocha test/extensions-tests.js --timeout 200 --slow 999999",
        "test-memory-leak": "node --expose-gc test/memory-leak.js",
        "test-resolve": "mocha test/resolver-tests.js --timeout 200 --slow 999999"
    },
    "version": "7.1.1"
}
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
