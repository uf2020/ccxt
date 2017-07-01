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

|id          | name                                         | docs                                                           | countries                  |
|------------|----------------------------------------------|----------------------------------------------------------------|----------------------------|
|_1broker    | [1Broker](https://1broker.com)               | [API](https://1broker.com/?c=en/content/api-documentation)     | US                         |
|_1btcxe     | [1BTCXE](https://1btcxe.com)                 | [API](https://1btcxe.com/api-docs.php)                         | Panama                     |
|bit2c       | [Bit2C](https://www.bit2c.co.il)             | [API](https://www.bit2c.co.il/home/api)                        | Israel                     |
|bitbay      | [BitBay](https://bitbay.net)                 | [API](https://bitbay.net/public-api)                           | Poland, EU                 |
|bitcoincoid | [Bitcoin.co.id](https://www.bitcoin.co.id)   | [API](https://vip.bitcoin.co.id/trade_api)                     | Indonesia                  |
|bitfinex    | [Bitfinex](https://www.bitfinex.com)         | [API](https://bitfinex.readme.io/v1/docs)                      | US                         |
|bitlish     | [bitlish](https://bitlish.com)               | [API](https://bitlish.com/api)                                 | UK, EU, Russia             |
|bitmarket   | [BitMarket](https://www.bitmarket.pl)        | [API](https://www.bitmarket.net/docs.php?file=api_public.html) | Poland, EU                 |
|bitmex      | [BitMEX](https://www.bitmex.com)             | [API](https://www.bitmex.com/app/apiOverview)                  | Seychelles                 |
|bitso       | [Bitso](https://bitso.com)                   | [API](https://bitso.com/api_info)                              | Mexico                     |
|bittrex     | [Bittrex](https://bittrex.com)               | [API](https://bittrex.com/Home/Api)                            | US                         |
|btcchina    | [BTCChina](https://www.btcchina.com)         | [API](https://www.btcchina.com/apidocs)                        | China                      |
|btcx        | [BTCX](https://btc-x.is)                     | [API](https://btc-x.is/custom/api-document.html)               | Iceland, US, EU            |
|bxinth      | [BX.in.th](https://bx.in.th)                 | [API](https://bx.in.th/info/api)                               | Thailand                   |
|ccex        | [C-CEX](https://c-cex.com)                   | [API](https://c-cex.com/?id=api)                               | Germany, EU                |
|cex         | [CEX.IO](https://cex.io)                     | [API](https://cex.io/cex-api)                                  | UK, EU, Cyprus, Russia     |
|coincheck   | [coincheck](https://coincheck.com)           | [API](https://coincheck.com/documents/exchange/api)            | Japan, Indonesia           |
|coinsecure  | [Coinsecure](https://coinsecure.in)          | [API](https://api.coinsecure.in)                               | India                      |
|exmo        | [EXMO](https://exmo.me)                      | [API](https://exmo.me/ru/api_doc)                              | Spain, Russia              |
|fybse       | [FYB-SE](https://www.fybse.se)               | [API](http://docs.fyb.apiary.io)                               | Sweden                     |
|fybsg       | [FYB-SG](https://www.fybsg.com)              | [API](http://docs.fyb.apiary.io)                               | Singapore                  |
|gdax        | [GDAX](https://www.gdax.com)                 | [API](https://docs.gdax.com)                                   | US                         |
|hitbtc      | [HitBTC](https://hitbtc.com)                 | [API](https://hitbtc.com/api)                                  | Hong Kong                  |
|huobi       | [Huobi](https://www.huobi.com)               | [API](https://github.com/huobiapi/API_Docs_en/wiki)            | China                      |
|jubi        | [jubi.com](https://www.jubi.com)             | [API](https://www.jubi.com/help/api.html)                      | China                      |
|kraken      | [Kraken](https://www.kraken.com)             | [API](https://www.kraken.com/en-us/help/api)                   | US                         |
|luno        | [luno](https://www.luno.com)                 | [API](https://npmjs.org/package/bitx)                          | UK, Singapore, South Africa|
|okcoinusd   | [OKCoin USD](https://www.okcoin.com)         | [API](https://www.okcoin.com/rest_getStarted.html)             | China, US                  |
|okcoincny   | [OKCoin CNY](https://www.okcoin.cn)          | [API](https://www.okcoin.cn/rest_getStarted.html)              | China                      |
|poloniex    | [Poloniex](https://poloniex.com)             | [API](https://poloniex.com/support/api/)                       | US                         |
|quadrigacx  | [QuadrigaCX](https://www.quadrigacx.com)     | [API](https://www.quadrigacx.com/api_info)                     | Canada                     |
|quoine      | [QUOINE](https://www.quoine.com)             | [API](https://developers.quoine.com)                           | Japan, Singapore, Vietnam  |
|therock     | [TheRockTrading](https://therocktrading.com) | [API](https://api.therocktrading.com/doc/)                     | Malta                      |
|vaultoro    | [Vaultoro](https://www.vaultoro.com)         | [API](https://api.vaultoro.com)                                | Switzerland                |
|virwox      | [VirWoX](https://www.virwox.com)             | [API](https://www.virwox.com/developers.php)                   | Austria                    |
|yobit       | [YoBit](https://www.yobit.net)               | [API](https://www.yobit.net/en/api/)                           | Russia                     |
|zaif        | [Zaif](https://zaif.jp)                      | [API](https://corp.zaif.jp/api-docs)                           | Japan                      |

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