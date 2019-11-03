# Endpoints

{% api-method method="get" host="https://api.0xtracker.com" path="/fills" %}
{% api-method-summary %}
Fills
{% endapi-method-summary %}

{% api-method-description %}
Returns a paginated collection of fills matching the specified parameters. Results are sorted from most recent to least recent. Please note that this endpoint will only return up to six months worth of transaction data.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Successful requests will return a paginated list of fills.
{% endapi-method-response-example-description %}

```javascript
{
    "fills": [
        {
            "assets": [],
            "date": "2019-11-03T18:22:06.000Z",
            "feeRecipient": "0x8124071f810d533ff63de61d0c98db99eeb99d64",
            "id": "5dbf1ae6aec0cb0004fef608",
            "makerAddress": "0x260e92d7b25c9315d068b2c3ca5f234d0cf9e505"
        },
        // ...
    ],
    "limit": 50, // The maximum number of fills returned
    "page": 1, // The current page
    "pageCount": 17221, // The total number of pages
    "total": 344408 // The total number of fills
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

