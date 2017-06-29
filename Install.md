The ccxt library is shipped as a single-file (all-in-one module) implementation with minimalistic dependencies and requirements.

The main file is:
- `ccxt.js` in JavaScript ([ccxt for Node.js](http://npmjs.com/package/ccxt) and web browsers)
- `ccxt/__init__.py` in Python (works in both Python 2 and 3)
- `ccxt.php` in PHP

The easiest way to install the ccxt library is to use builtin package managers. 

You can also clone it directly into your project directory from GitHub repository:

```shell
git clone https://github.com/kroitor/ccxt.git
```

An alternative way of installing this library into your code is to copy a single `ccxt.*` file manually into your working directory with language extension appropriate for your environment. 

## Node.js

```shell
npm install ccxt
```

Node version of the ccxt library requires `crypto` and `node-fetch`, both of them are installed automatically by npm.

```JavaScript
var ccxt = require ('ccxt')
console.log (Object.keys (ccxt)) // print all available markets
```

## Python

```shell
pip install ccxt
```

Python version of the ccxt library does not require any additional dependencies and uses builtin modules only.

```Python
import ccxt
print dir (ccxt) # print a list of all available market classes
```

## PHP

```shell
git clone https://github.com/kroitor/ccxt.git
```

The ccxt library in PHP requires common PHP modules:
- cURL
- mbstring (using UTF-8 is highly recommended)
- PCRE
- iconv

To check if you have requires modules enabled in your PHP installation, type `php -m` or execute phpinfo () with `php -r 'phpinfo ();'` in console.

Note, that ccxt library uses builtin UTC/GMT time functions, therefore you are required to set date.timezone in your php.ini or call [date_default_timezone_set](http://php.net/manual/en/function.date-default-timezone-set.php)() function before using the ccxt library in PHP. The recommended timezone setting is `"UTC"`.

```PHP
date_default_timezone_set ('UTC');
include "ccxt.php";
$market = new \cxxt\kraken ();
```

## Web Browsers

The ccxt library can also be used in web browser client-side JavaScript for various purposes. 

```shell
git clone https://github.com/kroitor/ccxt.git
```

The client-side JavaScript version also requires CryptoJS. Download and unpack [CryptoJS](https://code.google.com/archive/p/crypto-js/) into your working directory or clone [CryptoJS from GitHub](https://github.com/sytelus/CryptoJS).

```shell
git clone https://github.com/sytelus/CryptoJS
```

Add links to CryptoJS components and ccxt to your HTML page code:

```HTML
<script src="crypto-js/rollups/sha256.js"></script>
<script src="crypto-js/rollups/hmac-sha256.js"></script>
<script src="crypto-js/rollups/hmac-sha512.js"></script>
<script src="crypto-js/components/enc-base64-min.js"></script>
<script src="crypto-js/components/enc-utf16-min.js"></script>

<script type="text/javascript" src="ccxt.js"></script>
<script type="text/javascript">
    // print all available markets
    document.addEventListener ('DOMContentLoaded', () => console.log (ccxt))
</script>
```

### CORS (Access-Control-Allow-Origin)

CORS is [Cross-Origin Resource Sharing](https://en.wikipedia.org/wiki/Cross-origin_resource_sharing). When accessing a market HTTP REST API from browser with ccxt library you may get a warning or an exception, saying `No 'Access-Control-Allow-Origin' header is present on the requested resource`. That means that the exchange market admins haven't enabled access to their API from arbitrary web browser pages. You can still use the ccxt library from your browser via a CORS-proxy, which is very easy to install.

#### CORS Proxy

```
UNDER CONSTRUCTION
```
