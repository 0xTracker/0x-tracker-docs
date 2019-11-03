# Endpoints

{% api-method method="get" host="https://api.0xtracker.com" path="/fills" %}
{% api-method-summary %}
Fills
{% endapi-method-summary %}

{% api-method-description %}
Returns a paginated collection of fills matching the specified parameters. Fills are sorted from most recent to least recent. Please note that this endpoint will only return up to six months worth of transaction data.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="relayer" type="string" required=false %}
ID of a relayer to filter fills by. Relayer IDs can be found by calling the relayers endpoint.
{% endapi-method-parameter %}

{% api-method-parameter name="token" type="string" required=false %}
Address of a token to filter fills by.
{% endapi-method-parameter %}

{% api-method-parameter name="limit" type="number" required=false %}
The maximum number of fills to return per page.   
_Default value is 20, maximum value is 50._
{% endapi-method-parameter %}

{% api-method-parameter name="page" type="number" required=false %}
The page of data to return.   
_Default value is 1._
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

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

{% hint style="info" %}
**Note:** it's currently not possible to filter fills by both relayer and token. Work is being done to make this possible in the future.
{% endhint %}

{% api-method method="get" host="https://api.0xtracker.com" path="/relayers" %}
{% api-method-summary %}
Relayers
{% endapi-method-summary %}

{% api-method-description %}
Returns a paginated collection of relayers and their associated stats for the specified time period. Relayers are returned in order of most trade volume to least trade volume.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="statsPeriod" type="string" required=false %}
The time period for which to return stats. Must be one of: day, week, month, year, all.   
_Default value is day \(24 hours\)._
{% endapi-method-parameter %}

{% api-method-parameter name="limit" type="number" required=false %}
The maximum number of relayers to return per page.   
_Default value is 20, maximum value is 50._
{% endapi-method-parameter %}

{% api-method-parameter name="page" type="number" required=false %}
The page of data to return.   
_Default value is 1._
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

