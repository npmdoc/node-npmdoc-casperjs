# api documentation for  [casperjs (v1.1.3)](http://casperjs.org)  [![npm package](https://img.shields.io/npm/v/npmdoc-casperjs.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-casperjs) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-casperjs.svg)](https://travis-ci.org/npmdoc/node-npmdoc-casperjs)
#### A navigation scripting & testing utility for PhantomJS and SlimerJS

[![NPM](https://nodei.co/npm/casperjs.png?downloads=true)](https://www.npmjs.com/package/casperjs)

[![apidoc](https://npmdoc.github.io/node-npmdoc-casperjs/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-casperjs_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-casperjs/build..beta..travis-ci.org/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-casperjs/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-casperjs/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "CasperJS Organization",
        "url": "https://casperjs.org/"
    },
    "bin": {
        "casperjs": "./bin/casperjs"
    },
    "bugs": {
        "url": "https://github.com/casperjs/casperjs/issues"
    },
    "dependencies": {},
    "description": "A navigation scripting & testing utility for PhantomJS and SlimerJS",
    "devDependencies": {},
    "directories": {},
    "dist": {
        "shasum": "9653de731f8aa44d0915a69ba2233164bb2eaf94",
        "tarball": "https://registry.npmjs.org/casperjs/-/casperjs-1.1.3.tgz"
    },
    "gitHead": "f231707feb8f4acf5fc6462e93a38b23b1e1e374",
    "homepage": "http://casperjs.org",
    "keywords": [
        "phantomjs",
        "slimerjs",
        "test",
        "testing",
        "scraping"
    ],
    "licenses": [
        {
            "type": "MIT",
            "url": "http://www.opensource.org/licenses/mit-license.php"
        }
    ],
    "maintainers": [
        {
            "name": "istr",
            "email": "npm@ingostruck.de"
        },
        {
            "name": "mickaelandrieu",
            "email": "andrieu.travail@gmail.com"
        },
        {
            "name": "n1k0",
            "email": "nicolas@perriault.net"
        }
    ],
    "name": "casperjs",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git://github.com/casperjs/casperjs.git"
    },
    "scripts": {},
    "version": "1.1.3"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module casperjs](#apidoc.module.casperjs)
1.  object <span class="apidocSignatureSpan">casperjs.</span>events
1.  object <span class="apidocSignatureSpan">casperjs.</span>querystring

#### [module casperjs.events](#apidoc.module.casperjs.events)
1.  [function <span class="apidocSignatureSpan">casperjs.events.</span>EventEmitter ()](#apidoc.element.casperjs.events.EventEmitter)

#### [module casperjs.querystring](#apidoc.module.casperjs.querystring)
1.  [function <span class="apidocSignatureSpan">casperjs.querystring.</span>decode (qs, sep, eq, options)](#apidoc.element.casperjs.querystring.decode)
1.  [function <span class="apidocSignatureSpan">casperjs.querystring.</span>encode (obj, sep, eq, name)](#apidoc.element.casperjs.querystring.encode)
1.  [function <span class="apidocSignatureSpan">casperjs.querystring.</span>escape (str)](#apidoc.element.casperjs.querystring.escape)
1.  [function <span class="apidocSignatureSpan">casperjs.querystring.</span>parse (qs, sep, eq, options)](#apidoc.element.casperjs.querystring.parse)
1.  [function <span class="apidocSignatureSpan">casperjs.querystring.</span>stringify (obj, sep, eq, name)](#apidoc.element.casperjs.querystring.stringify)
1.  [function <span class="apidocSignatureSpan">casperjs.querystring.</span>unescape (s, decodeSpaces)](#apidoc.element.casperjs.querystring.unescape)
1.  [function <span class="apidocSignatureSpan">casperjs.querystring.</span>unescapeBuffer (s, decodeSpaces)](#apidoc.element.casperjs.querystring.unescapeBuffer)



# <a name="apidoc.module.casperjs"></a>[module casperjs](#apidoc.module.casperjs)



# <a name="apidoc.module.casperjs.events"></a>[module casperjs.events](#apidoc.module.casperjs.events)

#### <a name="apidoc.element.casperjs.events.EventEmitter"></a>[function <span class="apidocSignatureSpan">casperjs.events.</span>EventEmitter ()](#apidoc.element.casperjs.events.EventEmitter)
- description and source-code
```javascript
function EventEmitter() {
  this._filters = {};
}
```
- example usage
```shell
n/a
```



# <a name="apidoc.module.casperjs.querystring"></a>[module casperjs.querystring](#apidoc.module.casperjs.querystring)

#### <a name="apidoc.element.casperjs.querystring.decode"></a>[function <span class="apidocSignatureSpan">casperjs.querystring.</span>decode (qs, sep, eq, options)](#apidoc.element.casperjs.querystring.decode)
- description and source-code
```javascript
decode = function (qs, sep, eq, options) {
  sep = sep || '&';
  eq = eq || '=';
  var obj = {};

  if (typeof qs !== 'string' || qs.length === 0) {
    return obj;
  }

  var regexp = /\+/g;
  qs = qs.split(sep);

  var maxKeys = 1000;
  if (options && typeof options.maxKeys === 'number') {
    maxKeys = options.maxKeys;
  }

  var len = qs.length;
  // maxKeys <= 0 means that we should not limit keys count
  if (maxKeys > 0 && len > maxKeys) {
    len = maxKeys;
  }

  for (var i = 0; i < len; ++i) {
    var x = qs[i].replace(regexp, '%20'),
        idx = x.indexOf(eq),
        kstr, vstr, k, v;

    if (idx >= 0) {
      kstr = x.substr(0, idx);
      vstr = x.substr(idx + 1);
    } else {
      kstr = x;
      vstr = '';
    }

    try {
      k = decodeURIComponent(kstr);
      v = decodeURIComponent(vstr);
    } catch (e) {
      k = QueryString.unescape(kstr, true);
      v = QueryString.unescape(vstr, true);
    }

    if (!hasOwnProperty(obj, k)) {
      obj[k] = v;
    } else if (Array.isArray(obj[k])) {
      obj[k].push(v);
    } else {
      obj[k] = [obj[k], v];
    }
  }

  return obj;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.casperjs.querystring.encode"></a>[function <span class="apidocSignatureSpan">casperjs.querystring.</span>encode (obj, sep, eq, name)](#apidoc.element.casperjs.querystring.encode)
- description and source-code
```javascript
encode = function (obj, sep, eq, name) {
  sep = sep || '&';
  eq = eq || '=';
  if (obj === null) {
    obj = undefined;
  }

  if (typeof obj === 'object') {
    return Object.keys(obj).map(function(k) {
      var ks = QueryString.escape(stringifyPrimitive(k)) + eq;
      if (Array.isArray(obj[k])) {
        return obj[k].map(function(v) {
          return ks + QueryString.escape(stringifyPrimitive(v));
        }).join(sep);
      } else {
        return ks + QueryString.escape(stringifyPrimitive(obj[k]));
      }
    }).join(sep);

  }

  if (!name) return '';
  return QueryString.escape(stringifyPrimitive(name)) + eq +
         QueryString.escape(stringifyPrimitive(obj));
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.casperjs.querystring.escape"></a>[function <span class="apidocSignatureSpan">casperjs.querystring.</span>escape (str)](#apidoc.element.casperjs.querystring.escape)
- description and source-code
```javascript
escape = function (str) {
  return encodeURIComponent(str);
}
```
- example usage
```shell
...
eq = eq || '=';
if (obj === null) {
  obj = undefined;
}

if (typeof obj === 'object') {
  return Object.keys(obj).map(function(k) {
    var ks = QueryString.escape(stringifyPrimitive(k)) + eq;
    if (Array.isArray(obj[k])) {
      return obj[k].map(function(v) {
        return ks + QueryString.escape(stringifyPrimitive(v));
      }).join(sep);
    } else {
      return ks + QueryString.escape(stringifyPrimitive(obj[k]));
    }
...
```

#### <a name="apidoc.element.casperjs.querystring.parse"></a>[function <span class="apidocSignatureSpan">casperjs.querystring.</span>parse (qs, sep, eq, options)](#apidoc.element.casperjs.querystring.parse)
- description and source-code
```javascript
parse = function (qs, sep, eq, options) {
  sep = sep || '&';
  eq = eq || '=';
  var obj = {};

  if (typeof qs !== 'string' || qs.length === 0) {
    return obj;
  }

  var regexp = /\+/g;
  qs = qs.split(sep);

  var maxKeys = 1000;
  if (options && typeof options.maxKeys === 'number') {
    maxKeys = options.maxKeys;
  }

  var len = qs.length;
  // maxKeys <= 0 means that we should not limit keys count
  if (maxKeys > 0 && len > maxKeys) {
    len = maxKeys;
  }

  for (var i = 0; i < len; ++i) {
    var x = qs[i].replace(regexp, '%20'),
        idx = x.indexOf(eq),
        kstr, vstr, k, v;

    if (idx >= 0) {
      kstr = x.substr(0, idx);
      vstr = x.substr(idx + 1);
    } else {
      kstr = x;
      vstr = '';
    }

    try {
      k = decodeURIComponent(kstr);
      v = decodeURIComponent(vstr);
    } catch (e) {
      k = QueryString.unescape(kstr, true);
      v = QueryString.unescape(vstr, true);
    }

    if (!hasOwnProperty(obj, k)) {
      obj[k] = v;
    } else if (Array.isArray(obj[k])) {
      obj[k].push(v);
    } else {
      obj[k] = [obj[k], v];
    }
  }

  return obj;
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.casperjs.querystring.stringify"></a>[function <span class="apidocSignatureSpan">casperjs.querystring.</span>stringify (obj, sep, eq, name)](#apidoc.element.casperjs.querystring.stringify)
- description and source-code
```javascript
stringify = function (obj, sep, eq, name) {
  sep = sep || '&';
  eq = eq || '=';
  if (obj === null) {
    obj = undefined;
  }

  if (typeof obj === 'object') {
    return Object.keys(obj).map(function(k) {
      var ks = QueryString.escape(stringifyPrimitive(k)) + eq;
      if (Array.isArray(obj[k])) {
        return obj[k].map(function(v) {
          return ks + QueryString.escape(stringifyPrimitive(v));
        }).join(sep);
      } else {
        return ks + QueryString.escape(stringifyPrimitive(obj[k]));
      }
    }).join(sep);

  }

  if (!name) return '';
  return QueryString.escape(stringifyPrimitive(name)) + eq +
         QueryString.escape(stringifyPrimitive(obj));
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.casperjs.querystring.unescape"></a>[function <span class="apidocSignatureSpan">casperjs.querystring.</span>unescape (s, decodeSpaces)](#apidoc.element.casperjs.querystring.unescape)
- description and source-code
```javascript
unescape = function (s, decodeSpaces) {
  return QueryString.unescapeBuffer(s, decodeSpaces).toString();
}
```
- example usage
```shell
...
  vstr = '';
}

try {
  k = decodeURIComponent(kstr);
  v = decodeURIComponent(vstr);
} catch (e) {
  k = QueryString.unescape(kstr, true);
  v = QueryString.unescape(vstr, true);
}

if (!hasOwnProperty(obj, k)) {
  obj[k] = v;
} else if (Array.isArray(obj[k])) {
  obj[k].push(v);
...
```

#### <a name="apidoc.element.casperjs.querystring.unescapeBuffer"></a>[function <span class="apidocSignatureSpan">casperjs.querystring.</span>unescapeBuffer (s, decodeSpaces)](#apidoc.element.casperjs.querystring.unescapeBuffer)
- description and source-code
```javascript
unescapeBuffer = function (s, decodeSpaces) {
  var out = new Buffer(s.length);
  var state = 'CHAR'; // states: CHAR, HEX0, HEX1
  var n, m, hexchar;

  for (var inIndex = 0, outIndex = 0; inIndex <= s.length; inIndex++) {
    var c = s.charCodeAt(inIndex);
    switch (state) {
      case 'CHAR':
        switch (c) {
          case charCode('%'):
            n = 0;
            m = 0;
            state = 'HEX0';
            break;
          case charCode('+'):
            if (decodeSpaces) c = charCode(' ');
            // pass thru
          default:
            out[outIndex++] = c;
            break;
        }
        break;

      case 'HEX0':
        state = 'HEX1';
        hexchar = c;
        if (charCode('0') <= c && c <= charCode('9')) {
          n = c - charCode('0');
        } else if (charCode('a') <= c && c <= charCode('f')) {
          n = c - charCode('a') + 10;
        } else if (charCode('A') <= c && c <= charCode('F')) {
          n = c - charCode('A') + 10;
        } else {
          out[outIndex++] = charCode('%');
          out[outIndex++] = c;
          state = 'CHAR';
          break;
        }
        break;

      case 'HEX1':
        state = 'CHAR';
        if (charCode('0') <= c && c <= charCode('9')) {
          m = c - charCode('0');
        } else if (charCode('a') <= c && c <= charCode('f')) {
          m = c - charCode('a') + 10;
        } else if (charCode('A') <= c && c <= charCode('F')) {
          m = c - charCode('A') + 10;
        } else {
          out[outIndex++] = charCode('%');
          out[outIndex++] = hexchar;
          out[outIndex++] = c;
          break;
        }
        out[outIndex++] = 16 * n + m;
        break;
    }
  }

  // TODO support returning arbitrary buffers.

  return out.slice(0, outIndex - 1);
}
```
- example usage
```shell
...
  // TODO support returning arbitrary buffers.

  return out.slice(0, outIndex - 1);
};


QueryString.unescape = function(s, decodeSpaces) {
  return QueryString.unescapeBuffer(s, decodeSpaces).toString();
};


QueryString.escape = function(str) {
  return encodeURIComponent(str);
};
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
