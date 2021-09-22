# Import historical data

## Overview
This feature allows you to import historical data (tickers you selected) in Cassandre database, so you can initialise your strategy.

## Data file & format
At startup, Cassandre will search for all files starting with `tickers-to-import` and ending with `csv`.

This is how the file must be formatted:
```
CURRENCY_PAIR,OPEN,LAST,BID,ASK,HIGH,LOW,VWAP,VOLUME,QUOTE_VOLUME,BID_SIZE,ASK_SIZE,TIMESTAMP
"BTC/USDT","0.00000001","0.00000002","0.00000003","0.00000004","0.00000005","0.00000006","0.00000007","0.00000008","0.00000009","0.00000010","0.00000011",1508546000
"BTC/USDT","1.00000001","1.00000002","1.00000003","1.00000004","1.00000005","1.00000006","1.00000007","1.00000008","1.00000009","1.00000010","1.00000011",1508446000
"ETH/USDT","2.00000001","2.00000002","2.00000003","2.00000004","2.00000005","2.00000006","2.00000007","2.00000008","2.00000009","2.00000010","2.00000011",1508346000
```

## When to initialize data?
In you strategy, you should implement the `initialize()` method. This method is executed by Cassandre before any other data (tickers, orders, trades...) is pushed to the strategy.

## Access your data in your strategy
In your strategy, you can access the data with two methods:
 * `List<TickerDTO> getImportedTickers()`.
 * `List<TickerDTO> getImportedTickers(CurrencyPairDTO currencyPairDTO)`.