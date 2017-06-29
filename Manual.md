# Overview

```diff
- the ccxt documentation is under heavy development right now
```

The ccxt library is a collection of available crypto exchange markets or market classes. Each *market* implements the public and private API for a particular crypto exchange. All markets are derived from the base Market class and share a set of common methods. To access a particular market from ccxt library you need to create an instance of corresponding market class. Supported markets are updated frequently and new markets are added regularly.

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

A market can be instantiated like so:

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

Every market has a set of properties and methods which can be overridden upon construction (with JavaScript) or by subclassing (with Python and PHP). Among common market members are:

- `market.id` / `market['id']` / `$market->id`.
Each market has a default id. The id is not used for anything, it's a string literal for user-land market instance identification purposes. You can have multiple links to the same exchange market and differentiate them by ids. Default ids are all lowercase and correspond to market names.

- `market.name` / `market['name']` / `$market->name`. This is a string literal containing the human-readable market name.

- `market.countries` / `market['countries']` / `$market->countries`. A string literal or an array of string literals of 2-symbol ISO country codes, where the exchange is operating from.

- `market.urls['name']` / `market['urls']['api']` / `$market->urls['api']`. The single string literal base URL for API calls or an associative array of separate URLs for private and public APIs.

- `market.urls['www']` / `market['urls']['www']` / `$market->urls['www']`. The main HTTP website URL.

- `market.urls['doc']` / `market['urls']['doc']` / `$market->urls['doc']`. A single string URL link to original documentation for exchange API on their website or an array of links to docs.

- `market.version` / `market['version']` / `$market->version`. A string literal containing version identifier for current exchange market API. The version is often used in constructing the API URL. Do not override it unless you are implementing your own new crypto market class.

- `market.api` / `market['api']` / `$market->api`. An associative array containing a definition of all API endpoints exposed by a crypto exchange. The API definition is used by ccxt to automatically construct callable instance methods for each available endpoint.

- `market.timeout` / `market['timeout']` / `$market->timeout`. A timeout for a request-response roundtrip.

# Products

Each market is a place for trading some kinds of valuables. Sometimes they are called with various different terms like instruments, symbols, trading pairs, currencies, tokens, stocks, commodities, contracts, etc, but they all mean the same – a trading pair, a symbol, a financial instrument or some kind of *product*. In terms of the ccxt library, every market trades products within itself. Also, the set of products differs from market to market opening possibilities for cross-market and cross-product arbitrage.

Each product is an associative array with the following keys:
- `product['id']`. The string or numeric ID of the product or trade instrument within the market. Product ids are used to identify products and trading pairs with different markets.
- `product['symbol']`. An uppercase string code representation of a particular trading pair or instrument. This is usually written as `BaseCurrency/QuoteCurrency` with a slash as in `BTC/USD`, `LTC/CNY` or `ETH/EUR`, etc. Product symbols are used to identify products within the ccxt library.
- `product['base']`. An uppercase string code of base fiat or crypto currency.
- `product['quote']`. An uppercase string code of quoted fiat or crypto currency.
- `product['info']`. An associative array of non-common market properties, including fees, rates, limits and other general product information. The internal info array is different for each particular market product, its contents depend on the exchange market.

In most cases you are required to load the list of products and trading symbols for a particular market prior to accessing other market API methods. In order to load products call the `loadProducts()` / `load_products()` method on a market instance.

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