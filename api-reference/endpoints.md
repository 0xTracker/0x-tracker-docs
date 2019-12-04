# Endpoints

## Entities

{% api-method method="get" host="https://api.0xtracker.com" path="/article-sources" %}
{% api-method-summary %}
Article Sources
{% endapi-method-summary %}

{% api-method-description %}
Returns a collection of article sources which can be used to filter the articles endpoint.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
[
  {
    "name": "0x",
    "url": "https://0x.org",
    "imageUrl": "https://0xtracker.com/assets/logos/0x.png",
    "slug": "0x"
  },
  // ...
]
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.0xtracker.com" path="/articles" %}
{% api-method-summary %}
Articles
{% endapi-method-summary %}

{% api-method-description %}
Returns a paged collection of news articles matching the specified parameters. Articles are sorted from most recent to least recent.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="source" type="string" required=false %}
Slug of an article source to filter by.
{% endapi-method-parameter %}

{% api-method-parameter name="page" type="number" required=false %}
The page of data to return.  
_Default is 1._
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Returned when all parameters are valid.
{% endapi-method-response-example-description %}

```javascript
{
  "articles": [
    {
      "date": "2019-10-30T16:01:21.000Z",
      "id": "5db9b589ce5d870004529e18",
      "summary": "Announcing the upcoming 0x v3 vote",
      "title": "0x: The Community-owned Liquidity API",
      "url": "https://blog.0xproject.com/0x-the-community-owned-liquidity-api-26da5732447e?source=rss----86e37ca8e375---4",
      "source": {
        "name": "0x",
        "url": "https://0x.org",
        "imageUrl": "https://0xtracker.com/assets/logos/0x.png",
        "slug": "0x"
      }
    },
  ],
  "limit": 12,
  "page": 1,
  "pageCount": 40,
  "total": 473
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.0xtracker.com" path="/fills/:id" %}
{% api-method-summary %}
Fill
{% endapi-method-summary %}

{% api-method-description %}
Returns the full details of a single fill.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
ID of the fill to fetch.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Returned when the specified ID matches a valid fill.
{% endapi-method-response-example-description %}

```javascript
{
  "assets": [
    {
      "amount": "0.023595691875",
      "price": {
        "USD": 186.72
      },
      "tokenAddress": "0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2",
      "tokenSymbol": "WETH",
      "tokenType": "Wrapped Ether",
      "traderType": "maker",
      "type": "erc-20"
    },
    {
      "amount": "2041",
      "price": {
        "USD": 0.0021586416398334148
      },
      "tokenAddress": "0x503f9794d6a6bb0df8fbb19a2b3e2aeab35339ad",
      "tokenSymbol": "SBT",
      "tokenType": "Star Bit Token",
      "traderType": "taker",
      "type": "erc-20"
    }
  ],
  "date": "2019-11-04T18:26:05.000Z",
  "feeRecipient": "0x8124071f810d533ff63de61d0c98db99eeb99d64",
  "id": "5dc06d68ab099b000489d3fe",
  "makerAddress": "0xda912ecc847b3d98ca882e396e693e485deed518",
  "makerFee": {
    "USD": 0,
    "ZRX": "0"
  },
  "orderHash": "0x9165afe0f746839d2f390972b9a4473910143e6650be48477e7eb0196b607b02",
  "protocolVersion": 2,
  "relayer": {
    "slug": "star-bit",
    "name": "STAR BIT",
    "imageUrl": "https://0xtracker.com/assets/logos/starbit.png"
  },
  "senderAddress": "0x0681e844593a051e2882ec897ecd5444efe19ff2",
  "status": "successful",
  "takerAddress": "0x0681e844593a051e2882ec897ecd5444efe19ff2",
  "takerFee": {
    "USD": 0,
    "ZRX": "0"
  },
  "totalFees": {
    "USD": 0,
    "ZRX": "0"
  },
  "transactionHash": "0xc99fc0a2c65da2d3b94a1cd979afb05317203354a2dc6999c0dde26c61fecd0e",
  "value": {
    "USD": 4.4057875869
  }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
Returned when no fill can be found with the specified ID.
{% endapi-method-response-example-description %}

```javascript
{
  "errors": [
    {
      "code": "INVALID_URL",
      "status": 404,
      "title": "The requested URL is invalid."
    }
  ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.0xtracker.com" path="/fills" %}
{% api-method-summary %}
Fills
{% endapi-method-summary %}

{% api-method-description %}
Returns a paginated collection of fills matching the specified parameters. Fills are sorted from most recent to least recent.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="protocolVersion" type="number" required=false %}
Protocol version to filter by.
{% endapi-method-parameter %}

{% api-method-parameter name="relayer" type="string" required=false %}
ID of a relayer to filter by. Relayer IDs can be found by calling the relayers endpoint.
{% endapi-method-parameter %}

{% api-method-parameter name="token" type="string" required=false %}
Address of a token to filter by.
{% endapi-method-parameter %}

{% api-method-parameter name="limit" type="number" required=false %}
The maximum number of fills to return per page.   
_Default value is 20. Maximum value is 50._
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
Returned when all parameters are valid.
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
    "limit": 50,
    "page": 1,
    "pageCount": 17221,
    "total": 344408
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Returned when a parameter is invalid.
{% endapi-method-response-example-description %}

```javascript
{
  "errors": [
    {
      "code": "INVALID_PARAMETER",
      "message": "Invalid query parameter: relayer",
      "reason": "No relayer exists with an ID of \"fubar\"",
      "status": 400
    }
  ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% hint style="info" %}
**Notes:** 

This endpoint only returns up to six months of transaction data.

It's currently not possible to combine protocolVersion, relayer, and token parameters. Work is being done to make this possible in the future.
{% endhint %}

{% api-method method="get" host="https://api.0xtracker.com" path="/protocols" %}
{% api-method-summary %}
Protocols
{% endapi-method-summary %}

{% api-method-description %}
Returns a paginated collection of protocols matching the specified parameters.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="sortBy" type="string" required=false %}
The field by which to sort protocols. Must be one of: fillCount, fillVolume.  
_Default value is fillVolume._
{% endapi-method-parameter %}

{% api-method-parameter name="statsPeriod" type="string" required=false %}
The time period for which to return stats. Must be one of: day, week, month, year, all.  
_Default value is day._
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Returned when all parameters are valid.
{% endapi-method-response-example-description %}

```javascript
{
  "protocols": [
    {
      "stats": {
        "fillCount": 5385,
        "fillVolume": 1502594.5911382628
      },
      "version": 2
    },
    {
      "stats": {
        "fillCount": 2,
        "fillVolume": 20.2450049676
      },
      "version": 3
    }
  ],
  "page": 1,
  "pageCount": 1,
  "limit": 20,
  "total": 2
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Returned when a parameter is invalid.
{% endapi-method-response-example-description %}

```javascript
{
  "errors": [
    {
      "code": "INVALID_PARAMETER",
      "message": "Invalid query parameter: sortBy",
      "reason": "Must be one of: fillCount, fillVolume",
      "status": 400
    }
  ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.0xtracker.com" path="/relayers/:slug" %}
{% api-method-summary %}
Relayer
{% endapi-method-summary %}

{% api-method-description %}
Returns the details of a single relayer.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="slug" type="string" required=false %}
Slug of the relayer to fetch.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Returned when a relayer is found matching the specified slug.
{% endapi-method-response-example-description %}

```javascript
{
  "id": "radarRelay",
  "imageUrl": "https://0xtracker.com/assets/logos/radar-relay.png",
  "name": "Radar Relay",
  "slug": "radar-relay",
  "url": "https://radarrelay.com"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
Returned when no relayer can be found matching the specified slug.
{% endapi-method-response-example-description %}

```javascript
{
  "errors": [
    {
      "code": "INVALID_URL",
      "message": "The requested URL is invalid.",
      "status": 404
    }
  ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.0xtracker.com" path="/relayers" %}
{% api-method-summary %}
Relayers
{% endapi-method-summary %}

{% api-method-description %}
Returns a paginated collection of active relayers and their associated stats for the specified time period. Relayers are returned in order of most trade volume to least trade volume.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="statsPeriod" type="string" required=false %}
The time period for which to return stats. Must be one of: day, week, month, year, all.   
_Default value is day._
{% endapi-method-parameter %}

{% api-method-parameter name="limit" type="number" required=false %}
The maximum number of relayers to return per page.   
_Default value is 20. Maximum value is 50._
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
Returned when all parameters are valid.
{% endapi-method-response-example-description %}

```javascript
{
  "relayers": [
    {
      "id": "tokenlon",
      "imageUrl": "https://0xtracker.com/assets/logos/tokenlon.png",
      "name": "Tokenlon",
      "slug": "tokenlon",
      "stats": {
        "fillCount": 305,
        "fillVolume": 713586.326758335,
        "tradeCount": 305,
        "tradeVolume": 713586.326758335
      },
      "url": "https://tokenlon.token.im/tokenlon"
    },
    // ...
  ],
  "page": 1,
  "pageCount": 1,
  "limit": 20,
  "total": 10
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Returned when a parameter is invalid.
{% endapi-method-response-example-description %}

```javascript
{
  "errors": [
    {
      "code": "INVALID_PARAMETER",
      "message": "Invalid statsPeriod parameter: fubar",
      "reason": "Must be one of: day, week, month, year, all",
      "status": 400
    }
  ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.0xtracker.com" path="/tokens/:address" %}
{% api-method-summary %}
Token
{% endapi-method-summary %}

{% api-method-description %}
Returns the full details of a single token.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="address" type="string" required=true %}
Address of the token to fetch.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Returned when a token is found matching the specified address.
{% endapi-method-response-example-description %}

```javascript
{
  "address": "0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2",
  "imageUrl": "https://cdn.staticaly.com/gh/TrustWallet/tokens/master/tokens/0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2.png",
  "lastTrade": {
    "id": "5dc06f57ab099b00048e0737",
    "date": "2019-11-04T18:34:26.000Z"
  },
  "name": "Wrapped Ether",
  "price": {
    "last": 186.72
  },
  "symbol": "WETH",
  "type": "erc-20"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
Returned when no token can be found matching the specified address.
{% endapi-method-response-example-description %}

```javascript
{
  "errors": [
    {
      "code": "INVALID_URL",
      "status": 404,
      "title": "The requested URL is invalid."
    }
  ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.0xtracker.com" path="/tokens" %}
{% api-method-summary %}
Tokens
{% endapi-method-summary %}

{% api-method-description %}
Returns a paginated collection of traded tokens and their associated stats for the specified time period. Tokens are returned in order of most fill volume to least fill volume.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="type" type="string" required=false %}
The type of tokens to return. Must be one of: erc-20, erc-721.
{% endapi-method-parameter %}

{% api-method-parameter name="statsPeriod" type="string" required=false %}
The time period for which to return stats. Must be one of: day, week, month, year, all.  
_Default value is day._
{% endapi-method-parameter %}

{% api-method-parameter name="limit" type="number" required=false %}
The maximum number of tokens to return per page.  
_Default value is 20. Maximum value is 50._
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
Returned when all parameters are valid.
{% endapi-method-response-example-description %}

```javascript
{
  "tokens": [
    {
      "address": "0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2",
      "imageUrl": "https://raw.githubusercontent.com/TrustWallet/tokens/master/tokens/0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2.png",
      "lastTrade": {
        "id": "5dc06f57ab099b00048e0737",
        "date": "2019-11-04T18:34:26.000Z"
      },
      "name": "Wrapped Ether",
      "price": {
        "last": 186.72
      },
      "symbol": "WETH",
      "stats": {
        "fillCount": 1067,
        "fillVolume": {
          "token": "4214.4828876902467",
          "USD": 776534.3341971342
        }
      },
      "type": "erc-20"
    },
    // ...
  ],
  "page": 1,
  "pageCount": 3,
  "limit": 20,
  "total": 45
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Returned when a parameter is invalid.
{% endapi-method-response-example-description %}

```javascript
{
  "errors": [
    {
      "code": "INVALID_PARAMETER",
      "message": "Invalid statsPeriod parameter: fubar",
      "reason": "Must be one of: day, week, month, year, all",
      "status": 400
    }
  ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.0xtracker.com" path="/traders" %}
{% api-method-summary %}
Traders
{% endapi-method-summary %}

{% api-method-description %}
Returns a paginated collection of active traders and their associated stats for the specified time period. Traders are returned in order of most fill volume to least fill volume.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="type" type="string" required=false %}
The type of traders to return. Must be one of: maker, taker.
{% endapi-method-parameter %}

{% api-method-parameter name="excludeRelayers" type="boolean" required=false %}
Whether to exclude relayer taker addresses from the results.  
_Default is true._
{% endapi-method-parameter %}

{% api-method-parameter name="statsPeriod" type="string" required=false %}
The time period for which to return stats. Must be one of: day, week, month, year, all.  
_Default value is day._
{% endapi-method-parameter %}

{% api-method-parameter name="limit" type="number" required=false %}
The maximum number of traders to return per page.  
_Default value is 20. Maximum value is 50._
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
Returned when all parameters are valid.
{% endapi-method-response-example-description %}

```javascript
{
  "page": 1,
  "pageCount": 6,
  "limit": 20,
  "total": 119,
  "traders": [
    {
      "address": "0x41f8d14c9475444f30a80431c68cf24dc9a8369a",
      "stats": {
        "fillCount": {
          "maker": 0,
          "taker": 259,
          "total": 259
        },
        "fillVolume": {
          "maker": 0,
          "taker": 496613.5857697289,
          "total": 496613.5857697289
        }
      }
    },
    // ...
  ]
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Returned when a parameter is invalid.
{% endapi-method-response-example-description %}

```javascript
{
  "errors": [
    {
      "code": "INVALID_PARAMETER",
      "message": "Invalid statsPeriod parameter: fubar",
      "reason": "Must be one of: day, week, month, year, all",
      "status": 400
    }
  ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Metrics

{% api-method method="get" host="https://api.0xtracker.com" path="/metrics/network" %}
{% api-method-summary %}
Network Metrics
{% endapi-method-summary %}

{% api-method-description %}
Returns a collection of network metrics for the specified time period.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="period" type="string" required=false %}
Time period for which to return metrics. Must be one of: day, week, month, year, all.  
_Default value is month._
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Returned when all parameters are valid.
{% endapi-method-response-example-description %}

```javascript
[
  {
    "date": "2019-10-05T00:00:00.000Z",
    "fees": {
      "USD": 0,
      "ZRX": "0"
    },
    "fillCount": 1383,
    "fillVolume": 929465.5342802514,
    "protocolFees": {
      "ETH": "152.8",
      "USD": 22920
    }
  },
  {
    "date": "2019-10-06T00:00:00.000Z",
    "fees": {
      "USD": 0,
      "ZRX": "0"
    },
    "fillCount": 1624,
    "fillVolume": 595794.5615575106,
    "protocolFees": {
      "ETH": "167",
      "USD": 25050
    }
  },
  // ...
]
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Returned when a parameter is invalid.
{% endapi-method-response-example-description %}

```javascript
{
  "errors": [
    {
      "code": "INVALID_PARAMETER",
      "message": "Invalid period parameter: fubar",
      "reason": "Must be one of: day, week, month, year, all",
      "status": 400
    }
  ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.0xtracker.com" path="/metrics/relayer" %}
{% api-method-summary %}
Relayer Metrics
{% endapi-method-summary %}

{% api-method-description %}
Returns a collection of metrics for the specified relayer and time period.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="relayer" type="string" required=true %}
Id of the relayer to fetch metrics for.
{% endapi-method-parameter %}

{% api-method-parameter name="period" type="string" required=false %}
Time period for which to return metrics. Must be one of: day, week, month, year, all.  
_Default value is month._
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Returned when all parameters are valid.
{% endapi-method-response-example-description %}

```javascript
[
  {
    "date": "2019-10-09T00:00:00.000Z",
    "fees": {
      "USD": 0,
      "ZRX": "0"
    },
    "fillCount": 505,
    "fillVolume": 804818.3748855987,
    "tradeCount": 505,
    "tradeVolume": 804818.3748855987
  },
  {
    "date": "2019-10-10T00:00:00.000Z",
    "fees": {
      "USD": 0,
      "ZRX": "0"
    },
    "fillCount": 613,
    "fillVolume": 786533.7512397981,
    "tradeCount": 613,
    "tradeVolume": 786533.7512397981
  },
  // ...
]
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Returned when an invalid query parameter is provided.
{% endapi-method-response-example-description %}

```javascript
{
  "errors": [
    {
      "code": "INVALID_PARAMETER",
      "message": "Invalid query parameter: relayer",
      "reason": "No relayer exists with an ID of \"fubar\"",
      "status": 400
    }
  ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.0xtracker.com" path="/metrics/token" %}
{% api-method-summary %}
Token Metrics
{% endapi-method-summary %}

{% api-method-description %}
Returns a collection of metrics for the specified token and time period.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="token" type="string" required=true %}
Address of the token to fetch metrics for.
{% endapi-method-parameter %}

{% api-method-parameter name="period" type="string" required=false %}
Time period for which to return metrics. Must be one of: day, week, month, year, all.  
_Default value is month._
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Returned when all parameters are valid.
{% endapi-method-response-example-description %}

```javascript
[
  {
    "date": "2019-10-05T00:00:00.000Z",
    "fillCount": 241,
    "fillVolume": {
      "token": "492473.991404",
      "USD": 495067.7333900565
    }
  },
  {
    "date": "2019-10-06T00:00:00.000Z",
    "fillCount": 192,
    "volume": {
      "token": "262563.466067",
      "USD": 263534.0645080984
    }
  },
  // ...
]
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Returned when a parameter is invalid.
{% endapi-method-response-example-description %}

```javascript
{
  "errors": [
    {
      "code": "MISSING_PARAMETER",
      "message": "Missing query parameter: token",
      "reason": "Parameter must be provided",
      "status": 400
    }
  ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.0xtracker.com" path="/metrics/trader" %}
{% api-method-summary %}
Trader Metrics
{% endapi-method-summary %}

{% api-method-description %}
Returns a collection of metrics for the specified trader and time period.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="address" type="string" required=true %}
Address of the trader to fetch metrics for.
{% endapi-method-parameter %}

{% api-method-parameter name="period" type="string" required=false %}
Time period for which to return metrics. Must be one of: day, week, month, year, all.  
_Default value is month._
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Returned when all parameters are valid.
{% endapi-method-response-example-description %}

```javascript
[
  {
    "date": "2019-10-05T00:00:00.000Z",
    "fillCount": {
      "maker": 16,
      "taker": 0,
      "total": 16
    },
    "fillVolume": {
      "maker": 72991.34822187197,
      "taker": 0,
      "total": 72991.34822187197
    }
  },
  {
    "date": "2019-10-06T00:00:00.000Z",
    "fillCount": {
      "maker": 10,
      "taker": 0,
      "total": 10
    },
    "fillVolume": {
      "maker": 45067.52037545083,
      "taker": 0,
      "total": 45067.52037545083
    }
  },
  // ...
]
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Returned when a parameter is invalid.
{% endapi-method-response-example-description %}

```javascript
{
  "errors": [
    {
      "code": "MISSING_PARAMETER",
      "message": "Missing query parameter: address",
      "reason": "Parameter must be provided",
      "status": 400
    }
  ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Stats

{% api-method method="get" host="https://api.0xtracker.com" path="/stats/network" %}
{% api-method-summary %}
Network Stats
{% endapi-method-summary %}

{% api-method-description %}
Returns network stats for the specified time period.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="period" type="string" required=false %}
Time period for which to return stats. Must be one of: day, week, month, year, all.  
_Default value is day._
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Returned when all parameters were valid.
{% endapi-method-response-example-description %}

```javascript
{
  "fees": {
    "USD": 0,
    "ZRX": "0"
  },
  "fillCount": 1215,
  "fillVolume": 1424278.9861453106,
  "protocolFees": {
    "ETH": "221.8",
    "USD": 33270
  },
  "tradeCount": 887,
  "tradeVolume": 1408589.3708279347
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Returned when a parameter is invalid.
{% endapi-method-response-example-description %}

```javascript
{
  "errors": [
    {
      "code": "INVALID_PARAMETER",
      "message": "Invalid period parameter: fubar",
      "reason": "Must be one of: day, week, month, year, all",
      "status": 400
    }
  ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://api.0xtracker.com" path="/stats/trader" %}
{% api-method-summary %}
Trader Stats
{% endapi-method-summary %}

{% api-method-description %}
Returns trader stats for the specified time period.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="period" type="string" required=false %}
Time period to return stats for. Must be one of: day, week, month, year, all.  
_Default value is day._
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Returned when all parameters are valid.
{% endapi-method-response-example-description %}

```javascript
{
  "makerCount": 68,
  "takerCount": 53,
  "traderCount": 116
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Returned when a parameter is invalid.
{% endapi-method-response-example-description %}

```javascript
{
  "errors": [
    {
      "code": "INVALID_PARAMETER",
      "message": "Invalid period parameter: fubar",
      "reason": "Must be one of: day, week, month, year, all",
      "status": 400
    }
  ]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

