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

| id          | name                                         | docs                                                           | countries                   |
|-------------|----------------------------------------------|----------------------------------------------------------------|-----------------------------|
| _1broker    | [1Broker](https://1broker.com)               | [API](https://1broker.com/?c=en/content/api-documentation)     | US                          |
| _1btcxe     | [1BTCXE](https://1btcxe.com)                 | [API](https://1btcxe.com/api-docs.php)                         | Panama                      |
| bit2c       | [Bit2C](https://www.bit2c.co.il)             | [API](https://www.bit2c.co.il/home/api)                        | Israel                      |
| bitbay      | [BitBay](https://bitbay.net)                 | [API](https://bitbay.net/public-api)                           | Poland, EU                  |
| bitcoincoid | [Bitcoin.co.id](https://www.bitcoin.co.id)   | [API](https://vip.bitcoin.co.id/trade_api)                     | Indonesia                   |
| bitfinex    | [Bitfinex](https://www.bitfinex.com)         | [API](https://bitfinex.readme.io/v1/docs)                      | US                          |
| bitlish     | [bitlish](https://bitlish.com)               | [API](https://bitlish.com/api)                                 | UK, EU, Russia              |
| bitmarket   | [BitMarket](https://www.bitmarket.pl)        | [API](https://www.bitmarket.net/docs.php?file=api_public.html) | Poland, EU                  |
| bitmex      | [BitMEX](https://www.bitmex.com)             | [API](https://www.bitmex.com/app/apiOverview)                  | Seychelles                  |
| bitso       | [Bitso](https://bitso.com)                   | [API](https://bitso.com/api_info)                              | Mexico                      |
| bittrex     | [Bittrex](https://bittrex.com)               | [API](https://bittrex.com/Home/Api)                            | US                          |
| btcchina    | [BTCChina](https://www.btcchina.com)         | [API](https://www.btcchina.com/apidocs)                        | China, US                   |
| btcx        | [BTCX](https://btc-x.is)                     | [API](https://btc-x.is/custom/api-document.html)               | Iceland, US, EU             |
| bxinth      | [BX.in.th](https://bx.in.th)                 | [API](https://bx.in.th/info/api)                               | Thailand                    |
| ccex        | [C-CEX](https://c-cex.com)                   | [API](https://c-cex.com/?id=api)                               | Germany, EU                 |
| cex         | [CEX.IO](https://cex.io)                     | [API](https://cex.io/cex-api)                                  | UK, EU, Cyprus, Russia      |
| coincheck   | [coincheck](https://coincheck.com)           | [API](https://coincheck.com/documents/exchange/api)            | Japan, Indonesia            |
| coinsecure  | [Coinsecure](https://coinsecure.in)          | [API](https://api.coinsecure.in)                               | India                       |
| exmo        | [EXMO](https://exmo.me)                      | [API](https://exmo.me/ru/api_doc)                              | Spain, Russia               |
| fybse       | [FYB-SE](https://www.fybse.se)               | [API](http://docs.fyb.apiary.io)                               | Sweden                      |
| fybsg       | [FYB-SG](https://www.fybsg.com)              | [API](http://docs.fyb.apiary.io)                               | Singapore                   |
| gdax        | [GDAX](https://www.gdax.com)                 | [API](https://docs.gdax.com)                                   | US                          |
| hitbtc      | [HitBTC](https://hitbtc.com)                 | [API](https://hitbtc.com/api)                                  | Hong Kong                   |
| huobi       | [Huobi](https://www.huobi.com)               | [API](https://github.com/huobiapi/API_Docs_en/wiki)            | China                       |
| jubi        | [jubi.com](https://www.jubi.com)             | [API](https://www.jubi.com/help/api.html)                      | China                       |
| kraken      | [Kraken](https://www.kraken.com)             | [API](https://www.kraken.com/en-us/help/api)                   | US                          |
| luno        | [luno](https://www.luno.com)                 | [API](https://npmjs.org/package/bitx)                          | UK, Singapore, South Africa |
| okcoinusd   | [OKCoin USD](https://www.okcoin.com)         | [API](https://www.okcoin.com/rest_getStarted.html)             | China, US                   |
| okcoincny   | [OKCoin CNY](https://www.okcoin.cn)          | [API](https://www.okcoin.cn/rest_getStarted.html)              | China                       |
| poloniex    | [Poloniex](https://poloniex.com)             | [API](https://poloniex.com/support/api/)                       | US                          |
| quadrigacx  | [QuadrigaCX](https://www.quadrigacx.com)     | [API](https://www.quadrigacx.com/api_info)                     | Canada                      |
| quoine      | [QUOINE](https://www.quoine.com)             | [API](https://developers.quoine.com)                           | Japan, Singapore, Vietnam   |
| therock     | [TheRockTrading](https://therocktrading.com) | [API](https://api.therocktrading.com/doc/)                     | Malta                       |
| vaultoro    | [Vaultoro](https://www.vaultoro.com)         | [API](https://api.vaultoro.com)                                | Switzerland                 |
| virwox      | [VirWoX](https://www.virwox.com)             | [API](https://www.virwox.com/developers.php)                   | Austria                     |
| yobit       | [YoBit](https://www.yobit.net)               | [API](https://www.yobit.net/en/api/)                           | Russia                      |
| zaif        | [Zaif](https://zaif.jp)                      | [API](https://corp.zaif.jp/api-docs)                           | Japan                       |

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

Some markets are [DDoS](https://en.wikipedia.org/wiki/Denial-of-service_attack)-protected by [Cloudflare](https://www.cloudflare.com). Your IP can get temporarily blocked during periods of high load. Sometimes they even restrict whole countries and regions. In that case their servers usually return a page that states a HTTP 40x error or runs an AJAX test of your browser and delays the reload of the page for several seconds. Then your browser/fingerprint is granted access temporarily and gets added to a whitelist or receives a HTTP cookie for further use. 

If you encounter Cloudflare DDOS protection errors and cannot reach a particular exchange market then try later or ask the exchange support to add you to a whitelist. 

```
UNDER CONSTRUCTION
```

# Products

Each market is a place for trading some kinds of valuables. Sometimes they are called with various different terms like instruments, symbols, trading pairs, currencies, tokens, stocks, commodities, contracts, etc, but they all mean the same – a trading pair, a symbol, a financial instrument or some kind of *product*. 

In terms of the ccxt library, every market trades products within itself. Also, the set of products differs from market to market opening possibilities for cross-market and cross-product arbitrage.

## Product Structure

Each product is an associative array with the following keys:
- `product['id']`. The string or numeric ID of the product or trade instrument within the market. Product ids are used to identify products and trading pairs with different markets.
- `product['symbol']`. An uppercase string code representation of a particular trading pair or instrument. This is usually written as `BaseCurrency/QuoteCurrency` with a slash as in `BTC/USD`, `LTC/CNY` or `ETH/EUR`, etc. Product symbols are used to identify products within the ccxt library.
- `product['base']`. An uppercase string code of base fiat or crypto currency.
- `product['quote']`. An uppercase string code of quoted fiat or crypto currency.
- `product['info']`. An associative array of non-common market properties, including fees, rates, limits and other general product information. The internal info array is different for each particular market product, its contents depend on the exchange market.

## Loading Products

In most cases you are required to load the list of products and trading symbols for a particular market prior to accessing other market API methods. In order to load products call the `loadProducts()` / `load_products()` method on a market instance. It returns an associative array of products indexed by trading symbol.

```JavaScript
// JavaScript
let kraken = new ccxt.kraken ()
let products = await kraken.load_products ()
let symbols = Object.keys (products)
console.log (kraken.id, products)
console.log (kraken.id, symbols)
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

## Product Cache And Force Reloading

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

Each exchange market offers a set of API methods. Each method of the API is called an *endpoint*. Endpoints are HTTP URLs for querying various types of information. All endpoints return JSON in response to client requests. Usually, there is an endpoint for getting a list of products from an exchange market, an endpoint for retrieving an order book for a particular product, an endpoint for retrieving trade history, endpoints for placing and cancelling orders, for money deposit and withdrawal, etc... Basically every kind of action you could perform within a particular market has a separate endpoint URL offered by exchange API.

Because the set of methods differs from market to market, the ccxt library implements the following:
- a public and private API for all possible URLs and methods
- a unified API supporting a subset of common methods

The endpoint URLs are predefined in the `market['api'] / $market->api` property for each market. You don't have to override it, unless you are implementing a new market API (at least you should know what you're doing). 

The endpoint definition is a list of all API URLs exposed by a market. This list get converted to callable instance methods upon market instantiation. Each URL in the API endpoint list get a corresponding callable method. For example, if a market offers an HTTP GET URL for querying prices like `https://example.com/public/quotes`, it is converted to a method named `example.publicGetQuotes () / $example->publicGetQuotes ()`. This is done automatically for all markets, therefore the ccxt library supports all possible URLs offered by crypto exchanges.

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

For trading with private API you need to obtain API keys from/to exchange markets. It often means registering with exchange markets and creating API keys with your account. Most exchanges require personal info or identification. Some kind of verification may be necessary as well. If you want to trade you need to register yourself, this library will not create accounts or API keys for you. Some exchange APIs expose interface methods for registering an account from within the code itself, but most of exchanges don't. You have to sign up and create API keys with their websites.

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
    let symbol = products[0]['pair']
    bitfinex.publicGetPubtickerSymbol ({ symbol }).then (ticker => {
        // → nested codeflow
        console.log (bitfinex.id, symbol, ticker)
    })
})

// async / await style
(async () => {
    // ↓ linear codeflow
    let pairs = await kraken.publicGetAssetPairs () 
    let symbols = Object.keys (pairs['result'])
    let symbol = symbols[0]
    let ticker = await kraken.publicGetTicker ({ pair: symbol })
    console.log (kraken.id, symbol, ticker)
}) ()
```

## Returned JSON Objects

All public and private API methods return raw decoded JSON objects in response from the exchange markets, as is, untouched. The unified API returns JSON-decoded objects in a common format and structured uniformly across all markets.

## Passing Parameters To API Methods

The set of all possible legacy API endpoints differs from market to market. Most of methods accept a single associative array (or a Python dict) of key-value parameters. The params are passed as follows:

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

# Trading

```
UNDER CONSTRUCTION
```

## Overriding The Nonce

The default nonce is a 32-bit Unix Timestamp (seconds since epoch January 1, 1970).

In case you need to reset the nonce it is much easier to create another pair of keys for using with private APIs. If you are unable to create new keys for some reasons (due to lack of permissions or whatever) – you can still override the nonce by providing a `nonce` parameter to the market constructor and by setting it explicitly on a market object (in JavaScript) or by subclassing and overriding the nonce function of a particular market class (in Python / PHP).

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