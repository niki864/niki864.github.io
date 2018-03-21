---
priority: 0.7
title: Sentiment Analysis of Cryptocurrency Tweets
excerpt: A simple sentiment analyser for tweets related to cryptocurrencies
categories: works
background-image: bitcoin.jpg
tags:
  - RStudio
  - TwitteR
  - Plyr
  - ggplot2
---

# Sentiment Analysis of Tweets Related to Cryptocurrencies

I built a simple sentiment analyser that pulls tweets from Twitter and assigns it a sentiment score. Created this during the crypto hype of 2017 Aug-Dec where volatility was excessive and nearly everyone on social media became a self professed cryptocurrency expert. I thought it might be interesting to see what it is that they are actually saying (and hopefully make use of that for my personal portfolio :P)

## Packages Required

TwitteR, plyr, stringr, ggplot2, downloadable from CRAN

### Prerequisites

R and R Studio

## Dataset Description

All of this data is aggregated from Twitter using the TwitteR search api call. 
Here we search for the term "#Cryptocurrency" and look for the most recent 1500 tweets.(Unfortunately, that is Twitter's max. free limit)
This is raw tweet data as provided by the returned Json file.

After aggregating this data, data cleaning is done to remove repeat tweets, unnecessary characters, numbers, non-english words, twitter symbols like @ RT and # to get raw text of tweets. That removes around 35-40% of the data. So we effectively have around 800-900 tweets to work with.
I used simple Regex rules based matching to clean data.

## Sentiment Analyser Description

This is a simple analyser function that increments or decrements points to a sentence based on words in the sentence that are matched to a positive or negative word list. It's not a very elegant implementation but it gets the job done.

This follows the tutorial at http://jeffreybreen.wordpress.com/2011/07/04/twitter-text-mining-r-slides/ 

The scores are then stored and used to generate graph plots based on sentiment score. 

## Summary

Here ares some histogram models generated using ggplot based on the sentiment score of the overall dataset.

![alt tag](https://user-images.githubusercontent.com/10093954/34191361-5422d620-e514-11e7-9681-c36ce0085d80.jpeg)

After which, I applied the same logic for the search term #Bitcoin alone
Then we do the same for the term Bitcoin alone.

![alt tag](https://user-images.githubusercontent.com/10093954/34191362-5443caf6-e514-11e7-93a0-4ac6148bfa59.jpeg)

Likewise for Ethereum

![alt tag](https://user-images.githubusercontent.com/10093954/34191363-5466418a-e514-11e7-95d3-33919e847b8c.jpeg)

Likewise for Litecoin

![alt tag](https://user-images.githubusercontent.com/10093954/34191364-5499741a-e514-11e7-8c90-c5fe4be3f759.jpeg)

## Feedback

Contact me for any feedback regarding this project. Always eager to hear from fellow data enthusiasts.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* https://github.com/benmarwick/AAA2011-Tweets
