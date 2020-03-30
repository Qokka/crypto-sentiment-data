# Cryptocurrency Sentiment Data

by [Qokka Team](https://qokka.ai)

## Introduction


In Qokka | Crypto ([https://crypto.qokka.com](https://crypto.qokka.com/)), we continuously analyze community discussions from Reddit and Telegram for over 1500+ blockchain projects which have tradable cryptocurrencies. We include a community only if it is well established (e.g. /r/bitcoin on Reddit) or is officially managed by the project (e.g. [https://t.me/algorand](https://t.me/algorand) on Telegram). We use third-party data sources such as Coinmarketcap to collect and verify the status of the communities..

Most projects only have one active community. For example, Bitcoin only has Reddit. Some projects have both a Reddit community and an active Telegram group (e.g. EOS). 

## Data

### Methodology
#### Data Collection
We are one of the very few collecting authentic community discussion data on Reddit and Telegram. Whereas others only include Twitter data. As we all know that blockchain and cryptocurrency communities are mostly on Reddit, Telegram and Discord (coming soon). 

We built our own large scale real time crawl to collect all relevant data on various community platforms. 

#### Data Cleaning
We only analyze informative discussion data, uninformative data, such as memes and emojis, are excluded. We also transform discussion data into a format that emphasiezs more than what and how things are described and discussed. 

#### Data Analysis
Same as the crawlers, we also built our own systems, algorithms and machine learning models for sentiment analysis, topic modeling and interest profiling. Whereaes others are relying on third-party services, such as IBM Watson, Google NLP, Amazon Comprehend and Social Market Analytics, which are not designed for analyzing conversational community discussions. 
 
For sentiment analysis:
1. We train our models using data where labels are readily available.

2. We use deep learning methods that recognize semantic compositions in sentences.

3. We predict sentiment of each sentence using 5 classes with a score of 1 to 5: very negative, negative, neutral, positive, very positive. This means our methods won't just look out for keywords in sentences (e.g. good, bad, great). Instead, it looks at the overall structure and relationships between the words to some extent, and in principle shouldn't be confused by complex structures like double negative. However it may still be confused in less common cases (e.g. sacarcisms). 

4. We then combine the scores of sentences into a score between 1 to 5 for the discussion. 

5. In the end, when we compute the sentiment for a time range (e.g. for an hour), we use a combination of metrics (e.g. positive percentage, negative percentage, number of discussions) and compute a score between 0 to 1. Note that, this score is not normalized across cryptocurrencies, or across different time ranges for one cryptocurrency. We leave that at the discretion of our users since they might need the flexibility to normalize the scores differently.


### Dataset: 2019-daily-sentiment-price

This is the first dataset we release. It includes sentiment and price data in 2019, for most cryptocurrencies that are 

1. Listed on Coinbase, or
2. Has a high market cap, and an active community for 2+ years

The data for each crypto and each community (Reddit / Telegram) is put in separate files. All files are in CSV format.

#### Data fields

Each row represents a time range. Here are the definitions of each field. For price related fields, the value is aggregated across some reliable external data sources we use, which aggregate some top exchanges. All sentiment related fields are computed using our own algorithms, based on raw data we collected by ourselves.

**General fields**

- **cryptoId**: The ticker symbol of the crypto. We use tickers on [Coinmarketcap](https://coinmarketcap.com). Example: btc
- **start**: The millisecond timestamp for each row, indicating the starting time of a time range. Example: 1585297985477
- **duration**: The duration of the time range in milliseconds. Example: 86400000

Price related fields

- **open**: The opening price for the time range.
- **close**: The closing price for the time range.
- **high**: The highest price for the time range.
- **low**: The lowest price for the time range.
- **volumeUSD**: The trading volume in USD for the time range.

**Sentiment related fields**

- **source**: The source of the community discussion data which the sentiments are computed upon.
- **count**: The number of discussions used to compute the sentiments. They can be posts, comments, or a chat message. Garbage discussions are excluded (e.g. a meme message with no text)
- **average**: The average sentiment value for all discussions in the time range, where each discussion's sentiment is predicted to be between 1-5 (with 3 as neutral) 
- **std**: The standard deviation of the sentiments across all discussions in the time range.
- **positive**: Estimated percentage of relatively positive discussions in this time range.
- **negative**: Estimated percentage of relatively negative discussions in this time range.
- **score**: An adjusted sentiment score we computed for this time range. It is always between [0, 1]. We use a methodology that is designed to give higher scores when the proportion of positive discussions are high, and is less sensitive to overwhelming negative discussions. It shows many desirable statistical properties such as an empirical distribution with nicely spread and reasonable mean, among other things.
 

## About us

Our team has been working on machine learning research, engineering, and product design and management since 2012. We have been working on cryptocurrency related products since 2017. To learn more about us, please check out [our website](https:// qokka.ai)

## FAQ

Q1: Do you have data with higher resolution, and for more cryptocurrencies?

We may release higher resolution data soon for a limited subset of cryptocurrencies, but you can also get it from Qokka | Crypto ([https://crypto.qokka.com](https://crypto.qokka.com/)), especially if you want to build something for commercial purposes. It offers the data for all cryptocurrencies (1500+) we track. If you need some customizations, please feel free to contact us. 

Q2: Can I use this data for commercial purposes?

Under the license terms, you cannot. If you need a commerce license, please contact us at [team@qokka.ai](mailto:team@qokka.ai), or sign up for an API plan at Qokka | Crypto ([https://crypto.qokka.com](https://crypto.qokka.com/)). Feel free to be creative and experiment with the data, for example: building a trading bot, backtesting your algorithms, writing an article about sentiments of cryptocurrency landscape, as long as you attribute us when you publish your work. It is our understanding that these use cases are not limited by the "non-derivative" part of the license terms, since you would be creating essentially a new body of work, and you would not mix in our data when you publish your work. 


Please feel free to contact us at [team@qokka.ai](mailto:team@qokka.ai) if you have any other questions.

## Community

Please join our [Slack](https://qokka.typeform.com/to/T1W0eF) or [Discord](https://discord.gg/UyrH3QK) community. We are here to help.

## License

The data under this repository is licensed under the terms of [Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International License](https://creativecommons.org/licenses/by-nc-nd/4.0/).

