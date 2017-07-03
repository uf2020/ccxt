# Overview

```diff
- the ccxt documentation is under heavy development right now
```

The ccxt library is a collection of available crypto exchange markets or market classes. Each *market* implements the public and private API for a particular crypto exchange. All markets are derived from the base Market class and share a set of common methods. To access a particular market from ccxt library you need to create an instance of corresponding market class. Supported markets are updated frequently and new markets are added regularly.

The ccxt library implements full public and private HTTP REST APIs for all exchanges. WebSocket and FIX implementations in JavaScript, PHP, Python and other languages coming soon.

- [Exchange Markets](#exchange-markets)
- [Products](#products)
- [API Methods / Endpoints](#endpoints)
- [Market Data](#market-data)
- [Trading](#trading)

# Exchange Markets

Below is a list of currently supported cryptocurrency exchanges:

|                                                                                                                    | id          | name                                         | ver | doc                                                            | countries                               |
|--------------------------------------------------------------------------------------------------------------------|-------------|----------------------------------------------|:---:|:--------------------------------------------------------------:|-----------------------------------------|
|![_1broker](https://user-images.githubusercontent.com/1294454/27766021-420bd9fc-5ecb-11e7-8ed6-56d0081efed2.jpg)    | _1broker    | [1Broker](https://1broker.com)               | 2   | [API](https://1broker.com/?c=en/content/api-documentation)     | US                                      |
|![_1btcxe](https://user-images.githubusercontent.com/1294454/27766049-2b294408-5ecc-11e7-85cc-adaff013dc1a.jpg)     | _1btcxe     | [1BTCXE](https://1btcxe.com)                 | *   | [API](https://1btcxe.com/api-docs.php)                         | Panama                                  |
|![anxpro](https://user-images.githubusercontent.com/1294454/27765983-fd8595da-5ec9-11e7-82e3-adb3ab8c2612.jpg)      | anxpro      | [ANXPro](https://anxpro.com)                 | 2   | [API](https://anxpro.com/pages/api)                            | Japan, Singapore, Hong Kong, New Zealand|
|![bit2c](https://user-images.githubusercontent.com/1294454/27766119-3593220e-5ece-11e7-8b3a-5a041f6bcc3f.jpg)       | bit2c       | [Bit2C](https://www.bit2c.co.il)             | *   | [API](https://www.bit2c.co.il/home/api)                        | Israel                                  |
|![bitbay](https://user-images.githubusercontent.com/1294454/27766132-978a7bd8-5ece-11e7-9540-bc96d1e9bbb8.jpg)      | bitbay      | [BitBay](https://bitbay.net)                 | *   | [API](https://bitbay.net/public-api)                           | Poland, EU                              |
|![bitcoincoid](https://user-images.githubusercontent.com/1294454/27766138-043c7786-5ecf-11e7-882b-809c14f38b53.jpg) | bitcoincoid | [Bitcoin.co.id](https://www.bitcoin.co.id)   | *   | [API](https://vip.bitcoin.co.id/trade_api)                     | Indonesia                               |
|![bitfinex](https://user-images.githubusercontent.com/1294454/27766244-e328a50c-5ed2-11e7-947b-041416579bb3.jpg)    | bitfinex    | [Bitfinex](https://www.bitfinex.com)         | 1   | [API](https://bitfinex.readme.io/v1/docs)                      | US                                      |
|![bitlish](https://user-images.githubusercontent.com/1294454/27766275-dcfc6c30-5ed3-11e7-839d-00a846385d0b.jpg)     | bitlish     | [bitlish](https://bitlish.com)               | 1   | [API](https://bitlish.com/api)                                 | UK, EU, Russia                          |
|![bitmarket](https://user-images.githubusercontent.com/1294454/27767256-a8555200-5ef9-11e7-96fd-469a65e2b0bd.jpg)   | bitmarket   | [BitMarket](https://www.bitmarket.pl)        | *   | [API](https://www.bitmarket.net/docs.php?file=api_public.html) | Poland, EU                              |
|![bitmex](https://user-images.githubusercontent.com/1294454/27766319-f653c6e6-5ed4-11e7-933d-f0bc3699ae8f.jpg)      | bitmex      | [BitMEX](https://www.bitmex.com)             | 1   | [API](https://www.bitmex.com/app/apiOverview)                  | Seychelles                              |
|![bitso](https://user-images.githubusercontent.com/1294454/27766335-715ce7aa-5ed5-11e7-88a8-173a27bb30fe.jpg)       | bitso       | [Bitso](https://bitso.com)                   | 3   | [API](https://bitso.com/api_info)                              | Mexico                                  |
|![bittrex](https://user-images.githubusercontent.com/1294454/27766352-cf0b3c26-5ed5-11e7-82b7-f3826b7a97d8.jpg)     | bittrex     | [Bittrex](https://bittrex.com)               | 1.1 | [API](https://bittrex.com/Home/Api)                            | US                                      |
|![btcchina](https://user-images.githubusercontent.com/1294454/27766368-465b3286-5ed6-11e7-9a11-0f6467e1d82b.jpg)    | btcchina    | [BTCChina](https://www.btcchina.com)         | 1   | [API](https://www.btcchina.com/apidocs)                        | China                                   |
|![btcx](https://user-images.githubusercontent.com/1294454/27766385-9fdcc98c-5ed6-11e7-8f14-66d5e5cd47e6.jpg)        | btcx        | [BTCX](https://btc-x.is)                     | 1   | [API](https://btc-x.is/custom/api-document.html)               | Iceland, US, EU                         |
|![bxinth](https://user-images.githubusercontent.com/1294454/27766412-567b1eb4-5ed7-11e7-94a8-ff6a3884f6c5.jpg)      | bxinth      | [BX.in.th](https://bx.in.th)                 | *   | [API](https://bx.in.th/info/api)                               | Thailand                                |
|![ccex](https://user-images.githubusercontent.com/1294454/27766433-16881f90-5ed8-11e7-92f8-3d92cc747a6c.jpg)        | ccex        | [C-CEX](https://c-cex.com)                   | *   | [API](https://c-cex.com/?id=api)                               | Germany, EU                             |
|![cex](https://user-images.githubusercontent.com/1294454/27766442-8ddc33b0-5ed8-11e7-8b98-f786aef0f3c9.jpg)         | cex         | [CEX.IO](https://cex.io)                     | *   | [API](https://cex.io/cex-api)                                  | UK, EU, Cyprus, Russia                  |
|![coincheck](https://user-images.githubusercontent.com/1294454/27766464-3b5c3c74-5ed9-11e7-840e-31b32968e1da.jpg)   | coincheck   | [coincheck](https://coincheck.com)           | *   | [API](https://coincheck.com/documents/exchange/api)            | Japan, Indonesia                        |
|![coinsecure](https://user-images.githubusercontent.com/1294454/27766472-9cbd200a-5ed9-11e7-9551-2267ad7bac08.jpg)  | coinsecure  | [Coinsecure](https://coinsecure.in)          | 1   | [API](https://api.coinsecure.in)                               | India                                   |
|![exmo](https://user-images.githubusercontent.com/1294454/27766491-1b0ea956-5eda-11e7-9225-40d67b481b8d.jpg)        | exmo        | [EXMO](https://exmo.me)                      | 1   | [API](https://exmo.me/ru/api_doc)                              | Spain, Russia                           |
|![fybse](https://user-images.githubusercontent.com/1294454/27766512-31019772-5edb-11e7-8241-2e675e6797f1.jpg)       | fybse       | [FYB-SE](https://www.fybse.se)               | *   | [API](http://docs.fyb.apiary.io)                               | Sweden                                  |
|![fybsg](https://user-images.githubusercontent.com/1294454/27766513-3364d56a-5edb-11e7-9e6b-d5898bb89c81.jpg)       | fybsg       | [FYB-SG](https://www.fybsg.com)              | *   | [API](http://docs.fyb.apiary.io)                               | Singapore                               |
|![gdax](https://user-images.githubusercontent.com/1294454/27766527-b1be41c6-5edb-11e7-95f6-5b496c469e2c.jpg)        | gdax        | [GDAX](https://www.gdax.com)                 | *   | [API](https://docs.gdax.com)                                   | US                                      |
|![hitbtc](https://user-images.githubusercontent.com/1294454/27766555-8eaec20e-5edc-11e7-9c5b-6dc69fc42f5e.jpg)      | hitbtc      | [HitBTC](https://hitbtc.com)                 | 1   | [API](https://hitbtc.com/api)                                  | Hong Kong                               |
|![huobi](https://user-images.githubusercontent.com/1294454/27766569-15aa7b9a-5edd-11e7-9e7f-44791f4ee49c.jpg)       | huobi       | [Huobi](https://www.huobi.com)               | 3   | [API](https://github.com/huobiapi/API_Docs_en/wiki)            | China                                   |
|![jubi](https://user-images.githubusercontent.com/1294454/27766581-9d397d9a-5edd-11e7-8fb9-5d8236c0e692.jpg)        | jubi        | [jubi.com](https://www.jubi.com)             | 1   | [API](https://www.jubi.com/help/api.html)                      | China                                   |
|![kraken](https://user-images.githubusercontent.com/1294454/27766599-22709304-5ede-11e7-9de1-9f33732e1509.jpg)      | kraken      | [Kraken](https://www.kraken.com)             | 0   | [API](https://www.kraken.com/en-us/help/api)                   | US                                      |
|![luno](https://user-images.githubusercontent.com/1294454/27766607-8c1a69d8-5ede-11e7-930c-540b5eb9be24.jpg)        | luno        | [luno](https://www.luno.com)                 | 1   | [API](https://npmjs.org/package/bitx)                          | UK, Singapore, South Africa             |
|![okcoinusd](https://user-images.githubusercontent.com/1294454/27766791-89ffb502-5ee5-11e7-8a5b-c5950b68ac65.jpg)   | okcoinusd   | [OKCoin USD](https://www.okcoin.com)         | 1   | [API](https://www.okcoin.com/rest_getStarted.html)             | China, US                               |
|![okcoincny](https://user-images.githubusercontent.com/1294454/27766792-8be9157a-5ee5-11e7-926c-6d69b8d3378d.jpg)   | okcoincny   | [OKCoin CNY](https://www.okcoin.cn)          | 1   | [API](https://www.okcoin.cn/rest_getStarted.html)              | China                                   |
|![poloniex](https://user-images.githubusercontent.com/1294454/27766817-e9456312-5ee6-11e7-9b3c-b628ca5626a5.jpg)    | poloniex    | [Poloniex](https://poloniex.com)             | *   | [API](https://poloniex.com/support/api/)                       | US                                      |
|![quadrigacx](https://user-images.githubusercontent.com/1294454/27766825-98a6d0de-5ee7-11e7-9fa4-38e11a2c6f52.jpg)  | quadrigacx  | [QuadrigaCX](https://www.quadrigacx.com)     | 2   | [API](https://www.quadrigacx.com/api_info)                     | Canada                                  |
|![quoine](https://user-images.githubusercontent.com/1294454/27766844-9615a4e8-5ee8-11e7-8814-fcd004db8cdd.jpg)      | quoine      | [QUOINE](https://www.quoine.com)             | 2   | [API](https://developers.quoine.com)                           | Japan, Singapore, Vietnam               |
|![therock](https://user-images.githubusercontent.com/1294454/27766869-75057fa2-5ee9-11e7-9a6f-13e641fa4707.jpg)     | therock     | [TheRockTrading](https://therocktrading.com) | 1   | [API](https://api.therocktrading.com/doc/)                     | Malta                                   |
|![vaultoro](https://user-images.githubusercontent.com/1294454/27766880-f205e870-5ee9-11e7-8fe2-0d5b15880752.jpg)    | vaultoro    | [Vaultoro](https://www.vaultoro.com)         | 1   | [API](https://api.vaultoro.com)                                | Switzerland                             |
|![virwox](https://user-images.githubusercontent.com/1294454/27766894-6da9d360-5eea-11e7-90aa-41f2711b7405.jpg)      | virwox      | [VirWoX](https://www.virwox.com)             | *   | [API](https://www.virwox.com/developers.php)                   | Austria                                 |
|![yobit](https://user-images.githubusercontent.com/1294454/27766910-cdcbfdae-5eea-11e7-9859-03fea873272d.jpg)       | yobit       | [YoBit](https://www.yobit.net)               | 3   | [API](https://www.yobit.net/en/api/)                           | Russia                                  |
|![zaif](https://user-images.githubusercontent.com/1294454/27766927-39ca2ada-5eeb-11e7-972f-1b4199518ca6.jpg)        | zaif        | [Zaif](https://zaif.jp)                      | 1   | [API](https://corp.zaif.jp/api-docs)                           | Japan                                   |

## Instantiation

To connect to an exchange market and start trading you need to instantiate a market class instance from ccxt library. A market can be instantiated like so:

```JavaScript
// JavaScript
const ccxt = require ('ccxt')
let market = new ccxt.kraken () // default id
let kraken1 = new ccxt.kraken ({ id: 'kraken1' })
let kraken2 = new ccxt.kraken ({ id: 'kraken2' })
```

```Python
# Python
market = ccxt.okcoinusd () # default id
okcoin1 = ccxt.okcoinusd ({ 'id': 'okcoin1' })
okcoin2 = ccxt.okcoinusd ({ 'id': 'okcoin2' })
```

```PHP
// PHP
date_default_timezone_set ('UTC');
include 'ccxt.php';
$market = new \ccxt\bitfinex (); // default id
$bitfinex1 = new \ccxt\bitfinex (array ('id' => 'bitfinex1'));
$bitfinex2 = new \ccxt\bitfinex (array ('id' => 'bitfinex2'));
```

Note, that ccxt library in PHP uses builtin UTC/GMT time functions, therefore you are required to set date.timezone in your php.ini or call [date_default_timezone_set](http://php.net/manual/en/function.date-default-timezone-set.php)() function before using the PHP version of the library. The recommended timezone setting is `"UTC"`.

## Market Structure

Every market has a set of properties and methods most of which can be overridden upon construction (with JavaScript) or by subclassing (with Python and PHP). Among common market members are:

- `market.id` / `market['id']` / `$market->id`.
Each market has a default id. The id is not used for anything, it's a string literal for user-land market instance identification purposes. You can have multiple links to the same exchange market and differentiate them by ids. Default ids are all lowercase and correspond to market names.

- `market.name / market['name'] / $market->name`: This is a string literal containing the human-readable market name.

- `market.countries / market['countries'] / $market->countries`: A string literal or an array of string literals of 2-symbol ISO country codes, where the exchange is operating from.

- `market.urls['name'] / market['urls']['api'] / $market->urls['api']`: The single string literal base URL for API calls or an associative array of separate URLs for private and public APIs.

- `market.urls['www'] / market['urls']['www'] / $market->urls['www']`: The main HTTP website URL.

- `market.urls['doc'] / market['urls']['doc'] / $market->urls['doc']`: A single string URL link to original documentation for exchange API on their website or an array of links to docs.

- `market.version / market['version'] / $market->version`: A string literal containing version identifier for current exchange market API. The version is often used in constructing the API URL. Do not override it unless you are implementing your own new crypto market class.

- `market.api / market['api'] / $market->api`: An associative array containing a definition of all API endpoints exposed by a crypto exchange. The API definition is used by ccxt to automatically construct callable instance methods for each available endpoint.

- `market.timeout / market['timeout'] / $market->timeout`: A timeout for a request-response roundtrip (default timeout is 10 seconds).

- `market.rateLimit / market['rateLimit'] / $market->rateLimit`: A request rate limit in milliseconds. Specifies the required minimal delay between two consequent HTTP requests to the same market. This parameter is not used for now (reserved for future).

- `market.verbose / market['verbose'] / $market->verbose`: A boolean flag indicating whether to log HTTP requests to stdout (verbose flag is false by default).

- `market.products / market['products'] / $market->products`: An associative array of products indexed by trading pair or symbol. Market products should be loaded prior to accessing this property. Products are unavailable until you call the `loadProduct() / load_products()` method on a market instance.

## Rate Limit

Exchange markets usually impose what is called a *rate limit*. Exchanges will remember and track your user credentials and your IP address and will not allow you to query the API too frequently. They balance their load and control traffic congestion to protect API servers from (D)DoS and misuse.

Most markets allow **up to 1 or 2 requests per second**. Markets may temporarily restrict your access to their exchange API or ban you for some period of time if you are too aggressive with your requests.

```
UNDER CONSTRUCTION
```

## DDoS Protection By Cloudflare

Some markets are [DDoS](https://en.wikipedia.org/wiki/Denial-of-service_attack)-protected by [Cloudflare](https://www.cloudflare.com). Your IP can get temporarily blocked during periods of high load. Sometimes they even restrict whole countries and regions. In that case their servers usually return a page that states a HTTP 40x error or runs an AJAX test of your browser / captcha test and delays the reload of the page for several seconds. Then your browser/fingerprint is granted access temporarily and gets added to a whitelist or receives a HTTP cookie for further use. 

If you encounter Cloudflare DDOS protection errors and cannot reach a particular exchange market then try later or ask the exchange support to add you to a whitelist. 

```
UNDER CONSTRUCTION
```

# Products

Each market is a place for trading some kinds of valuables. Sometimes they are called with various different terms like instruments, symbols, trading pairs, currencies, tokens, stocks, commodities, contracts, etc, but they all mean the same – a trading pair, a symbol, a financial instrument or some kind of *product*. 

In terms of the ccxt library, every market trades products within itself. The set of products differs from market to market opening possibilities for cross-market and cross-product arbitrage. A product is usually a pair of traded crypto and/or fiat currencies. 

Some markets and exchange services offer trading various derivatives (like future contracts and options) and also have [dark pools](https://en.wikipedia.org/wiki/Dark_pool), [OTC](https://en.wikipedia.org/wiki/Over-the-counter_(finance)) (over-the-counter deals), merchant APIs and much more.

## Product Structure

Each product is an associative array with the following keys:
- `product['id']`. The string or numeric ID of the product or trade instrument within the market. Product ids are used inside markets internally to identify products and trading pairs during the request/response process.
- `product['symbol']`. An uppercase string code representation of a particular trading pair or instrument. This is usually written as `BaseCurrency/QuoteCurrency` with a slash as in `BTC/USD`, `LTC/CNY` or `ETH/EUR`, etc. Product symbols are used to reference products within the ccxt library.
- `product['base']`. An uppercase string code of base fiat or crypto currency.
- `product['quote']`. An uppercase string code of quoted fiat or crypto currency.
- `product['info']`. An associative array of non-common market properties, including fees, rates, limits and other general product information. The internal info array is different for each particular market product, its contents depend on the exchange market.

## Loading Products

In most cases you are required to load the list of products and trading symbols for a particular market prior to accessing other market API methods. In order to load products call the `loadProducts()` / `load_products()` method on a market instance. It returns an associative array of products indexed by trading symbol.

```JavaScript
// JavaScript
let kraken = new ccxt.kraken ()
let products = await kraken.load_products ()
console.log (kraken.id, products)

```

```Python
# Python
okcoin = ccxt.okcoinusd ()
products = okcoin.load_products ()
symbols = products.keys ()
print (okcoin.id, products)
print (okcoin.id, symbols)
```

```PHP
// PHP
$huobi = new \ccxt\huobi ();
$products = $huobi.load_products ();
$symbols = array_keys ($products);
var_dump ($huobi->id, $products);
var_dump ($huobi->id, $symbols);
```

## Product Ids And Symbols

Product ids are used during the REST request-response process to reference trading pairs withing markets. Because a product id for a  traded pair of valuables differs from market to market, product ids are unique per exchange and cannot be used across markets. For example, the BTC/USD pair/product may have different ids on various popular markets, like btcusd, BTCUSD, XBTUSD, btc/usd, 137 (number id), BTC/USD, Btc/Usd, tBTCUSD, XXBTZUSD. You don't need to remember or use product ids, they are there only for internal HTTP request-response purposes inside market implementations.

The ccxt library abstracts uncommon product ids to symbols, standardized to a common format. Symbols are not the same as product ids. Every product is referenced by a corresponding symbol. Symbols are common across markets which makes them suitable for arbitrage and many other things.

A symbol is an uppercase literal name of a pair of traded currencies with a slash in between. A currency is usually a code of three or four uppercase letters, like BTC, USD, GBP, DOGE, etc. Some markets have exotic currencies with longer names. Examples of a symbol are: BTC/USD, DOGE/LTC, ETH/EUR, DASH/XRP, BTC/CNY, ZEC/XMR, ETH/JPY.

Products are indexed by symbols. The base market class has builtin methods for accessing products by symbols.

```JavaScript
// JavaScript
(async () => {
    console.log (await market.loadProducts ())
    let btcusd1 = market.products['BTC/USD'] // get product structure by symbol
    let btcusd2 = market.product ('BTC/USD') // get product structure by symbol
    let btcusdId = market.productId ('BTC/USD') // get product id by symbol
    let symbols = Object.keys (market.products)
    console.log (market.id, symbols) // print all symbols
})
```

```Python
# Python
print (market.load_products ())
etheur1 = market.products['ETH/EUR'] # get product structure by symbol
etheur2 = market.product ('ETH/EUR') # get product structure by symbol
etheurId = market.product_id ('BTC/USD') # get product id by symbol
symbols = market.products.keys ()
print (market.id, symbols) # print all symbols
```

```PHP
// PHP
$var_dump (market->load_products ());
etheur1 = $market->products['ETH/EUR']; // get product structure by symbol
etheur2 = $market->product ('ETH/EUR'); // get product structure by symbol
etheurId = $market->product_id ('BTC/USD'); // get product id by symbol
$symbols = array_keys ($market->products);
var_dump ($market->id, $symbols); // print all symbols
```

## Product Cache Force Reload

The loadProducts / load_products is also a dirty method with a side effect of saving the array of products on the market instance. You only need to call it once per market. All subsequent calls to the same method will return the locally saved (cached) array of products.

When market products are loaded, you can then access product information any time via the `market.products / market['products'] / $market->products` property. This property contains an associative array of products indexed by symbol. If you need to force reload the list of products after you have them loaded already, pass the reload = true flag to the same method again.

```JavaScript
// JavaScript
(async () => {
    let kraken = new ccxt.kraken ({ verbose: true }) // log HTTP requests
    await kraken.load_products () // request products
    console.log (kraken.id, kraken.products) // output a full list of all loaded products
    console.log (Object.keys (kraken.products)) // output a short list of product symbols
    console.log (kraken.products['BTC/USD']) // output single product details
    await kraken.load_products () // return a locally cached version, no reload
    let reloadedProducts = await kraken.load_products (true) // force HTTP reload = true
    console.log (reloadedProducts['ETH/BTC'])
}) ()
```

```Python
# Python
poloniex = ccxt.poloniex ({ 'verbose': True }) # log HTTP requests
poloniex.load_products () # request products
print (poloniex.id, poloniex.products) # output a full list of all loaded products
print (poloniex.products.keys ()) # output a short list of product symbols
print (poloniex.products['BTC/ETH']) # output single product details
poloniex.load_products () # return a locally cached version, no reload
reloadedProducts = poloniex.load_products (True) # force HTTP reload = True
print (reloadedProducts['ETH/ZEC'])
```

```PHP
// PHP
$bitfinex = new \ccxt\bitfinex (array ('verbose' => true)); // log HTTP requests
$bitfinex.load_products (); // request products
var_dump ($bitfinex->id, $bitfinex->products); // output a full list of all loaded products
var_dump (array_keys ($bitfinex->products)); // output a short list of product symbols
var_dump ($bitfinex->products['XRP/USD']); // output single product details
$bitfinex->load_products (); // return a locally cached version, no reload
$reloadedProducts = $bitfinex->load_products (true); // force HTTP reload = true
var_dump ($bitfinex->products['XRP/BTC']);
```

# API Methods / Endpoints

Each exchange market offers a set of API methods. Each method of the API is called an *endpoint*. Endpoints are HTTP URLs for querying various types of information. All endpoints return JSON in response to client requests. 

Usually, there is an endpoint for getting a list of products from an exchange market, an endpoint for retrieving an order book for a particular product, an endpoint for retrieving trade history, endpoints for placing and cancelling orders, for money deposit and withdrawal, etc... Basically every kind of action you could perform within a particular market has a separate endpoint URL offered by exchange API.

Because the set of methods differs from market to market, the ccxt library implements the following:
- a public and private API for all possible URLs and methods
- a unified API supporting a subset of common methods

The endpoint URLs are predefined in the `market['api'] / $market->api` property for each market. You don't have to override it, unless you are implementing a new market API (at least you should know what you're doing). 

The endpoint definition is a list of all API URLs exposed by a market. This list gets converted to callable instance methods upon market instantiation. Each URL in the API endpoint list gets a corresponding callable method. For example, if a market offers an HTTP GET URL for querying prices like `https://example.com/public/quotes`, it is converted to a method named `example.publicGetQuotes () / $example->publicGetQuotes ()`. This is done automatically for all markets, therefore the ccxt library supports all possible URLs offered by crypto exchanges.

## Public / Private API

API URLs are usually grouped into two sets of methods called a *public API* for market data and a *private API* for trading and account access. These groups of API methods are usually prefixed with a word 'public' or 'private'. Most exchanges have a public and a private API.

A public API is used to access market data. Public APIs usually do not require any authentication whatsoever. Most markets provide market data to public. With the ccxt library anyone can access market data out of the box without having to register with the markets and without setting up account keys and passwords.

Public APIs include the following: 
- instruments/trading pairs
- price feeds (exchange rates)
- order books (L1, L2, L3...)
- trade history (closed orders, transactions, executions)
- tickers (spot / 24h price)
- OHLC(V) for charting
- other public endpoints

For trading with private API you need to obtain API keys from/to exchange markets. It often means registering with exchange markets and creating API keys with your account. Most exchanges require personal info or identification. Some kind of verification may be necessary as well.

If you want to trade you need to register yourself, this library will not create accounts or API keys for you. Some exchange APIs expose interface methods for registering an account from within the code itself, but most of exchanges don't. You have to sign up and create API keys with their websites.

Private APIs allow the following:
- manage personal account info
- query account balances
- trade by making market and limit orders
- create deposit addresses and fund accounts
- request withdrawal of fiat and crypto funds
- query personal open / closed orders
- query positions in margin/leverage trading
- get ledger history
- transfer funds between accounts
- use merchant services

Some exchanges offer the same logic under different names. For example, a public API is also often called *market data*, *basic*, *market*, *mapi*, *api*, *price*, etc... All of them mean a set of methods for accessing data available to public. A private API is also often called *trading*, *trade*, *tapi*, *exchange*, *account*, etc... A few exchanges also expose a merchant API which is often called *merchant*, *ecapi* (for e-commerce).

To get a list of all available methods with a market instance, you can simply do the following:

```
console.log (new ccxt.kraken ())   // JavaScript
print (dir (ccxt.hitbtc ()))        # Python
var_dump (new \ccxt\okcoinusd ()); // PHP
```

In Python and PHP all API methods are synchronous. In JavaScript all methods are asynchronous and return Promises that resolve with a decoded JSON object. Therefore there are two styles for JavaScript code structuring – callbacks and async/await.

```JavaScript
// JavaScript

// callback style
bitfinex.publicGetSymbolsDetails ().then (products => {
    // → nested codeflow
    let productId = products[0]['pair']
    bitfinex.publicGetPubtickerSymbol ({ symbol: productId }).then (ticker => {
        // → nested codeflow
        console.log (bitfinex.id, productId, ticker)
    })
})

// async / await style
(async () => {
    // ↓ linear codeflow
    let pairs = await kraken.publicGetAssetPairs () 
    let productIds = Object.keys (pairs['result'])
    let productId = productIds[0]
    let ticker = await kraken.publicGetTicker ({ pair: productId })
    console.log (kraken.id, productId, ticker)
}) ()
```

## Returned JSON Objects

All public and private API methods return raw decoded JSON objects in response from the exchange markets, as is, untouched. The unified API returns JSON-decoded objects in a common format and structured uniformly across all markets.

## Passing Parameters To API Methods

The set of all possible API endpoints differs from market to market. Most of methods accept a single associative array (or a Python dict) of key-value parameters. The params are passed as follows:

```
bitso.publicGetTicker ({ book: 'eth_mxn' })            // JavaScript
zaif.api_get_ticker_pair ({ 'pair': 'btc_jpy' })        # Python
$luno->public_get_ticker (array ('pair' => 'XBTIDR')); // PHP
```

For a full list of accepted method parameters for each market, please consult [API docs](#exchange-markets).

### API Method Naming Conventions

A market method name is a concatenated string consisting of type (public or private), HTTP method (GET, POST, PUT, DELETE) and endpoint URL path like in the following examples:

| Method Name                  | Base API URL                   | Endpoint URL                   |
|------------------------------|--------------------------------|--------------------------------|
| publicGetIdOrderbook         | https://bitbay.net/API/Public  | {id}/orderbook                 |
| publicGetPairs               | https://bitlish.com/api        | pairs                          |
| publicGetJsonMarketTicker    | https://www.bitmarket.net      | json/{market}/ticker           |
| privateGetUserMargin         | https://bitmex.com             | user/margin                    |
| privatePostTrade             | https://btc-x.is/api           | trade                          |
| tapiCancelOrder              | https://yobit.net              | tapi/CancelOrder               |
| ...                          | ...                            | ...                            |

The ccxt library supports both camelcase notation (preferred in JavaScript) and underscore notation (preferred in Python and PHP), therefore all methods can be called in either notation or coding style in any language. Both of these notations work in JavaScript, Python and PHP:

```
market.methodName ()  // camelcase pseudocode
market.method_name () // underscore pseudocode
```

```
UNDER CONSTRUCTION
```

## Unified API

The unified ccxt API is a subset of methods common among the markets. It currently contains the following methods:

- `fetchProducts ()`: Fetches a list of all available products from a market and returns an abstracted JSON-decoded response, an array of products. Some markets do not have means for obtaining a list of products via their online API, for those the list of products is hardcoded.

- `loadProducts ([reload])`: Loads the list of products indexed by symbol and caches it with the market instance. Returns cached products if loaded already, unless the `reload = true` flag is forced. 

- `fetchOrderBook (symbol)`: Fetch an order book for a particular product trading symbol.

- `fetchTrades (symbol)`: Fetch recent trades for a particular trading symbol.

- `fetchTicker (symbol)`: Fetch latest ticker data by trading symbol.

- `fetchBalance ()`: Fetch Balance.

- `order (symbol, side, amount[, price[, params]])`
- `trade (symbol, side, amount[, price[, params]])`
- `buy (symbol, amount[, price[, params]])`
- `sell (symbol, amount[, price[, params]])`
- `createOrder (symbol, side, amount[, price[, params]])`
- `createBuyOrder (symbol, amount[, price[, params]])`
- `createSellOrder (symbol, amount[, price[, params]])`
- `createLimitOrder (symbol, side, amount, price, params])`
- `createMarketOrder (symbol, side, amount[, params])`
- `createLimitBuyOrder (symbol, amount, price[, params])`
- `createLimitSellOrder (symbol, amount, price[, params])`
- `createMarketBuyOrder (symbol, amount[, params])`
- `createMarketSellOrder (symbol, amount[, params])`
- `cancelOrder (id)`

# Market Data

```
UNDER CONSTRUCTION
```

## Order Books

```
UNDER CONSTRUCTION
```

## Price Tickers

A price ticker contains statistics for a particular product/symbol for some period of time in recent past, usually last 24 hours. The structure of a ticker is as follows:

```
{
    details:   { the original non-modified unparsed reply from exchange market API server },
    timestamp:   int (64-bit Unix Timestamp in milliseconds since Epoch 1 Jan 1970)
    datetime:    ISO8601 datetime string with milliseconds
    high:        float (highest price)
    low:         float (lowest price)
    bid:         float (current bid (buy) price)
    ask:         float (current ask (sell) price)
    vwap:        float (volume weighed average price)
    open:        float (open price),
    first:       float (price of first trade),
    last:        float (price of last trade),
    change:      float (percentage change),
    average:     float (average),
    baseVolume:  float (volume of base currency),
    quoteVolume: float (volume of quote currency),
}
```

Timestamp and datetime are both Universal Time Coordinated (UTC).
To get the ticker data from exchange market call the `market.fetchTicker (productOrSymbol) / market.fetch_ticker (product_or_symbol)`:

```JavaScript
// JavaScript
(async () => {
    console.log (await (market.fetchTicker ('BTC/USD'))) // ticker for BTC/USD
    let symbols = Object.keys (market.products) 
    let random = Math.floor ((Math.random () * symbols.length)) - 1
    console.log (market.fetchTicker (symbols[random])) // ticker for a random symbol
}) ()
```

```Python
# Python
import random
print (market.fetch_ticker ('LTC/ZEC')) # ticker for LTC/ZEC
symbols = market.products.keys ()
print (market.fetch_ticker (random.choice (symbols))) # ticker for a random symbol
```

```PHP
// PHP (don't forget to set your timezone properly!)
var_dump ($market->fetch_ticker ('ETH/CNY')); // ticker for ETH/CNY
$symbols = array_keys ($market->products);
$random = rand () % count ($symbols);
var_dump ($market->fetch_ticker ($symbols[$random])); // ticker for a random symbol
```

```
UNDER CONSTRUCTION
```

## OHLC(V) Candlestick Charts

```
UNDER CONSTRUCTION
```

## Trades, Orders, Executions, Transactions

```
UNDER CONSTRUCTION
```

# Trading

```
UNDER CONSTRUCTION
```

## Overriding The Nonce

The default nonce is a 32-bit Unix Timestamp (seconds since epoch January 1, 1970).

In case you need to reset the nonce it is much easier to create another pair of keys for using with private APIs. In some cases you are unable to create new keys due to lack of permissions or whatever. If that happens you can still override the nonce. 

In Javascript you can override the nonce by providing a `nonce` parameter to the market constructor or by setting it explicitly on a market object:

```JavaScript
// JavaScript
let nonce = 1
// A: nonce redefined in constructor parameters
let kraken1 = new ccxt.kraken ({ nonce: () => nonce++ }) 
// B: nonce redefined explicitly
let kraken2 = new ccxt.kraken ()
kraken2.nonce = function () { return nonce++ } // uses same nonce as kraken1
// C: nonce redefined by calling this.milliseconds
let kraken3 = new ccxt.kraken ({
    nonce: function () { return this.milliseconds () },
})
```

In Python and PHP you can do the same by subclassing and overriding nonce function of a particular market class:

```Python
# Python
class MyKraken (ccxt.kraken):
    n = 1
    def nonce (self):
        return self.n += 1
mykraken = MyKraken ()
```

```PHP
// PHP
class MyOKCoinUSD extends \ccxt\okcoinusd {
    public function __construct ($options = array ()) {
        parent::__construct (array_merge (array ('i' => 1), $options));
    }
    public function nonce () {
        return $this->i++;
    }
}
```

```
UNDER CONSTRUCTION
```