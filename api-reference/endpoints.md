# Endpoints

## Entities

{% api-method method="get" host="https://api.0xtracker.com" path="/apps/:slug" %}
{% api-method-summary %}
App
{% endapi-method-summary %}

{% api-method-description %}
Returns the details and stats of a single app.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="slug" type="string" required=false %}
Slug of the app to fetch.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter name="statsPeriodTo" type="string" required=false %}
End of the time period for which to return stats. Should be used as an alternative to the statsPeriod parameter. Must be in the format YYYY-MM-DD.
{% endapi-method-parameter %}

{% api-method-parameter name="statsPeriodFrom" type="string" required=false %}
Start of the time period for which to return stats. Should be used as an alternative to the statsPeriod parameter. Must be in the format YYYY-MM-DD.
{% endapi-method-parameter %}

{% api-method-parameter name="statsPeriod" type="string" required=false %}
The time period for which to return stats. Valid values are: "day", "week", "month", "year" and "all".  
_Default value is "day"._
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Returned when an app is found matching the specified slug.
{% endapi-method-response-example-description %}

```javascript
{
  "categories": [
    "dex-aggregator",
    "relayer"
  ],
  "description": "Built by the 0x core team – Matcha is a DEX aggregator built on top of 0x API which allows users to easily swap tokens and place limit orders.",
  "id": "5067df8b-f9cd-4a34-aee1-38d607100145",
  "logoUrl": "https://cdn.staticaly.com/gh/0xTracker/0x-tracker-worker/master/src/attributions/logos/matcha.png",
  "name": "Matcha",
  "stats": {
    "activeTraders": 2018,
    "activeTradersChange": -28.768090363572185,
    "avgTradeSize": 6993.46645518334,
    "avgTradeSizeChange": 109.03017173450618,
    "tradeCount": {
      "relayed": 94,
      "total": 3034
    },
    "tradeCountChange": {
      "relayed": 80.76923076923077,
      "total": -22.72032603158431
    },
    "tradeVolume": {
      "relayed": 2725771.217305796,
      "total": 21183209.892750338
    },
    "tradeVolumeChange": {
      "relayed": 273.2930045664127,
      "total": 61.477273701560634
    }
  },
  "urlSlug": "matcha",
  "websiteUrl": "https://matcha.xyz"
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

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
Returned when no app can be found matching the specified slug.
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

{% api-method method="get" host="https://api.0xtracker.com" path="/apps" %}
{% api-method-summary %}
Apps
{% endapi-method-summary %}

{% api-method-description %}
Returns a paginated collection of active apps and their associated stats for the specified time period.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="sortDirection" type="string" required=false %}
The direction in which to sort results Valid values are "asc" and "desc".  
_Default value is "desc"._
{% endapi-method-parameter %}

{% api-method-parameter name="sortBy" type="string" required=false %}
The field by which to sort results. Valid values are: "activeTraders", "tradeCount" and "tradeVolume".  
_Default value is "tradeVolume"._
{% endapi-method-parameter %}

{% api-method-parameter name="statsPeriod" type="string" required=false %}
The time period for which to return stats. Valid values are: "day", "week", "month", "year" and "all".  
_Default value is "day"._
{% endapi-method-parameter %}

{% api-method-parameter name="limit" type="number" required=false %}
The maximum number of apps to return per page.  
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
  "apps": [
    {
      "categories": [
        "relayer"
      ],
      "description": "Built by the 0x core team – 0x API makes accessing DEX liquidity easy through the use of smart order routing which aggregates liquidity from 0x Mesh, Kyber, Uniswap, and more.",
      "id": "052b4862-2142-4532-bdc0-416814b0a5fe",
      "logoUrl": "https://cdn.staticaly.com/gh/0xTracker/0x-tracker-worker/master/src/attributions/logos/0x-api.png",
      "name": "0x API",
      "stats": {
        "activeTraders": 4857,
        "activeTradersChange": -16.099499049922265,
        "tradeCount": {
          "relayed": 7316,
          "total": 7316
        },
        "tradeCountChange": {
          "relayed": -14.900546702338024,
          "total": -14.900546702338024
        },
        "tradeVolume": {
          "relayed": 27118521.443833765,
          "total": 27118521.443833765
        },
        "tradeVolumeChange": {
          "relayed": 30.176737544737716,
          "total": 30.176737544737716
        }
      },
      "urlSlug": "0x-api",
      "websiteUrl": "https://0x.org/api"
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

{% api-method method="get" host="https://api.0xtracker.com" path="/article-sources" %}

{% api-method method="get" host="https://api.0xtracker.com" path="/articles" %}
{% api-method-summary %}

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
        "fillCount": 2026,
        "fillVolume": 1728911.7356433223,
        "tradeCount": 1559,
        "tradeVolume": 1285629.9583338788
      },
      "version": 2
    },
    {
      "stats": {
        "fillCount": 374,
        "fillVolume": 585201.4918576538,
        "tradeCount": 357,
        "tradeVolume": 540775.9960855007
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

{% api-method-query-parameters %}
{% api-method-parameter name="statsPeriod" type="string" required=false %}
The time period for which to return stats and price. Must be one of: day, week, month, year, all.  
_Default value is day._
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Returned when a token is found matching the specified address.
{% endapi-method-response-example-description %}

```javascript
{
  "address": "0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2",
  "circulatingSupply": null,
  "imageUrl": "https://cdn.staticaly.com/gh/TrustWallet/tokens/master/tokens/0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2.png",
  "lastTrade": {
    "date": "2020-04-16T19:01:36.000Z",
    "id": "5e98ac33f3edba0548d57499"
  },
  "marketCap": 401979735.10782796,
  "name": "Wrapped Ether",
  "price": {
    "change": 8.77204150486982,
    "close": 170.87,
    "high": 174.47853088378906,
    "last": 170.87,
    "low": 145.86898803710938,
    "open": 157.09
  },
  "stats": {
    "fillCount": 3403,
    "fillVolume": {
      "token": 29343.563185668743,
      "USD": 4839232.989858636
    },
    "tradeCount": 3064,
    "tradeVolume": {
      "token": 25417.591251252252,
      "USD": 4189388.872657468
    }
  },
  "statsPeriod": "day",
  "symbol": "WETH",
  "totalSupply": 2352547.1709944867,
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
The time period for which to return stats and price. Must be one of: day, week, month, year, all.  
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
      "circulatingSupply": null,
      "imageUrl": "https://cdn.staticaly.com/gh/TrustWallet/tokens/master/tokens/0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2.png",
      "lastTrade": {
        "date": "2020-04-16T19:01:36.000Z",
        "id": "5e98ac33f3edba0548d57499"
      },
      "marketCap": 401979735.10782796,
      "name": "Wrapped Ether",
      "price": {
        "change": 8.509557376008132,
        "close": 170.87,
        "high": 174.47853088378906,
        "last": 170.87,
        "low": 145.86898803710938,
        "open": 157.47
      },
      "stats": {
        "fillCount": 3434,
        "fillVolume": {
          "token": 29353.28848995183,
          "USD": 4840761.2617340805
        },
        "tradeCount": 3092,
        "tradeVolume": {
          "token": 25423.74629868023,
          "USD": 4190355.757510045
        }
      },
      "symbol": "WETH",
      "totalSupply": 2352547.1709944867,
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
{% api-method-parameter name="statsPeriodTo" type="string" required=false %}
End of the time period for which to return stats. Should be used as an alternative to the statsPeriod parameter. Must be in the format YYYY-MM-DD.
{% endapi-method-parameter %}

{% api-method-parameter name="statsPeriodFrom" type="string" required=false %}
Start of the time period for which to return stats. Should be used as an alternative to the statsPeriod parameter. Must be in the format YYYY-MM-DD.
{% endapi-method-parameter %}

{% api-method-parameter name="apps" type="string" required=false %}
A comma-separated list of app IDs to filter the traders by. App IDs can be found by calling the apps endpoint.
{% endapi-method-parameter %}

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

{% api-method method="get" host="https://api.0xtracker.com" path="/fills/:id" %}
{% api-method-summary %}
Trade
{% endapi-method-summary %}

{% api-method-description %}
Returns the full details of a single trade.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
ID of the trade to fetch.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Returned when the specified ID matches a valid trade.
{% endapi-method-response-example-description %}

```javascript
{
  "affiliate": null,
  "apps": [
    {
      "id": "a5808078-d297-4fbd-a818-dccd8a5438ed",
      "logoUrl": "https://cdn.staticaly.com/gh/0xTracker/0x-tracker-worker/master/src/attributions/logos/star-bit.png",
      "name": "STAR BIT",
      "type": "relayer",
      "urlSlug": "star-bit"
    }
  ],
  "assets": [
    {
      "amount": "0.023595691875",
      "bridge": null,
      "price": {
        "USD": 186.71999999999997
      },
      "tokenAddress": "0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2",
      "tokenImageUrl": "https://cdn.staticaly.com/gh/TrustWallet/tokens/master/tokens/0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2.png",
      "tokenSymbol": "WETH",
      "tokenType": "Wrapped Ether",
      "traderType": "maker",
      "type": "erc-20"
    },
    {
      "amount": "2041",
      "bridge": null,
      "price": {
        "USD": 0.0021586416398334148
      },
      "tokenAddress": "0x503f9794d6a6bb0df8fbb19a2b3e2aeab35339ad",
      "tokenImageUrl": "https://0xtracker.com/assets/logos/starbit.png",
      "tokenSymbol": "SBT",
      "tokenType": "Star Bit Token",
      "traderType": "taker",
      "type": "erc-20"
    }
  ],
  "date": "2019-11-04T18:22:03.000Z",
  "fees": [],
  "feeRecipient": "0x8124071f810d533ff63de61d0c98db99eeb99d64",
  "feeRecipientMetadata": {
    "address": "0x8124071f810d533ff63de61d0c98db99eeb99d64",
    "imageUrl": null,
    "isContract": false,
    "name": null
  },
  "id": "5dc06d68ab099b000489d3fe",
  "makerAddress": "0xda912ecc847b3d98ca882e396e693e485deed518",
  "maker": {
    "address": "0xda912ecc847b3d98ca882e396e693e485deed518",
    "imageUrl": null,
    "isContract": false,
    "name": null
  },
  "orderHash": "0x9165afe0f746839d2f390972b9a4473910143e6650be48477e7eb0196b607b02",
  "protocolVersion": 2,
  "relayer": {
    "imageUrl": "https://cdn.staticaly.com/gh/0xTracker/0x-tracker-worker/master/src/attributions/logos/star-bit.png",
    "name": "STAR BIT",
    "slug": "star-bit"
  },
  "senderAddress": "0x0681e844593a051e2882ec897ecd5444efe19ff2",
  "sender": {
    "address": "0x0681e844593a051e2882ec897ecd5444efe19ff2",
    "imageUrl": "https://cdn.staticaly.com/gh/0xTracker/ethereum-address-metadata/master/images/starbit.png",
    "isContract": false,
    "name": "StarbitEx"
  },
  "status": "successful",
  "takerAddress": "0x0681e844593a051e2882ec897ecd5444efe19ff2",
  "taker": {
    "address": "0x0681e844593a051e2882ec897ecd5444efe19ff2",
    "imageUrl": "https://cdn.staticaly.com/gh/0xTracker/ethereum-address-metadata/master/images/starbit.png",
    "isContract": false,
    "name": "StarbitEx"
  },
  "transactionHash": "0xc99fc0a2c65da2d3b94a1cd979afb05317203354a2dc6999c0dde26c61fecd0e",
  "transactionFrom": {
    "address": "0x0681E844593A051E2882Ec897ecD5444eFE19FF2",
    "imageUrl": null,
    "isContract": null,
    "name": null
  },
  "transactionTo": {
    "address": "0x080bf510FCbF18b91105470639e9561022937712",
    "imageUrl": null,
    "isContract": null,
    "name": null
  },
  "value": {
    "USD": 4.4057875869
  }
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}
Returned when no trade can be found with the specified ID.
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
Trades
{% endapi-method-summary %}

{% api-method-description %}
Returns a paginated collection of trades matching the specified parameters.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="trader" type="string" required=false %}
Trader address to filter by.
{% endapi-method-parameter %}

{% api-method-parameter name="sortDirection" type="string" required=false %}
The direction in which results should be sorted. Valid values are: "asc" and "desc".  
_Default value is "desc"._
{% endapi-method-parameter %}

{% api-method-parameter name="sortBy" type="string" required=false %}
The field by which to sort results. Valid values are: "date", "protocolFeeUSD" and "value".  
_Default value is "date"._
{% endapi-method-parameter %}

{% api-method-parameter name="apps" type="string" required=false %}
A comma-separated list of app IDs to filter by. App IDs can be found by calling the apps endpoint.
{% endapi-method-parameter %}

{% api-method-parameter name="valueTo" type="number" required=false %}
Minimum trade value \(in USD\) to filter by.
{% endapi-method-parameter %}

{% api-method-parameter name="valueFrom" type="number" required=false %}
Minimum trade value \(in USD\) to filter by.
{% endapi-method-parameter %}

{% api-method-parameter name="protocolVersion" type="number" required=false %}
Protocol version to filter by.
{% endapi-method-parameter %}

{% api-method-parameter name="token" type="string" required=false %}
Address of a token to filter by.
{% endapi-method-parameter %}

{% api-method-parameter name="limit" type="number" required=false %}
The maximum number of trades to return per page.  
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
          "apps": [
            {
              "id": "0a5d5f06-1626-4276-893f-42527e5a4147",
              "logoUrl": "https://cdn.staticaly.com/gh/0xTracker/0x-tracker-worker/master/src/attributions/logos/tokenlon.png",
              "name": "Tokenlon",
              "type": "relayer",
              "urlSlug": "tokenlon"
            }
          ],
          "assets": [
            {
              "amount": "367.191483",
              "bridge": null,
              "price": {
                "USD": 0.9997
              },
              "tokenAddress": "0xdac17f958d2ee523a2206206994597c13d831ec7",
              "tokenImageUrl": "https://cdn.staticaly.com/gh/TrustWallet/tokens/master/tokens/0xdac17f958d2ee523a2206206994597c13d831ec7.png",
              "tokenSymbol": "USDT",
              "tokenType": "Tether USD",
              "traderType": "maker",
              "type": "erc-20"
            },
            {
              "amount": "0.5",
              "bridge": null,
              "price": {
                "USD": 734.1626511102
              },
              "tokenAddress": "0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2",
              "tokenImageUrl": "https://cdn.staticaly.com/gh/TrustWallet/tokens/master/tokens/0xc02aaa39b223fe8d0a0e5c4f27ead9083c756cc2.png",
              "tokenSymbol": "WETH",
              "tokenType": "Wrapped Ether",
              "traderType": "taker",
              "type": "erc-20"
            }
          ],
          "date": "2020-12-30T14:47:21.000Z",
          "feeRecipient": "0xd4dff17ccf7ca237e66270cc097ae60dabf8f85b",
          "id": "5fec93c57f7a4022f922b139",
          "makerAddress": "0x9c597c4da5e8f052182fe9b3d12af7e61e8d809b",
          "protocolVersion": 2,
          "relayer": {
            "imageUrl": "https://cdn.staticaly.com/gh/0xTracker/0x-tracker-worker/master/src/attributions/logos/tokenlon.png",
            "name": "Tokenlon",
            "slug": "tokenlon"
          },
          "status": "successful",
          "takerAddress": "0x8d90113a1e286a5ab3e496fbd1853f265e5913c6",
          "value": {
            "USD": 367.0813255551
          }
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
      "message": "Invalid query parameter: app",
      "reason": "No app exists with an ID of \"fubar\"",
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

{% hint style="info" %}
All metrics endpoints \(with the exception of token\) accept a granularity parameter whose valid values vary based on the specified time period. The valid values for each time period are as follows:

* **day** - hour
* **week** - hour, day
* **month** - day
* **year** - day, week, month
* **all** - week, month
{% endhint %}

{% api-method method="get" host="https://api.0xtracker.com" path="/metrics/active-trader" %}
{% api-method-summary %}
Active Trader Metrics
{% endapi-method-summary %}

{% api-method-description %}
Returns a collection of active trader metrics for the specified time period.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="granularity" type="string" required=false %}
Granularity at which to aggregate metrics. Must be one of: hour, day, week, month. Valid values vary based on specified period \(see note above\).
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
    "date": "2020-02-05T00:00:00.000Z",
    "makerCount": 157,
    "takerCount": 61,
    "traderCount": 210
  },
  {
    "date": "2020-02-06T00:00:00.000Z",
    "makerCount": 149,
    "takerCount": 70,
    "traderCount": 209
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

{% api-method method="get" host="https://api.0xtracker.com" path="/metrics/app" %}
{% api-method-summary %}
App Metrics
{% endapi-method-summary %}

{% api-method-description %}
Returns a collection of metrics for the specified app and time period.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="granularity" type="string" required=false %}
Granularity at which to aggregate metrics. Valid values are: "hour", "day", "week" and "month". Valid values vary based on specified period \(see note above\).
{% endapi-method-parameter %}

{% api-method-parameter name="app" type="string" required=true %}
ID of the app to fetch metrics for. App IDs can be found by calling the apps endpoint.
{% endapi-method-parameter %}

{% api-method-parameter name="period" type="string" required=false %}
Time period for which to return metrics. Valid values are: "day", "week", "month", "year" and "all".  
_Default value is "month"._
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
    "fillCount": 505,
    "fillVolume": 804818.3748855987,
    "tradeCount": 505,
    "tradeVolume": 804818.3748855987
  },
  {
    "date": "2019-10-10T00:00:00.000Z",
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
{% api-method-parameter name="granularity" type="string" required=false %}
Granularity at which to aggregate metrics. Must be one of: hour, day, week, month. Valid values vary based on specified period \(see note above\).
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
    "fillCount": 1383,
    "fillVolume": 929465.5342802514,
    "protocolFees": {
      "ETH": "152.8",
      "USD": 22920
    },
    "tradeCount": 999,
    "tradeVolume": 876987,
  },
  {
    "date": "2019-10-06T00:00:00.000Z",
    "fillCount": 1624,
    "fillVolume": 595794.5615575106,
    "protocolFees": {
      "ETH": "167",
      "USD": 25050
    },
    "tradeCount": 1473,
    "tradeVolume": 512018.89,
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

{% api-method method="get" host="https://api.0xtracker.com" path="/metrics/protocol" %}
{% api-method-summary %}
Protocol Metrics
{% endapi-method-summary %}

{% api-method-description %}
Returns a collection of protocol metrics for the specified time period.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="granularity" type="string" required=false %}
Granularity at which to aggregate metrics. Must be one of: hour, day, week, month. Valid values vary based on specified period \(see note above\).
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
    "date": "2020-02-05T00:00:00.000Z",
    "stats": [
      {
        "fillCount": 1750,
        "fillVolume": 1096872.58949153,
        "protocolVersion": 2,
        "tradeCount": 1229,
        "tradeVolume": 977798.7221048203
      },
      {
        "fillCount": 513,
        "fillVolume": 762915.6891538525,
        "protocolVersion": 3,
        "tradeCount": 453,
        "tradeVolume": 677829.7757666862
      }
    ]
  },
  {
    "date": "2020-02-06T00:00:00.000Z",
    "stats": [
      {
        "fillCount": 1419,
        "fillVolume": 1273827.704905562,
        "protocolVersion": 2,
        "tradeCount": 1054,
        "tradeVolume": 1151976.1669566333
      },
      {
        "fillCount": 579,
        "fillVolume": 861379.0750347817,
        "protocolVersion": 3,
        "tradeCount": 526,
        "tradeVolume": 772009.9522138488
      }
    ]
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
{% api-method-parameter name="granularity" type="string" required=false %}
Granularity at which to aggregate metrics. Must be one of: hour, day, week, month. Valid values vary based on specified period \(see note above\).
{% endapi-method-parameter %}

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
    "date": "2020-03-18T00:00:00.000Z",
    "fillCount": 2629,
    "fillVolume": {
      "token": 17862.190608243993,
      "USD": 2057401.0503150492
    },
    "tradeCount": 2231,
    "tradeVolume": {
      "token": 16152.55733998471,
      "USD": 1860912.8854162937
    },
    "price": {
      "close": 118.59575932663792
    }
  },
  {
    "date": "2020-03-19T00:00:00.000Z",
    "fillCount": 2702,
    "fillVolume": {
      "token": 35666.59929770062,
      "USD": 4625891.901006651
    },
    "tradeCount": 2495,
    "tradeVolume": {
      "token": 30823.688957643713,
      "USD": 3979471.2098343465
    },
    "price": {
      "close": 136.7
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
{% api-method-parameter name="granularity" type="string" required=false %}
Granularity at which to aggregate metrics. Must be one of: hour, day, week, month. Valid values vary based on specified period \(see note above\).
{% endapi-method-parameter %}

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
    },
    "tradeCount": {
      "maker": 8,
      "taker": 0,
      "total": 8
    },
    "tradeVolume": {
      "maker": 36012.78,
      "taker": 0,
      "total": 36012.78
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
    },
    "tradeCount": {
      "maker": 5,
      "taker": 0,
      "total": 5
    },
    "tradeVolume": {
      "maker": 23042.76,
      "taker": 0,
      "total": 23042.76
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
Returns active trader stats for the specified time period.
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

