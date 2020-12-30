# FAQs

## Where are token prices derived from?

Token prices are derived for any trade involving a trusted base token. These base tokens are currently: DAI, ETH, USDC, ZRX, WBTC, TUSD and USDT. If a trade does not involve one of these tokens then the assets within it will not have their prices derived and the value of the fill will be unknown. There are also a couple of other conditions:

* If an asset belonging to a trade has not been identified then we cannot calculate its price. This is because the exchanged amount of that asset will also be unknown.
* Both parties in the exchange must be exchanging a single type of asset. For example, if the trade involves the exchange of 1 ETH for 300 ZRX & 100 BAT then we cannot know the value of ZRX or BAT. This is because we don't know which portion of the trade value each asset relates to.

Assuming we have a trade which satisfies the required criteria \(e.g. 2 ETH for 1,200 ZRX\) then we fetch the price of the base token at the time the trade occurred. This price is used to calculate the trade value and we then use the trade value to calculate the price of the other asset.

In our example of 2 ETH for 1,200 ZRX we would fetch the ETH price since it is the trusted base token. Lets say the price is $180 at the time of exchange. We would then calculate that the trade value is $360 \(2 ETH x $180\). We use this value to calculate a price of $0.30 for the ZRX assets \($360 / 1,200 ZRX\).

### Where are base token prices fetched from?

Base token prices are fetched from the [CryptoCompare API](https://min-api.cryptocompare.com/). This data source has proven reliable but could be replaced for decentralised price oracles when they become available.

### What happens if a trade involves two base tokens?

When the trade involves two base tokens we follow the same method detailed above but the base token for a trade is determined in the following order: DAI, USDC, USDT, TUSD, ETH, ZRX, WBTC. This order deliberately gives preference to stable coins due to their lack of volatility.

## How can I get my 0x app listed on 0x Tracker?

If your 0x-based app is not listed yet then please [fill out this form](https://0xtracker.typeform.com/to/wXA7tZ) to submit your details.

## How can I get my token listed on 0x Tracker?

Token information is automatically sourced from [Ethplorer](https://ethplorer.io) and token contracts which means you do not need to submit tokens directly to 0x Tracker. If you notice that information is missing for a particular token please follow these steps:

* Check whether the token contract exposes decimals, name, and symbol values.
* Check whether the token information is available on Ethplorer using their search.
* If the token information is available in the token contract or on Ethplorer then please [file a bug](https://github.com/0xTracker/0x-tracker-worker/issues/new) on the 0x Tracker GitHub.
* If the token information is missing from Ethplorer please fill out their [contact form](https://docs.google.com/forms/d/e/1FAIpQLSfJ8m5n1HDw28-WCrATm8wriEutJDUq8KAVrLwO2WNeKrwFGA/viewform).

{% hint style="info" %}
0x Tracker only displays Ethereum-based tokens which have been traded using 0x.
{% endhint %}

## How can I trust the information being reported?

All of the code behind 0x Tracker is open source and available to inspect on [GitHub](https://github.com/0xTracker). This helps to provide an end-to-end understanding of how data is collected, processed and served.

If you want to verify that the data being served on 0xtracker.com is not being tampered with in some way then you are welcome to run the project yourself. By running the project you can reproduce the data set for comparison against 0x Tracker.

## My question is not listed here. How can I get in touch?

For general enquiries the best way to get in touch is [hello@0xtracker.com](mailto:hello@0xtracker.com). Alternatively you can reach out to [@0xTracker](https://twitter.com/0xtracker) on Twitter.

