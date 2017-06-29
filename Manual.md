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

| id         | name                                         | countries                   |   
|------------|----------------------------------------------|-----------------------------|
| _1broker   | [1Broker](https://1broker.com)               | US                          |   
| _1btcxe    | [1BTCXE](https://1btcxe.com)                 | Panama                      |   
| bit2c      | [Bit2C](https://www.bit2c.co.il)             | Israel                      |   
| bitbay     | [BitBay](https://bitbay.net)                 | Poland, EU                  |   
| bitcoid    | [Bitcoin.co.id](https://www.bitcoin.co.id)   | Indonesia                   |   
| bitfinex   | [Bitfinex](https://www.bitfinex.com)         | US                          |   
| bitlish    | [bitlish](https://bitlish.com)               | UK, EU, Russia              |   
| bitmarket  | [BitMarket](https://www.bitmarket.pl)        | Poland, EU                  |   
| bitmex     | [BitMEX](https://www.bitmex.com)             | Seychelles                  |   
| bitso      | [Bitso](https://bitso.com)                   | Mexico                      |   
| bittrex    | [Bittrex](https://bittrex.com)               | US                          |
| btcx       | [BTCX](https://btc-x.is)                     | Iceland, US, EU             |   
| bxinth     | [BX.in.th](https://bx.in.th)                 | Thailand                    |   
| ccex       | [C-CEX](https://c-cex.com)                   | Germany, EU                 |   
| cex        | [CEX.IO](https://cex.io)                     | UK, EU, Cyprus, Russia      |   
| coincheck  | [coincheck](https://coincheck.com)           | Japan                       |   
| coinsecure | [Coinsecure](https://coinsecure.in)          | India                       |   
| exmo       | [EXMO](https://exmo.me)                      | Spain, Russia               |   
| fybse      | [FYB-SE](https://www.fybse.se)               | Sweden                      |   
| fybsg      | [FYB-SG](https://www.fybsg.com)              | Singapore                   |   
| hitbtc     | [HitBTC](https://hitbtc.com)                 | China, Denmark              |   
| huobi      | [Huobi](https://www.huobi.com)               | China                       |
| jubi       | [jubi.com](https://www.jubi.com)             | China                       |   
| kraken     | [Kraken](https://www.kraken.com)             | US                          |   
| luno       | [luno](https://www.luno.com)                 | UK, Singapore, South Africa |   
| okcoinusd  | [OKCoin USD](https://www.okcoin.com)         | China, US                   |   
| okcoincny  | [OKCoin CNY](https://www.okcoin.cn)          | China                       |   
| poloniex   | [Poloniex](https://poloniex.com)             | US                          |   
| quadrigacx | [QuadrigaCX](https://www.quadrigacx.com)     | Canada                      |   
| quoine     | [QUOINE](https://www.quoine.com)             | Japan, Singapore, Vietnam   |   
| therock    | [TheRockTrading](https://therocktrading.com) | Malta                       |   
| vaultoro   | [Vaultoro](https://www.vaultoro.com)         | Switzerland                 |   
| virwox     | [VirWoX](https://www.virwox.com)             | Austria                     |   
| yobit      | [YoBit](https://www.yobit.net)               | Russia                      |   
| zaif       | [Zaif](https://zaif.jp)                      | Japan                       |   

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
include 'ccxt.php';
$market = new \ccxt\bitfinex (); // default id
$bitfinex1 = new \ccxt\bitfinex (array ('id' => 'bitfinex1'));
$bitfinex2 = new \ccxt\bitfinex (array ('id' => 'bitfinex2'));

```

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

- `market.verbose / market['verbose'] / $market->verbose`: A boolean flag indicating whether to log HTTP requests to stdout (verbose flag is false by default).

- `market.products / market['products'] / $market->products`: An associative array of products indexed by trading pair or symbol. Market products should be loaded prior to accessing this property. Products are unavailable until you call the `loadProduct() / load_products()` method on market instance.

# Products

Each market is a place for trading some kinds of valuables. Sometimes they are called with various different terms like instruments, symbols, trading pairs, currencies, tokens, stocks, commodities, contracts, etc, but they all mean the same – a trading pair, a symbol, a financial instrument or some kind of *product*. 

In terms of the ccxt library, every market trades products within itself. Also, the set of products differs from market to market opening possibilities for cross-market and cross-product arbitrage.

Each product is an associative array with the following keys:
- `product['id']`. The string or numeric ID of the product or trade instrument within the market. Product ids are used to identify products and trading pairs with different markets.
- `product['symbol']`. An uppercase string code representation of a particular trading pair or instrument. This is usually written as `BaseCurrency/QuoteCurrency` with a slash as in `BTC/USD`, `LTC/CNY` or `ETH/EUR`, etc. Product symbols are used to identify products within the ccxt library.
- `product['base']`. An uppercase string code of base fiat or crypto currency.
- `product['quote']`. An uppercase string code of quoted fiat or crypto currency.
- `product['info']`. An associative array of non-common market properties, including fees, rates, limits and other general product information. The internal info array is different for each particular market product, its contents depend on the exchange market.

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

# Endpoints

```
UNDER CONSTRUCTION
```

# Market Data

```
UNDER CONSTRUCTION
```

# Trading

```
UNDER CONSTRUCTION
```