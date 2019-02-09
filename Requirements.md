# CCXT Integration Requirements

The exchange is required to implement the following list of methods and structures in order to get integrated and certified with CCXT.

## Public API

#### Exchange Information, Fee Schedule and Trading Rules

- [`fetchMarkets`](https://github.com/ccxt/ccxt/wiki/Manual#markets) – a list of trading pairs and their statuses + [market structure](https://github.com/ccxt/ccxt/wiki/Manual#market-structure)
- [`fetchCurrencies`]() – a list of tokens or assets and their statuses
- `fetchTradingLimits` – min/max order volume, price, cost, precision, etc...
- `fetchTradingFees` – trading fees, either public or personal
- `fetchFundingLimits` – a list of withdrawal limits

#### Market Data

- [`fetchTicker`](https://github.com/ccxt/ccxt/wiki/Manual#price-tickers) – 24h volumes and stats
- [`fetchOrderBook`](https://github.com/ccxt/ccxt/wiki/Manual#order-book) – l2, l3 + [orderbook structure](https://github.com/ccxt/ccxt/wiki/Manual#order-book-structure)
- [`fetchTrades`](https://github.com/ccxt/ccxt/wiki/Manual#trades-executions-transactions) – a list of recent public trades + [trade structure](https://github.com/ccxt/ccxt/wiki/Manual#trade-structure)

## Private API

#### Trading

- [`fetchBalance`](https://github.com/ccxt/ccxt/wiki/Manual#querying-account-balance) - for all types of accounts + [balance structure](https://github.com/ccxt/ccxt/wiki/Manual#balance-structure)
- `fetchAccounts` - required if exchange allows to manage user accounts / sub-accounts
- [`createOrder`](https://github.com/ccxt/ccxt/wiki/Manual#placing-orders) (limit, market, etc)
- [`cancelOrder`](https://github.com/ccxt/ccxt/wiki/Manual#canceling-orders)
- `editOrder` – change the price/amount of an open order

#### Trading History

- [`fetchOrder`](https://github.com/ccxt/ccxt/wiki/Manual#querying-orders) – one order by order id
- [`fetchOpenOrders`](https://github.com/ccxt/ccxt/wiki/Manual#querying-orders) – a list of all open orders
- [`fetchAllOrders`](https://github.com/ccxt/ccxt/wiki/Manual#querying-orders) – a list of all orders
- [`fetchMyTrades`](https://github.com/ccxt/ccxt/wiki/Manual#personal-trades) – the personal history of filled trades for the account

#### Funding

- [`fetchDepositAddress`](https://github.com/ccxt/ccxt/wiki/Manual#funding-your-account) – deposit address(es) + [address structure](https://github.com/ccxt/ccxt/wiki/Manual#address-structure)
- [`fetchDeposits`](https://github.com/ccxt/ccxt/wiki/Manual#transactions)
- [`fetchWithdrawals`](https://github.com/ccxt/ccxt/wiki/Manual#transactions)
- [`fetchTransactions`](https://github.com/ccxt/ccxt/wiki/Manual#transactions) + [transaction structure](https://github.com/ccxt/ccxt/wiki/Manual#transaction-structure)
- [`fetchLedger`](https://github.com/ccxt/ccxt/wiki/Manual#ledger) - transactions, transfers, referrals, cashbacks + [ledger entry structure](https://github.com/ccxt/ccxt/wiki/Manual#ledger-entry-structureccccccigfrubcntngfuhein)
- [`withdraw`](https://github.com/ccxt/ccxt/wiki/Manual#withdraw)
- `transfer` - required if exchange has sub-accounts to transfer assets between them
