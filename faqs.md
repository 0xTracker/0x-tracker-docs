# FAQs

## What is a fill?

Traders on the 0x protocol broadcast their intent to trade via orders. When another party is interested in fulfilling some, or all of the requirements of that order, they are said to "fill" the order. Filling an order \(even partially\) will emit a fill event. It is these fill events which 0x Tracker monitors to understand trading activity.

## What is the difference between "fill" and "trade" volume?

Two parties are involved when the exchange of assets \(an order fill\) occurs on the 0x protocol, the maker and the taker. Depending on the [relayer strategy](https://0x.org/docs/guides/relayer-strategies) being used these parties may represent both traders or they may represent a trader and a relayer. Because of this, a trade may actually involve more than one fill event.

In a simple relayer scenario we have two parties who wish to exchange $1,000 worth of assets. An order is created by the maker, and the taker fills the order. The trade is complete, a single fill event is emitted, and the value of the fill can be calculated as $1,000. This contributes $1,000 to the total `fill volume` and $1,000 to the total `trade volume`.

In another relayer scenario, the taker of an order is the relayer, not the party interested in filling the order. Two fill events are emitted in this instance, one for each trading party. The end result is that $1,000 of assets have been exchanged BUT we have got two fill events which are both valued at $1,000. This results in $2,000 of `fill volume` but only $1,000 of `trade volume`.

Fill volume can therefore be understood as the value of all asset exchange facilitate by 0x. Trade volume is the value of actual trading activity facilitated by 0x.

{% hint style="info" %}
Trade volume can only be calculated for fill events originating from a known relayer. This is because we can only reliably calculate trade volume when we understand the strategy in use by a given relayer. Because of this constraint, there may be unidentified trade volume which is not accounted for due to a relayer not having been identified yet.
{% endhint %}

## How are relayers identified for fill events?

Relayers are associated with a given fill by matching either the `fee recipient` or the `taker address` of the fill with a predefined registry of known relayers.

## Where are token prices derived from?

Token prices are derived for any fill involving a trusted base token. These base tokens are currently: DAI, ETH, USDC, and USDT. If a fill does not involve one of these tokens then the assets within it will not have their prices derived and the value of the fill will be unknown. There are also a couple of other conditions:

* If an asset belonging to a fill has not been identified then we cannot calculate its price. This is because the exchanged amount of that asset will also be unknown.
* Both parties in the exchange must be exchanging a single type of asset. For example, if the fill involves the exchange of 1 ETH for 300 ZRX & 100 BAT then we cannot know the value of ZRX or BAT. This is because we don't know which portion of the order value each asset relates to.

Assuming we have a fill which satisfies the required criteria \(e.g. 2 ETH for 1,200 ZRX\) then we fetch the price of the base token at the time the fill occurred. This price is used to calculate the fill value and we then use the fill value to calculate the price of the other asset.

In our example of 2 ETH for 1,200 ZRX we would fetch the ETH price since it is the trusted base token. Lets say the price is $180 at the time of exchange. We would then calculate that the fill value is $360 \(2 ETH x $180\). We use this value to calculate a price of $0.30 for the ZRX assets \($360 / 1,200 ZRX\).

### Where are base token prices fetched from?

Base token prices are fetched from the [CryptoCompare API](https://min-api.cryptocompare.com/). This data source has proven reliable but could be replaced for decentralised price oracles when they become available.

### What happens if a fill involves two base tokens?

When the fill involves two base tokens we follow the same method detailed above but the base token for a fill is determined in the following order: DAI, USDC, USDT, ETH. This order deliberately gives preference to stable coins due to their lack of volatility.

## How can I get my 0x relayer listed on 0x Tracker?

If your relayer is not listed yet then please [fill out this form](https://0xtracker.typeform.com/to/wXA7tZ) to submit your details.

## How can I get my token listed on 0x Tracker?

Token information is automatically sourced from [Ethplorer](https://ethplorer.io) which means you do not need to submit tokens directly to 0x Tracker. If you notice that information is missing for a particular token please follow these steps:

* Check whether the token information is available on Ethplorer using their search.
* If the token information is on Ethplorer then please [file a bug](https://github.com/0xTracker/0x-tracker-worker/issues/new) on the 0x Tracker GitHub.
* If the token information is missing from Ethplorer please fill out their [contact form](https://docs.google.com/forms/d/e/1FAIpQLSfJ8m5n1HDw28-WCrATm8wriEutJDUq8KAVrLwO2WNeKrwFGA/viewform).

{% hint style="info" %}
0x Tracker only displays tokens which have been traded on the 0x protocol.
{% endhint %}

## How can I trust the information being reported?

All of the code behind 0x Tracker is open source and available to inspect on [GitHub](https://github.com/0xTracker). This helps to provide an end-to-end understanding of how data is collected, processed and served.

Unfortunately it is not currently possible to provide proof that this code is actually being used in production. If you want to verify that the data being served on 0xtracker.com is not being tampered with in some way then you are welcome to run the project yourself. By running the project you can reproduce the data set for comparison against 0x Tracker.

## My question is not listed here. How can I get in touch?

For general enquiries the best way to get in touch is [hello@0xtracker.com](mailto:hello@0xtracker.com). Alternatively you can reach out to [@0xTracker](https://twitter.com/0xtracker) on Twitter.

