# api documentation for  [promise (v7.1.1)](https://github.com/then/promise)  [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-promise.svg)](https://travis-ci.org/npmdoc/node-npmdoc-promise)
#### Bare bones Promises/A+ implementation

[![NPM](https://nodei.co/npm/promise.png?downloads=true)](https://www.npmjs.com/package/promise)

[![apidoc](https://npmdoc.github.io/node-npmdoc-promise/build/screen-capture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-promise_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-promise/build..beta..travis-ci.org/apidoc.html)

![package-listing](https://npmdoc.github.io/node-npmdoc-promise/build/screen-capture.npmPackageListing.svg)



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
            "name": "forbeslindesay",
            "email": "forbes@lindesay.co.uk"
        },
        {
            "name": "nathan7",
            "email": "nathan@nathan7.eu"
        }
    ],
    "name": "promise",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
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



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module promise](#apidoc.module.promise)
1.  [function <span class="apidocSignatureSpan">promise.</span>_61 ()](#apidoc.element.promise._61)
1.  [function <span class="apidocSignatureSpan">promise.</span>all (arr)](#apidoc.element.promise.all)
1.  [function <span class="apidocSignatureSpan">promise.</span>denodeify (fn, argumentCount)](#apidoc.element.promise.denodeify)
1.  [function <span class="apidocSignatureSpan">promise.</span>disableSynchronous ()](#apidoc.element.promise.disableSynchronous)
1.  [function <span class="apidocSignatureSpan">promise.</span>enableSynchronous ()](#apidoc.element.promise.enableSynchronous)
1.  [function <span class="apidocSignatureSpan">promise.</span>nodeify (fn)](#apidoc.element.promise.nodeify)
1.  [function <span class="apidocSignatureSpan">promise.</span>race (values)](#apidoc.element.promise.race)
1.  [function <span class="apidocSignatureSpan">promise.</span>reject (value)](#apidoc.element.promise.reject)
1.  [function <span class="apidocSignatureSpan">promise.</span>resolve (value)](#apidoc.element.promise.resolve)
1.  object <span class="apidocSignatureSpan">promise.</span>_10
1.  object <span class="apidocSignatureSpan">promise.</span>_97
1.  object <span class="apidocSignatureSpan">promise.</span>rejection_tracking

#### [module promise.rejection_tracking](#apidoc.module.promise.rejection_tracking)
1.  [function <span class="apidocSignatureSpan">promise.rejection_tracking.</span>disable ()](#apidoc.element.promise.rejection_tracking.disable)
1.  [function <span class="apidocSignatureSpan">promise.rejection_tracking.</span>enable (options)](#apidoc.element.promise.rejection_tracking.enable)



# <a name="apidoc.module.promise"></a>[module promise](#apidoc.module.promise)

#### <a name="apidoc.element.promise._61"></a>[function <span class="apidocSignatureSpan">promise.</span>_61 ()](#apidoc.element.promise._61)
- description and source-code
```javascript
function noop() {}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.promise.all"></a>[function <span class="apidocSignatureSpan">promise.</span>all (arr)](#apidoc.element.promise.all)
- description and source-code
```javascript
all = function (arr) {
  var args = Array.prototype.slice.call(arr);

  return new Promise(function (resolve, reject) {
    if (args.length === 0) return resolve([]);
    var remaining = args.length;
    function res(i, val) {
      if (val && (typeof val === 'object' || typeof val === 'function')) {
        if (val instanceof Promise && val.then === Promise.prototype.then) {
          while (val._81 === 3) {
            val = val._65;
          }
          if (val._81 === 1) return res(i, val._65);
          if (val._81 === 2) reject(val._65);
          val.then(function (val) {
            res(i, val);
          }, reject);
          return;
        } else {
          var then = val.then;
          if (typeof then === 'function') {
            var p = new Promise(then.bind(val));
            p.then(function (val) {
              res(i, val);
            }, reject);
            return;
          }
        }
      }
      args[i] = val;
      if (--remaining === 0) {
        resolve(args);
      }
    }
    for (var i = 0; i < args.length; i++) {
      res(i, args[i]);
    }
  });
}
```
- example usage
```shell
...

Converts values and foreign promises into Promises/A+ promises.  If you pass it a value then it returns a Promise for that value
.  If you pass it something that is close to a promise (such as a jQuery attempt at a promise) it returns a Promise that takes on
 the state of 'value' (rejected or fulfilled).

#### Promise.reject(value)

Returns a rejected promise with the given value.

#### Promise.all(array)

Returns a promise for an array.  If it is called with a single argument that 'Array.isArray' then this returns a promise for a copy
 of that array with any promises replaced by their fulfilled values.  e.g.

'''js
Promise.all([Promise.resolve('a'), 'b', Promise.resolve('c')])
.then(function (res) {
  assert(res[0] === 'a')
...
```

#### <a name="apidoc.element.promise.denodeify"></a>[function <span class="apidocSignatureSpan">promise.</span>denodeify (fn, argumentCount)](#apidoc.element.promise.denodeify)
- description and source-code
```javascript
denodeify = function (fn, argumentCount) {
  if (
    typeof argumentCount === 'number' && argumentCount !== Infinity
  ) {
    return denodeifyWithCount(fn, argumentCount);
  } else {
    return denodeifyWithoutCount(fn);
  }
}
```
- example usage
```shell
...
  .then(function (res) {
    assert(res[0] === 'a')
    assert(res[1] === 'b')
    assert(res[2] === 'c')
  })
'''

#### Promise.denodeify(fn)

_Non Standard_

Takes a function which accepts a node style callback and returns a new function that returns a promise instead.

e.g.
...
```

#### <a name="apidoc.element.promise.disableSynchronous"></a>[function <span class="apidocSignatureSpan">promise.</span>disableSynchronous ()](#apidoc.element.promise.disableSynchronous)
- description and source-code
```javascript
disableSynchronous = function () {
  Promise.prototype.isPending = undefined;
  Promise.prototype.isFulfilled = undefined;
  Promise.prototype.isRejected = undefined;
  Promise.prototype.getValue = undefined;
  Promise.prototype.getReason = undefined;
  Promise.prototype.getState = undefined;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.promise.enableSynchronous"></a>[function <span class="apidocSignatureSpan">promise.</span>enableSynchronous ()](#apidoc.element.promise.enableSynchronous)
- description and source-code
```javascript
enableSynchronous = function () {
  Promise.prototype.isPending = function() {
    return this.getState() == 0;
  };

  Promise.prototype.isFulfilled = function() {
    return this.getState() == 1;
  };

  Promise.prototype.isRejected = function() {
    return this.getState() == 2;
  };

  Promise.prototype.getValue = function () {
    if (this._81 === 3) {
      return this._65.getValue();
    }

    if (!this.isFulfilled()) {
      throw new Error('Cannot get a value of an unfulfilled promise.');
    }

    return this._65;
  };

  Promise.prototype.getReason = function () {
    if (this._81 === 3) {
      return this._65.getReason();
    }

    if (!this.isRejected()) {
      throw new Error('Cannot get a rejection reason of a non-rejected promise.');
    }

    return this._65;
  };

  Promise.prototype.getState = function () {
    if (this._81 === 3) {
      return this._65.getState();
    }
    if (this._81 === -1 || this._81 === -2) {
      return 0;
    }

    return this._81;
  };
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.promise.nodeify"></a>[function <span class="apidocSignatureSpan">promise.</span>nodeify (fn)](#apidoc.element.promise.nodeify)
- description and source-code
```javascript
nodeify = function (fn) {
  return function () {
    var args = Array.prototype.slice.call(arguments);
    var callback =
      typeof args[args.length - 1] === 'function' ? args.pop() : null;
    var ctx = this;
    try {
      return fn.apply(this, arguments).nodeify(callback, ctx);
    } catch (ex) {
      if (callback === null || typeof callback == 'undefined') {
        return new Promise(function (resolve, reject) {
          reject(ex);
        });
      } else {
        asap(function () {
          callback.call(ctx, ex);
        })
      }
    }
  }
}
```
- example usage
```shell
...

var p = read('foo.json', 'utf8')
  .then(function (str) {
    return write('foo.json', JSON.stringify(JSON.parse(str), null, '  '), 'utf8')
  })
'''

#### Promise.nodeify(fn)

_Non Standard_

The twin to 'denodeify' is useful when you want to export an API that can be used by people who haven't learnt about the brilliance
 of promises yet.

'''javascript
module.exports = Promise.nodeify(awesomeAPI)
...
```

#### <a name="apidoc.element.promise.race"></a>[function <span class="apidocSignatureSpan">promise.</span>race (values)](#apidoc.element.promise.race)
- description and source-code
```javascript
race = function (values) {
  return new Promise(function (resolve, reject) {
    values.forEach(function(value){
      Promise.resolve(value).then(resolve, reject);
    });
  });
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.promise.reject"></a>[function <span class="apidocSignatureSpan">promise.</span>reject (value)](#apidoc.element.promise.reject)
- description and source-code
```javascript
reject = function (value) {
  return new Promise(function (resolve, reject) {
    reject(value);
  });
}
```
- example usage
```shell
...

#### Promise.resolve(value)

(deprecated aliases: 'Promise.from(value)', 'Promise.cast(value)')

Converts values and foreign promises into Promises/A+ promises.  If you pass it a value then it returns a Promise for that value
.  If you pass it something that is close to a promise (such as a jQuery attempt at a promise) it returns a Promise that takes on
 the state of 'value' (rejected or fulfilled).

#### Promise.reject(value)

Returns a rejected promise with the given value.

#### Promise.all(array)

Returns a promise for an array.  If it is called with a single argument that 'Array.isArray' then this returns a promise for a copy
 of that array with any promises replaced by their fulfilled values.  e.g.
...
```

#### <a name="apidoc.element.promise.resolve"></a>[function <span class="apidocSignatureSpan">promise.</span>resolve (value)](#apidoc.element.promise.resolve)
- description and source-code
```javascript
resolve = function (value) {
  if (value instanceof Promise) return value;

  if (value === null) return NULL;
  if (value === undefined) return UNDEFINED;
  if (value === true) return TRUE;
  if (value === false) return FALSE;
  if (value === 0) return ZERO;
  if (value === '') return EMPTYSTRING;

  if (typeof value === 'object' || typeof value === 'function') {
    try {
      var then = value.then;
      if (typeof then === 'function') {
        return new Promise(then.bind(value));
      }
    } catch (ex) {
      return new Promise(function (resolve, reject) {
        reject(ex);
      });
    }
  }
  return valuePromise(value);
}
```
- example usage
```shell
...
 1. 'resolve' should be called with a single argument.  If it is called with a non-promise value then the promise is fulfilled with
 that value.  If it is called with a promise (A) then the returned promise takes on the state of that new promise (A).
 2. 'reject' should be called with a single argument.  The returned promise will be rejected with that argument.

### Static Functions

  These methods are invoked by calling 'Promise.methodName'.

#### Promise.resolve(value)

(deprecated aliases: 'Promise.from(value)', 'Promise.cast(value)')

Converts values and foreign promises into Promises/A+ promises.  If you pass it a value then it returns a Promise for that value
.  If you pass it something that is close to a promise (such as a jQuery attempt at a promise) it returns a Promise that takes on
 the state of 'value' (rejected or fulfilled).

#### Promise.reject(value)
...
```



# <a name="apidoc.module.promise.rejection_tracking"></a>[module promise.rejection_tracking](#apidoc.module.promise.rejection_tracking)

#### <a name="apidoc.element.promise.rejection_tracking.disable"></a>[function <span class="apidocSignatureSpan">promise.rejection_tracking.</span>disable ()](#apidoc.element.promise.rejection_tracking.disable)
- description and source-code
```javascript
function disable() {
  enabled = false;
  Promise._10 = null;
  Promise._97 = null;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.promise.rejection_tracking.enable"></a>[function <span class="apidocSignatureSpan">promise.rejection_tracking.</span>enable (options)](#apidoc.element.promise.rejection_tracking.enable)
- description and source-code
```javascript
function enable(options) {
  options = options || {};
  if (enabled) disable();
  enabled = true;
  var id = 0;
  var displayId = 0;
  var rejections = {};
  Promise._10 = function (promise) {
    if (
      promise._81 === 2 && // IS REJECTED
      rejections[promise._72]
    ) {
      if (rejections[promise._72].logged) {
        onHandled(promise._72);
      } else {
        clearTimeout(rejections[promise._72].timeout);
      }
      delete rejections[promise._72];
    }
  };
  Promise._97 = function (promise, err) {
    if (promise._45 === 0) { // not yet handled
      promise._72 = id++;
      rejections[promise._72] = {
        displayId: null,
        error: err,
        timeout: setTimeout(
          onUnhandled.bind(null, promise._72),
          // For reference errors and type errors, this almost always
          // means the programmer made a mistake, so log them after just
          // 100ms
          // otherwise, wait 2 seconds to see if they get handled
          matchWhitelist(err, DEFAULT_WHITELIST)
            ? 100
            : 2000
        ),
        logged: false
      };
    }
  };
  function onUnhandled(id) {
    if (
      options.allRejections ||
      matchWhitelist(
        rejections[id].error,
        options.whitelist || DEFAULT_WHITELIST
      )
    ) {
      rejections[id].displayId = displayId++;
      if (options.onUnhandled) {
        rejections[id].logged = true;
        options.onUnhandled(
          rejections[id].displayId,
          rejections[id].error
        );
      } else {
        rejections[id].logged = true;
        logError(
          rejections[id].displayId,
          rejections[id].error
        );
      }
    }
  }
  function onHandled(id) {
    if (rejections[id].logged) {
      if (options.onHandled) {
        options.onHandled(rejections[id].displayId, rejections[id].error);
      } else if (!rejections[id].onUnhandled) {
        console.warn(
          'Promise Rejection Handled (id: ' + rejections[id].displayId + '):'
        );
        console.warn(
          '  This means you can ignore any previous messages of the form "Possible Unhandled Promise Rejection" with id ' +
          rejections[id].displayId + '.'
        );
      }
    }
  }
}
```
- example usage
```shell
...
## Unhandled Rejections

By default, promises silence any unhandled rejections.

You can enable logging of unhandled ReferenceErrors and TypeErrors via:

'''js
require('promise/lib/rejection-tracking').enable();
'''

Due to the performance cost, you should only do this during development.

You can enable logging of all unhandled rejections if you need to debug an exception you think is being swallowed by promises:

'''js
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
