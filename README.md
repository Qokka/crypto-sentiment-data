# Crypto Sentiment Data

by [Qokka Inc](https://qokka.ai)

## Data

In Qokka | Crypto ([https://crypto.qokka.com](https://crypto.qokka.com)), we continuously analyze community discussions from Reddit and Telegram for over 1500+ blockchain projects. We include a community only if it is well established (e.g. /r/bitcoin on Reddit) or is officially managed by the project (e.g. https://t.me/algorand on Telegram). We use third-party data sources such as Coinmarketcap to verify some information. 

Most projects only have one active community. For example, Bitcoin only has Reddit. Some projects have both Reddit community and an active Telegram group (e.g. EOS). 


### 2019-daily-sentiment-price
This is the first dataset we release. It includes sentiment and price data in 2019, for most cryptocurrencies that are 

1. Listed on Coinbase, or
2. Has a high market cap, and an active community for 2+ years

The data for each crypto and each community (Reddit / Telegram) is put in separate files. All files are in CSV format.

#### Data fields

Each row represents a time range. Here are the definitions of each field. For price related fields, the value is aggregated across some reliable external data sources we use, which aggregate some top exchanges. All sentiment related fields are computed using our own algorithms, based on raw data we collected by ourselves.

General fields

- **cryptoId**: The ticker symbol of the crypto. We use tickers on [Coinmarketcap](https://coinmarketcap.com). Example: btc
- **start**: The millisecond timestamp for each row, indicating the starting time of a time range. Example: 1585297985477
- **duration**: The duration of the time range in milliseconds. Example: 86400000

Price related fields

- **open**: The opening price for the time range.
- **close**: The closing price for the time range.
- **high**: The highest price for the time range.
- **low**: The lowest price for the time range.
- **volumeUSD**: The trading volume in USD for the time range.

Sentiment related fields

- **source**: The source of the community discussion data which the sentiments are computed upon.
- **count**: The number of discussions used to compute the sentiments. They can be posts, comments, or a chat message. Garbage discussions are excluded (e.g. a meme message with no text)
- **average**: The average sentiment value for all discussions in the time range, where each discussion's sentiment is predicated to be between 1-5 (with 3 as neutral) 
- **std**: The standard deviation of the sentiments across all discussions in the time range.
- **positive**: Estimated percentage of relatively positive discussions in this time range.
- **negative**: Estimated percentage of relatively negative discussions in this time range.
- **score**: An adjusted sentiment score we computed for this time range. It is always between [0, 1]. We use a methodology that is designed to give higher score when proportion of positive discussions are high, and is less sensitive to overwhelming negative discussions. It shows many desirable statistical properties such as a empirical distribution with nicely spread and reasonable mean, among other things.
 
## Coming soon

We have live data for  Hourly data, more cryptocurrencies, and more sources. 

Please let us know what you need and we will definitely consider them when we release the next dataset!

## Q & A

Please feel free to reach out to our team at [team@qokka.ai](mailto:team@qokka.ai) if you have any questions. We will put answers to commonly asked questions here.

## Community

Join [our Slack community](https://qokka.typeform.com/to/T1W0eF), or [our Discord server](https://discord.gg/UyrH3QK). We are there to help you.

## License

The data under this repository is licensed under the terms of [Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International License](https://creativecommons.org/licenses/by-nc-nd/4.0/).