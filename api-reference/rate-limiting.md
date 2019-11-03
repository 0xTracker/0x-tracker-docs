# Rate Limiting

Rate limiting is used by the API to prevent abuse and ensure a reliable experience for all consumers. The current limit is 250 requests to all endpoints in a given five minute time period. The limit is non-accruing and resets every five minutes.

If you require a more generous limit then please get in touch via [hello@0xtracker.com](mailto:hello@0xtracker.com) to discuss your use case.

{% hint style="info" %}
Please note that the API is not intended to be used for scraping transaction data. If you require offline access to all transaction data then please run the [0x Event Extractor](https://github.com/0xtracker/0x-event-extractor) and [0x Tracker Worker](https://github.com/0xtracker/0x-tracker-worker) applications yourself.
{% endhint %}

