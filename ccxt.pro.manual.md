# Manual

The CCXT Pro stack is built upon [CCXT](https://ccxt.trade) and extends the core CCXT classes, using:

- JavaScript prototype-level mixins
- Python multiple inheritance
- PHP Traits

The CCXT Pro heavily relies on the transpiler of CCXT for [multilanguge support](https://github.com/ccxt/ccxt/blob/master/CONTRIBUTING.md#multilanguage-support).

```
                                 User

    +-------------------------------------------------------------+
    |                          CCXT Pro                           |
    +------------------------------+------------------------------+
    |            Public            .           Private            |
    +=============================================================+
    │                              .                              |
    │                  The Unified CCXT Pro API                   |
    |                              .                              |
    |       loadMarkets            .           watchBalance       |
    |       watchTicker            .       watchCreateOrder       |
    |       watchTickers           .       watchCancelOrder       |
    |       watchOrderBook         .             watchOrder       |
    |       watchOHLCV             .            watchOrders       |
    |       watchStatus            .        wathgOpenOrders       |
    |       watchTrades            .      watchClosedOrders       |
    |                              .          watchMyTrades       |
    |                              .           watchDeposit       |
    |                              .          watchWithdraw       |
    │                              .                              |
    +=============================================================+
    │                              .                              |
    |            The Underlying Exchange-Specific APIs            |
    |         (Derived Classes And Their Implementations)         |
    │                              .                              |
    +=============================================================+
    │                              .                              |
    |                 CCXT Pro Base Exchange Class                |
    │                              .                              |
    +=============================================================+

    +-------------------------------------------------------------+
    |                                                             |
    |                            CCXT                             |
    |                                                             |
    +=============================================================+
```

# Exchanges

The CCXT Pro library currently supports the following 12 cryptocurrency exchange markets and trading APIs:

|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;logo&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;                                                                                                       | id                 | name                                                                                    | ver | doc                                                                                          | certified                                                                                                                   | pro                                                                         |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------|-----------------------------------------------------------------------------------------|:---:|:--------------------------------------------------------------------------------------------:|-----------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------|
|[![binance](https://user-images.githubusercontent.com/1294454/29604020-d5483cdc-87ee-11e7-94c7-d1a8d9169293.jpg)](https://www.binance.com/?ref=10205187)                                       | binance            | [Binance](https://www.binance.com/?ref=10205187)                                        | *   | [API](https://binance-docs.github.io/apidocs/spot/en)                                        | [![CCXT Certified](https://img.shields.io/badge/CCXT-Certified-green.svg)](https://github.com/ccxt/ccxt/wiki/Certification) | [![CCXT Pro](https://img.shields.io/badge/CCXT-Pro-black)](https://ccxt.pro)|
|[![binanceje](https://user-images.githubusercontent.com/1294454/54874009-d526eb00-4df3-11e9-928c-ce6a2b914cd1.jpg)](https://www.binance.je/?ref=35047921)                                      | binanceje          | [Binance Jersey](https://www.binance.je/?ref=35047921)                                  | *   | [API](https://github.com/binance-exchange/binance-official-api-docs/blob/master/rest-api.md) |                                                                                                                             | [![CCXT Pro](https://img.shields.io/badge/CCXT-Pro-black)](https://ccxt.pro)|
|[![binanceus](https://user-images.githubusercontent.com/1294454/65177307-217b7c80-da5f-11e9-876e-0b748ba0a358.jpg)](https://www.binance.us/?ref=35005074)                                      | binanceus          | [Binance US](https://www.binance.us/?ref=35005074)                                      | *   | [API](https://github.com/binance-us/binance-official-api-docs)                               |                                                                                                                             | [![CCXT Pro](https://img.shields.io/badge/CCXT-Pro-black)](https://ccxt.pro)|
|[![bitfinex](https://user-images.githubusercontent.com/1294454/27766244-e328a50c-5ed2-11e7-947b-041416579bb3.jpg)](https://www.bitfinex.com/?refcode=P61eYxFL)                                 | bitfinex           | [Bitfinex](https://www.bitfinex.com/?refcode=P61eYxFL)                                  | 1   | [API](https://docs.bitfinex.com/v1/docs)                                                     | [![CCXT Certified](https://img.shields.io/badge/CCXT-Certified-green.svg)](https://github.com/ccxt/ccxt/wiki/Certification) | [![CCXT Pro](https://img.shields.io/badge/CCXT-Pro-black)](https://ccxt.pro)|
|[![bitmex](https://user-images.githubusercontent.com/1294454/27766319-f653c6e6-5ed4-11e7-933d-f0bc3699ae8f.jpg)](https://www.bitmex.com/register/rm3C16)                                       | bitmex             | [BitMEX](https://www.bitmex.com/register/rm3C16)                                        | 1   | [API](https://www.bitmex.com/app/apiOverview)                                                |                                                                                                                             | [![CCXT Pro](https://img.shields.io/badge/CCXT-Pro-black)](https://ccxt.pro)|
|[![bittrex](https://user-images.githubusercontent.com/1294454/27766352-cf0b3c26-5ed5-11e7-82b7-f3826b7a97d8.jpg)](https://bittrex.com)                                                         | bittrex            | [Bittrex](https://bittrex.com)                                                          | 1.1 | [API](https://bittrex.github.io/api/)                                                        | [![CCXT Certified](https://img.shields.io/badge/CCXT-Certified-green.svg)](https://github.com/ccxt/ccxt/wiki/Certification) | [![CCXT Pro](https://img.shields.io/badge/CCXT-Pro-black)](https://ccxt.pro)|
|[![coinbaseprime](https://user-images.githubusercontent.com/1294454/44539184-29f26e00-a70c-11e8-868f-e907fc236a7c.jpg)](https://prime.coinbase.com)                                            | coinbaseprime      | [Coinbase Prime](https://prime.coinbase.com)                                            | *   | [API](https://docs.prime.coinbase.com)                                                       |                                                                                                                             | [![CCXT Pro](https://img.shields.io/badge/CCXT-Pro-black)](https://ccxt.pro)|
|[![coinbasepro](https://user-images.githubusercontent.com/1294454/41764625-63b7ffde-760a-11e8-996d-a6328fa9347a.jpg)](https://pro.coinbase.com/)                                               | coinbasepro        | [Coinbase Pro](https://pro.coinbase.com/)                                               | *   | [API](https://docs.pro.coinbase.com)                                                         |                                                                                                                             | [![CCXT Pro](https://img.shields.io/badge/CCXT-Pro-black)](https://ccxt.pro)|
|[![gateio](https://user-images.githubusercontent.com/1294454/31784029-0313c702-b509-11e7-9ccc-bc0da6a0e435.jpg)](https://www.gate.io/signup/2436035)                                           | gateio             | [Gate.io](https://www.gate.io/signup/2436035)                                           | 2   | [API](https://gate.io/api2)                                                                  |                                                                                                                             | [![CCXT Pro](https://img.shields.io/badge/CCXT-Pro-black)](https://ccxt.pro)|
|[![kraken](https://user-images.githubusercontent.com/1294454/27766599-22709304-5ede-11e7-9de1-9f33732e1509.jpg)](https://www.kraken.com)                                                       | kraken             | [Kraken](https://www.kraken.com)                                                        | 0   | [API](https://www.kraken.com/features/api)                                                   | [![CCXT Certified](https://img.shields.io/badge/CCXT-Certified-green.svg)](https://github.com/ccxt/ccxt/wiki/Certification) | [![CCXT Pro](https://img.shields.io/badge/CCXT-Pro-black)](https://ccxt.pro)|
|[![kucoin](https://user-images.githubusercontent.com/1294454/57369448-3cc3aa80-7196-11e9-883e-5ebeb35e4f57.jpg)](https://www.kucoin.com/?rcode=E5wkqe)                                         | kucoin             | [KuCoin](https://www.kucoin.com/?rcode=E5wkqe)                                          | 2   | [API](https://docs.kucoin.com)                                                               |                                                                                                                             | [![CCXT Pro](https://img.shields.io/badge/CCXT-Pro-black)](https://ccxt.pro)|
|[![poloniex](https://user-images.githubusercontent.com/1294454/27766817-e9456312-5ee6-11e7-9b3c-b628ca5626a5.jpg)](https://www.poloniex.com/?utm_source=ccxt&utm_medium=web)                   | poloniex           | [Poloniex](https://www.poloniex.com/?utm_source=ccxt&utm_medium=web)                    | *   | [API](https://docs.poloniex.com)                                                             | [![CCXT Certified](https://img.shields.io/badge/CCXT-Certified-green.svg)](https://github.com/ccxt/ccxt/wiki/Certification) | [![CCXT Pro](https://img.shields.io/badge/CCXT-Pro-black)](https://ccxt.pro)|

This list will be updated with new exchanges on a regular basis.

# Usage

```diff
- this part of the doc is under heavy development right now
- there may be some typos, mistakes and missing info here and there
- contributions, pull requests and feedback appreciated
```

## Prerequisites

The best way to understand CCXT Pro is to make sure you grasp the entire CCXT Manual and practice standard CCXT first. CCXT Pro borrows from CCXT. The two libraries share a lot of commonalities, including:

- the concepts of public API and private authenticated API
- markets, symbols, currency codes and ids
- unified data structures and formats, orderbooks, trades, orders, candles, ...
- exceptions and error mappings
- authentication and API keys (for private feeds and calls)
- configuration options

The CCXT Pro audience consists mostly of professional algorithmic traders and developers. In order to work efficiently with this library the user is required to be well-familiar with the concepts of streaming. One has to understand the underlying differences between connection-based streaming APIs ([WebSocket](https://en.wikipedia.org/wiki/WebSocket), CCXT Pro) and request-response based APIs ([REST](https://en.wikipedia.org/wiki/Representational_state_transfer), CCXT).

The general async-style flow for a CCXT application is as follows:

```JavaScript

// a RESTful orderbook polling request-response loop

while (condition) {

    try {

        // fetch some of the public data
        orderbook = await exchange.fetchOrderBook (symbol, limit)

        // do something or react somehow based on that data
        // ...

    } catch (e) {

        // handle errors
    }
}
```

In CCXT Pro each public and private unified RESTful method having a `fetch*` prefix also has a corresponding stream-based counterpart method prefixed with `watch*`, as follows:

- Public API
  - `fetchStatus` → `watchStatus`
  - `fetchOrderBook` → `watchOrderBook`
  - `fetchTicker` → `watchTicker`
  - `fetchTickers` → `watchTickers`
  - `fetchOHLCV` → `watchOHLCV`
  - `fetchTrades` → `watchTrades`
  - `fetchStatus` → `watchStatus`
- Private API
  - `fetchBalance` → `watchBalance`
  - `fetchOrders` → `watchOrders`
  - `fetchMyTrades` → `watchMyTrades`
  - `fetchTransactions` → `watchTransactions`
  - `fetchLedger` → `watchLedger`
  - `createOrder` → `watchCreateOrder` <sup>*(notice the `watch` prefix)*</sup>
  - `cancelOrder` → `watchCancelOrder` <sup>*(notice the `watch` prefix)*</sup>

The Unified CCXT Pro Streaming API inherits CCXT usage patterns to make migration easier.

The general async-style flow for a CCXT Pro application (as opposed to a CCXT application above) is shown below:

```JavaScript

// a stream-based (WebSocket) orderbook feed loop

while (condition) {

    try {

        // watch some of the public data
        orderbook = await exchange.watchOrderBook (symbol, limit)

        // do something or react somehow based on that data
        // ...

    } catch (e) {

        // handle errors
    }
}
```

That usage pattern is usually wrapped up into a core business-logic method called _"a `tick()` function"_, since it reiterates a reaction to the incoming events (aka _ticks_). From the two examples above it is obvious that the generic usage pattern in CCXT Pro and CCXT is identical.

Many of the CCXT rules and concepts also apply to CCXT Pro:

- CCXT Pro will load markets and will cache markets upon the first call to a unified API method
- CCXT Pro will call CCXT RESTful methods under the hood if necessary
- CCXT Pro will throw standard CCXT exceptions where necessary
- ...

## Streaming Specifics

Despite of the numerous commonalities, streaming-based APIs have their own specifics, because of their connection-based nature.

Having a connection-based interface implies connection-handling mechanisms. Connections are managed by CCXT Pro transparently to the user. Each exchange instance manages its own set of connections.

Upon your first call to any `watch*()` method the library will establish a connection to a specific stream/resource of the exchange and will maintain it. If the connection already exists – it is reused. The library will handle the subscription request/response messaging sequences as well as the authentication/signing if the requested stream is private.

The library will also watch the status of the uplink and will keep the connection alive. Upon a critical exception, a disconnect or a connection timeout/failure, the next iteration of the tick function will call the `watch` method that will trigger a reconnection. This way the library handles disconnections and reconnections for the user transparently. CCXT Pro applies the necessary rate-limiting and exponential backoff reconnection delays. All of that functionality is enabled by default and can be configured via exchange properties, as usual.

Most of the exchanges only have a single base URL for streaming APIs (usually, WebSocket, starting with `ws://` or `wss://`). Some of them may have more than one URL for each stream, depending on the feed in question.

Exchanges' Streaming APIs can be classified into two different categories:

- *sub* or *subscribe* allows receiving only
- *pub* or *publish* allows sending and receiving

### Sub

A *sub* interface usually allows to subscribe to a stream of data and listen for it. Most of exchanges that do support WebSockets will offer a *sub* type of API only. The *sub* type includes streaming public market data. Sometimes exchanges also allow subcribing to private user data. After the user subscribes to a data feed the channel effectively starts working one-way sending updates from the exchange towards the user continuously.

Commonly appearing types of public data streams:

- order book (most common) - updates on added, edited and deleted orders (aka *change deltas*)
- ticker updates upon changing of 24 hour stats
- fills feed (also common) - a live stream of public trades
- ohlcv candlestick feed
- heartbeat
- exchange chat/trollbox

Less common types of private user data streams:

- the stream of private trades of the user
- live order updates
- balance updates
- custom streams
- exchange-specific and other streams

### Pub

A *pub* interface usually allows users to send data requests towards the server. This usually includes common user actions, like:

- placing orders
- canceling orders
- placing withdrawal requests
- posting chat/trollbox messages
- etc

**Some exchanges do not offer a *pub* WS API, they will offer *sub* WS API only.** However, there are exchanges that have a complete Streaming API as well. In most cases a user cannot operate effectively having just the Streaming API. Exchanges will stream public market data *sub*, and the REST API is still needed for the *pub* part where missing.

### Incremental Data Structures

In many cases due to a unidirectional nature of the underlying data feeds, the application listening on the client-side has to keep a local snapshot of the data in memory and merge the updates received from the exchange server into the local snapshot. The updates coming from the exchange are also often called _deltas_, because in most cases those updates will contain just the changes between two states of the data and will not include the data that has not changed making it necessary to store the locally cached current state S of all relevant data objects.

All of that functionality is handled by CCXT Pro for the user. To work with CCXT Pro, the user does not have to track or manage subscriptions and related data. CCXT Pro will keep a cache of structures in memory to handle the underlying hassle.

Each incoming update says which parts of the data have changed and the receiving side "increments" local state S by merging the update on top of current state S and moves to next local state S'. In terms CCXT Pro that is called _"incremental state"_ and the structures involved in the process of storing and updating the cached state are called _"incremental structures"_. CCXT Pro introduces several new base classes to handle the incremental state where necessary.

## Linking

The process of including the CCXT Pro library into your script is pretty much the same as with the standard CCXT, the only difference is the name of the actual JavaScript module, Python package, or PHP namespace.

```JavaScript
// JavaScript
const ccxtpro = require ('ccxt.pro')
console.log ('CCXT Pro version', ccxtpro.version)
console.log ('Supported exchanges:', ccxtpro.exchanges)
```

```Python
# Python
import ccxtpro
print('CCXT Pro version', ccxtpro.__version__)
print('Supported exchanges:', ccxtpro.exchanges)
```

```PHP
// PHP
use \ccxtpro; // optional, since you can use fully qualified names
echo 'CCXT Pro version ', \ccxtpro\Exchange::VERSION, "\n";
echo 'Supported exchanges: ', json_encode(\ccxtpro\Exchange::$exchanges), "\n";
```

The imported CCXT Pro module wraps the CCXT inside itself – every exchange instantiated via CCXT Pro has all the CCXT methods as well as the additional functionality.

## Instantiation

CCXT Pro is designed for async/await style syntax and relies heavily on async primitives such as *promises* and *futures*.

Creating a CCXT Pro exchange instance is pretty much identical to creating a CCXT exchange instance, as shown below.

```JavaScript
// JavaScript
const ccxtpro = require ('ccxt.pro')
const exchange = new ccxtpro.binance ({ enableRateLimit: true })
```

```Python
# Python
import ccxtpro
exchange = ccxtpro.kraken({'enableRateLimit': True})
```

In PHP the async primitives are borrowed from [ReactPHP](https://reactphp.org). The PHP implementation of CCXT Pro relies on [Promise](https://github.com/reactphp/promise) and [EventLoop](https://github.com/reactphp/event-loop) in particular. In PHP the user is required to supply a ReactPHP's event loop instance in the constructor arguments as shown below:

```PHP
// PHP
error_reporting(E_ALL | E_STRICT);
date_default_timezone_set('UTC');
require_once 'vendor/autoload.php';

$loop = \React\EventLoop\Factory::create(); // the event loop goes here ↓
$exchange = new \ccxtpro\kucoin(array('enableRateLimit' => true, 'loop' => $loop));
```

## Exchange Properties

Every CCXT Pro instance contains all properties of the underlying CCXT instance. Apart from the standard CCXT properties, the CCXT Pro instance includes the following:

```JavaScript
{
    'has': { // an associative array of extended exchange capabilities
        'ws': true, // only available in CCXT Pro
        'watchOrderBook': true,
        'watchTicker': true,
        'watchTrades': true,
        'watchOHLCV': true,
        'watchBalance': true,
        'watchCreateOrder': true,
        'watchCancelOrder': true,
        ...
    },
    'urls': {
        'api': { // will contain a streaming API base URL, depending on the underlying protocol
            'ws': 'wss://ws.exchange.com',            // https://en.wikipedia.org/wiki/WebSocket
            'signalr': 'https://signalr.exchange.com' // https://en.wikipedia.org/wiki/SignalR
            'socketio': 'wss://socket.exchange.io'    // https://socket.io
        },
    },
    'version': '1.21',
    'streaming': {
        'keepAlive': 30000, // integer keep-alive rate in milliseconds
        'maxPingPongMisses': 2.0, // how many ping pong misses to drop and reconnect
        ... // other streaming options
    },
    // incremental data structures
    'orderbooks':   {}, // incremental order books indexed by symbol
    'ohlcvs':       {}, // standard CCXT OHLCVs indexed by symbol by timeframe
    'balance':      {}, // a standard CCXT balance structure, accounts indexed by currency code
    'orders':       {}, // standard CCXT order structures indexed by order id
    'trades':       {}, // arrays of CCXT trades indexed by symbol
    'tickers':      {}, // standard CCXT tickers indexed by symbol
    'transactions': {}, // standard CCXT deposits and withdrawals indexed by id or txid
    ...
}
```

## Unified API

The Unified CCXT Pro API encourages direct control flow for better codestyle, more readable and architecturally superior code compared to using EventEmitters and callbacks. The latter is considered an outdated approach nowadays since it requires inversion of control (people aren't used to inverted thinking).

CCXT Pro goes with the modern approach and it is designed for the async syntax. Under the hood, CCXT Pro will still have to use inverted control flow sometimes because of the dependencies and the WebSocket libs that can't do otherwise.

The same is true not only for JS/ES6 but also for Python 3 async code as well. In PHP the async primitives are borrowed from [ReactPHP](https://reactphp.org/).

Modern async syntax allows you to combine and split the execution into parallel pathways and then merge them, group them, prioritize them, and what not. With promises one can easily convert from direct async-style control flow to inverted callback-style control flow, back and forth.

### Real-Time vs Throttling

CCXT Pro supports two modes of tick function loops – the real-time mode and the throttling mode. Both of them are shown below in pseudocode:

```JavaScript
// real-time mode
const limit = 5 // optional
while (true) {
    try {
        const orderbook = await exchange.watchOrderBook (symbol, limit)
        // your reaction to the update takes place here
        // you arrive here after receiving the update from the exchange in real time
        console.log (orderbook) // every update
    } catch (e) {
        console.log (e)
        // throw e // uncomment to stop the loop on exceptions
    }
}
```

```JavaScript
// throttling mode
const limit = 5 // optional
// await is optional, alternatively you can launch it in bg without await
await exchange.watchOrderBook (symbol, limit)
while (true) {
    // your reaction takes place here
    // you arrive here every 100 ms regardless of whether there was an update or not
    // in throttling mode offloading the orderbook with .limit () is required
    console.log (exchange.orderbooks[symbol].limit (limit))
    await sleep (100) // every 100 ms
}
```

In **real-time mode** CCXT Pro will return the result as soon as each new delta arrives from the exchange. The general logic of a unified call in a real-time loop is to await for the next delta and immediately return the unified result structure to the user, over and over again. This is useful when reaction time is critical, or has to be as fast as possible.

However, the real-time mode requires programming experience with async flows when it comes to synchronizing multiple parallel tick loops. Apart from that, the exchanges can stream a very large number of updates during periods of high activity or high volatility. Therefore the user developing a real-time algorithm has to make sure that the userland code is capable of consuming data that fast. Working in real-time mode may be more demanding for resources sometimes.

In **throttling mode** CCXT Pro will receive and manage the data in the background. The user is responsible for calling the results from time to time when necessary. The general logic of the throttling loop is to sleep for the most time and wake up to check results occasionally. This is usually done at some fixed frequency, or, "frame rate". The code inside a throttling loop is often easier to synchronize across multiple exchanges. The rationing of time spent in a throttled loop also helps reduce resource usage to a minimum. This is handy when your algorithm is heavy and you want to control the execution precisely to avoid running it too often.

The obvious downside of the throttling mode is being less reactive or responsive to updates. When a trading algorithm has to wait some number milliseconds before being executed – an update or two may arrive sooner than that time expires. In throttling mode the user will only check for those updates upon next wakeup (loop iteration), so the reaction delay may vary within some number of milliseconds over time.

### Public Methods

#### Market Data

##### watchOrderBook

```JavaScript
// JavaScript
if (exchange.has['watchOrderBook']) {
    while (true) {
        try {
            const orderbook = await exchange.watchOrderBook (symbol, limit, params)
            console.log (new Date (), symbol, orderbook['asks'][0], orderbook['bids'][0])
        } catch (e) {
            console.log (e)
            // stop the loop on exception or leave it commented to retry
            // throw e
        }
    }
}
```

```Python
# Python
if exchange.has['watchOrderBook']:
    while True:
        try:
            orderbook = await exchange.watch_order_book(symbol, limit, params)
            print(exchange.iso8601(exchange.milliseconds()), symbol, orderbook['asks'][0], orderbook['bids'][0])
        except Exception as e:
            print(e)
            # stop the loop on exception or leave it commented to retry
            # rasie e
```

```PHP
// PHP
if ($exchange->has['watchOrderBook']) {
    $main = function () use (&$exchange, &$main, $symbol, $limit, $params) {
        $exchange->watch_order_book($symbol, $limit, $params)->then(function($orderbook) use (&$main, $symbol) {
            echo date('c'), ' ', $symbol, ' ', json_encode(array($orderbook['asks'][0], $orderbook['bids'][0])), "\n";
            $main();
        })->otherwise(function (\Exception $e) use (&$main) {
            echo get_class ($e) . ' ' . $e->getMessage (). "\n";
            $main();
            // stop the loop on exception or leave it commented to retry
            // throw $e;
        })
    };
    $loop->futureTick($main);
}
```

##### watchTicker

```JavaScript
// JavaScript
if (exchange.has['watchTicker']) {
    while (true) {
        try {
            const ticker = await exchange.watchTicker (symbol, params)
            console.log (new Date (), ticker)
        } catch (e) {
            console.log (e)
            // stop the loop on exception or leave it commented to retry
            // throw e
        }
    }
}
```

```Python
# Python
if exchange.has['watchTicker']:
    while True:
        try:
            ticker = await exchange.watch_ticker(symbol, params)
            print(exchange.iso8601(exchange.milliseconds()), ticker)
        except Exception as e:
            print(e)
            # stop the loop on exception or leave it commented to retry
            # rasie e
```

```PHP
// PHP
if ($exchange->has['watchTicker']) {
    $main = function () use (&$exchange, &$main, $symbol, $params) {
        $exchange->watch_ticker($symbol, $params)->then(function($ticker) use (&$main) {
            echo date('c'), ' ', json_encode($ticker), "\n";
            $main();
        })->otherwise(function (\Exception $e) use (&$main) {
            echo get_class ($e) . ' ' . $e->getMessage (). "\n";
            $main();
            // stop the loop on exception or leave it commented to retry
            // throw $e;
        })
    };
    $loop->futureTick($main);
}
```

##### watchTickers

```JavaScript
// JavaScript
if (exchange.has['watchTickers']) {
    while (true) {
        try {
            const tickers = await exchange.watchTickers (symbols, params)
            console.log (new Date (), tickers)
        } catch (e) {
            console.log (e)
            // stop the loop on exception or leave it commented to retry
            // throw e
        }
    }
}
```

```Python
# Python
if exchange.has['watchTickers']:
    while True:
        try:
            tickers = await exchange.watch_tickers(symbols, params)
            print(exchange.iso8601(exchange.milliseconds()), tickers)
        except Exception as e:
            print(e)
            # stop the loop on exception or leave it commented to retry
            # rasie e
```

```PHP
// PHP
if ($exchange->has['watchTickers']) {
    $main = function () use (&$exchange, &$main, $symbols, $params) {
        $exchange->watch_tickers($symbols, $params)->then(function($tickers) use (&$main) {
            echo date('c'), ' ', json_encode($tickers), "\n";
            $main();
        })->otherwise(function (\Exception $e) use (&$main) {
            echo get_class ($e) . ' ' . $e->getMessage (). "\n";
            $main();
            // stop the loop on exception or leave it commented to retry
            // throw $e;
        })
    };
    $loop->futureTick($main);
}
```

##### watchOHLCV

```JavaScript
// JavaScript
if (exchange.has['watchOHLCV']) {
    while (true) {
        try {
            const candles = await exchange.watchOHLCV (symbol, since, limit, params)
            console.log (new Date (), candles)
        } catch (e) {
            console.log (e)
            // stop the loop on exception or leave it commented to retry
            // throw e
        }
    }
}
```

```Python
# Python
if exchange.has['watchOHLCV']:
    while True:
        try:
            candles = await exchange.watch_ohlcv(symbol, since, limit, params)
            print(exchange.iso8601(exchange.milliseconds()), candles)
        except Exception as e:
            print(e)
            # stop the loop on exception or leave it commented to retry
            # rasie e
```

```PHP
// PHP
if ($exchange->has['watchOHLCV']) {
    $main = function () use (&$exchange, &$main, $symbol, $timeframe, $since, $limit, $params) {
        $exchange->watch_ohlcv($symbol, $timeframe, $since, $limit, $params)->then(
            function($candles) use (&$main, $symbol, $timeframe) {
                echo date('c'), ' ', $symbol, ' ', $timeframe, ' ', json_encode($candles), "\n";
                $main();
            }
        )->otherwise(function (\Exception $e) use (&$main) {
            echo get_class ($e) . ' ' . $e->getMessage (). "\n";
            $main();
            // stop the loop on exception or leave it commented to retry
            // throw $e;
        })
    };
    $loop->futureTick($main);
}
```

##### watchTrades

```JavaScript
// JavaScript
if (exchange.has['watchTrades']) {
    while (true) {
        try {
            const trades = await exchange.watchTrades (symbol, since, limit, params)
            console.log (new Date (), trades)
        } catch (e) {
            console.log (e)
            // stop the loop on exception or leave it commented to retry
            // throw e
        }
    }
}
```

```Python
# Python
if exchange.has['watchTrades']:
    while True:
        try:
            trades = await exchange.watch_trades(symbol, since, limit, params)
            print(exchange.iso8601(exchange.milliseconds()), trades)
        except Exception as e:
            print(e)
            # stop the loop on exception or leave it commented to retry
            # rasie e
```

```PHP
// PHP
if ($exchange->has['watchTrades']) {
    $main = function () use (&$exchange, &$main, $symbol, $since, $limit, $params) {
        $exchange->watch_trades($symbol, $since, $limit, $params)->then(function($trades) use (&$main) {
            echo date('c'), ' ', json_encode($trades), "\n";
            $main();
        })->otherwise(function (\Exception $e) use (&$main) {
            echo get_class ($e) . ' ' . $e->getMessage (). "\n";
            $main();
            // stop the loop on exception or leave it commented to retry
            // throw $e;
        })
    };
    $loop->futureTick($main);
}
```

### Private Methods

```diff
- work in progress now
```

#### Authentication

In most cases the authentication logic is borrowed from CCXT since the exchanges use the same keypairs and signing algorithms for REST APIs and WebSocket APIs. See [API Keys Setup](https://github.com/ccxt/ccxt/wiki/Manual#api-keys-setup) for more details.

#### Trading

##### watchBalance

```JavaScript
// JavaScript
if (exchange.has['watchBalance']) {
    while (true) {
        try {
            const balance = await exchange.watchBalance (params)
            console.log (new Date (), balance)
        } catch (e) {
            console.log (e)
            // stop the loop on exception or leave it commented to retry
            // throw e
        }
    }
}
```

```Python
# Python
if exchange.has['watchBalance']:
    while True:
        try:
            balance = await exchange.watch_balance(params)
            print(exchange.iso8601(exchange.milliseconds()), balance)
        except Exception as e:
            print(e)
            # stop the loop on exception or leave it commented to retry
            # rasie e
```

```PHP
// PHP
if ($exchange->has['watchBalance']) {
    $main = function () use (&$exchange, &$main, $params) {
        $exchange->watch_balance($params)->then(function($balance) use (&$main) {
            echo date('c'), ' ', json_encode($balance), "\n";
            $main();
        })->otherwise(function (\Exception $e) use (&$main) {
            echo get_class ($e) . ' ' . $e->getMessage (). "\n";
            $main();
            // stop the loop on exception or leave it commented to retry
            // throw $e;
        })
    };
    $loop->futureTick($main);
}
```

##### watchOrders

```diff
- work in progress now
```

##### watchCreateOrder

```diff
- work in progress now
```

##### watchCancelOrder

```diff
- work in progress now
```

##### watchMyTrades

```diff
- work in progress now
```

```JavaScript
// JavaScript
watchMyTrades (symbol = undefined, since = undefined, limit = undefined, params = {})
```

```Python
# Python
watch_my_trades(symbol=None, since=None, limit=None, params={})
```

```PHP
// PHP
watch_my_trades($symbol = null, $since = null, $lmit = null, $params = array());
```

#### Funding

##### watchTransactions

```diff
- work in progress now
```

## Error Handling

In case of an error the CCXT Pro will throw a standard CCXT exception, see [Error Handling](https://github.com/ccxt/ccxt/wiki/Manual#error-handling) for more details.
