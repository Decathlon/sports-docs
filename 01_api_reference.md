# API Reference

## List of sports

```shell
curl "https://sports.api.decathlon.com/sports"
```

> JSON response:

```json
{
    "data": [
        {
            "id": "224",
            "type": "sport",
            "attributes": {
                "name": "Swimming",
                "description": null,
                "parent_id": null,
                "decathlon_id": 224,
                "slug": "swimming",
                "locale": "en",
                "weather": []
            },
            "relationships": {
                "tags": {
                  "data": [
                      "bathing",
                      "swimming-pool",
                      "triathlon",
                      "crawl",
                      "breaststroke",
                      "butterfly",
                      "backstroke",
                      "freestyle",
                      "open-water-swimming",
                      "marathon-swimming",
                      "synchronized-swimming",
                      "paralympic-swimming",
                      "aqualearning",
                      "competitive-swimming"
                  ]
                },
                "children": {
                    "data": [
                        {
                            "id": "331",
                            "type": "sport"
                        },
                      //...
                    ]
                },
              //...
            },
          //...
        },
        {
            "id": "291",
            "type": "sport",
            "attributes": {
                "name": "Body Building / Cross Training",
                "description": null,
                "parent_id": 486,
                "slug": "body-building-cross-training",
                "locale": "en"
            },
            "relationships": {
                "parent": {
                    "data": {
                        "id": "486",
                        "type": "sport"
                    },
                  //...
                }
            },
          //...
        },
      //...
    ]
}

```

This endpoint returns a detailled collection of all the sports in our database.

### HTTP Request

`GET https://sports.api.decathlon.com/sports`

### Request Parameters

Parameter    | Example  | Description
---------    | -------  | -----------
tag          | `'race'` | Filter out sports not containing the tag.
parents_only | `true`   | Filter out sports that are not considered _parent sports_.
has_icon    | `true` | Filter out sports which do not have an associated icon.
has\_decahtlon\_id | `true`   | _Decathlon specific logic:_ Filter out sports that are not matched to a masterdata sport.

## Querying a single Sport

```shell
curl "https://sports.api.decathlon.com/sports/224"
```

> JSON Response

```json
{
    "data": {
        "id": "224",
        "type": "sport",
        "attributes": {
            "name": "Swimming",
            "description": null,
            "parent_id": null,
            "slug": "swimming",
            "locale": "en",
            "weather": [ ],
            "icon": "https://sports-api-production.s3.amazonaws.com/uploads/sport/icon/224/224.svg"
        },
        "relationships": {
            "children": {
                "data": [
                    {
                        "id": "331",
                        "type": "sport"
                    },
                    {
                        "id": "219",
                        "type": "sport"
                    },
                  //...
                ]
            },
          //...
        }
    }
}
```

This endpoint retrieves a single sport.<br/>
The ID parameter can be passed in as a `slug` or `id` for convenience.<br/>

### HTTP Request

`GET https://sports.api.decathlon.com/sports/:id`

### Request Parameters

The only accepted (and required) parameter for this endpoint is the sport `id` or `slug`

<div id="isearch"></div>

## Intelligent Search

```shell
curl "https://sports.api.decathlon.com/sports/search/water?coordinates=-73.5826985,45.5119864"
```
> JSON response:

```json
[
    {
        "id": 224,
        "type": "sport",
        "attributes": {
            "name": "Swimming",
            "description": "Swimming includes several sports that are practiced on the surface and/or under the water. It allows you to use your whole body to move, sometimes in speed trials, sometimes in artistic routines, but requiring at all times a great coordination. Above all, thanks to the effect of gravity, swimming helps to minimize the impact of force on your body and joints, in addition to being a complete and very accessible sport that can easily allow you to feel like a fish in the water!\n",
            "parent_id": null,
            "decathlon_id": 224,
            "slug": "swimming",
            "locale": "en",
            "weather": []
        },
        "relationships": {
            "children": {
                "data": [
                    {
                        "id": 331,
                        "type": "sport"
                    },
                    {
                        "id": 385,
                        "type": "sport"
                    },
                    {
                        "id": 406,
                        "type": "sport"
                    },
                    {
                        "id": 228,
                        "type": "sport"
                    },
                    {
                        "id": 500,
                        "type": "sport"
                    },
                    {
                        "id": 501,
                        "type": "sport"
                    }
                ]
            },
            "parent": {
                "data": null
            },
            "group": {
                "data": {
                    "id": 1,
                    "type": "group"
                }
            },
            "related": {
                "data": [
                    {
                        "id": 219,
                        "type": "sport"
                    },
                    {
                        "id": 405,
                        "type": "sport"
                    },
                    {
                        "id": 12,
                        "type": "sport"
                    }
                ]
            },
            "tags": {
                "data": [
                    "bathing",
                    "swimming-pool",
                    "triathlon",
                    "crawl",
                    "breaststroke",
                    "butterfly",
                    "backstroke",
                    "freestyle",
                    "open-water-swimming",
                    "marathon-swimming",
                    "synchronized-swimming",
                    "paralympic-swimming",
                    "aqualearning",
                    "competitive-swimming"
                ]
            },
            "images": {
                "data": [
                    {
                        "id": 204,
                        "url": "https://sports.api.decathlon.com/rails/active_storage/blobs/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBY3c9IiwiZXhwIjpudWxsLCJwdXIiOiJibG9iX2lkIn19--cb60fb5bcf08e4676adace5cf677d12196bafe55/swimming.jpg",
                        "meta": {
                            "width": 500,
                            "height": 333
                        },
                        "variants": [
                            {
                                "thumbnail": {
                                    "url": "https://sports.api.decathlon.com/rails/active_storage/representations/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBY3c9IiwiZXhwIjpudWxsLCJwdXIiOiJibG9iX2lkIn19--cb60fb5bcf08e4676adace5cf677d12196bafe55/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaDdCam9MY21WemFYcGxTU0lJTWpBd0Jqb0dSVlE9IiwiZXhwIjpudWxsLCJwdXIiOiJ2YXJpYXRpb24ifX0=--8ed889d31ac3a5e9d5446846a4f7747f8eaa0bc1/swimming.jpg"
                                },
                                "medium": {
                                    "url": "https://sports.api.decathlon.com/rails/active_storage/representations/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBY3c9IiwiZXhwIjpudWxsLCJwdXIiOiJibG9iX2lkIn19--cb60fb5bcf08e4676adace5cf677d12196bafe55/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaDdCam9MY21WemFYcGxTU0lKTVRBeU5BWTZCa1ZVIiwiZXhwIjpudWxsLCJwdXIiOiJ2YXJpYXRpb24ifX0=--0e36b4a54e8a5057a18945f67d3ad11a9ef22382/swimming.jpg"
                                }
                            }
                        ]
                    }
                ]
            }
        }
    },
    {
        "id": 219,
        "type": "sport",
        "attributes": {
            "name": "Aquafit",
    //...
    },
  }
]
```

Given coordinates and a search query: the endpoint will return you with a list of <u><i>relevant sports</i></u> by searching through: ` synonyms, lexical champ, tags and descriptions`.

**Assuring location and application relevance:** Prior to being returned, the results will be <u><i>reindexed based on the popularity</i></u> of the sports in the vicinity of the given coordinates. If a source is provided, the popularity attributed to each sport will be influenced by the specified dataset.
<br/><br/>



Example: <a style="font-style: bold" href="https://sports.api.decathlon.com/sports/search/water?source=activities&coordinates=-73.123,45.123" target="_blank">`https://sports.api.decathlon.com/sports/search/water?source=activities&coordinates=-73.123,45.123`</a>, will return water sports and the results in the query will be sorted by how often these sports have activities listed for them near the coordinates.

### HTTP Request

`GET https://sports.api.decathlon.com/sportssearch/:query?coordinates=:coordinates"`

### Request Parameters

The only required parameter for this endpoint is the `:coordinates`.

Parameter    |  Example   | Description
:---               |  :---:     | :---
query              |  `'water'`               | Filter sports by their relevance to your query.
coordinates        | `-73.5826985,45.5119864` | (`longitude, latitude`) Sport popularity is geolocalized.
source             | `popular`                | Influence popularity re-indexing by application: `popular, decathlon, activities, places, events` (default: `popular`)
has_icon           | `true`  | Filter out sports without an associated icon.
parents_only       | `true`  | Filter out sports that are not considered _parent sports_.
strict             | `true`  | If `true`, will perform a search for sport who's name contains the exact `query`
has\_decathlon\_id | `true`  | _Decathlon specific logic:_ Filter out sports that are not matched to a masterdata sport.
**Showcase**

To easily explore the various parameters, we built a <a style="font-style: bold" href="https://quiet-mesa-31414.herokuapp.com/" target="_blank">showcase</a>

## Location based recommendations
<div id="recommendations"></div>

```shell
curl
"https://sports.api.decathlon.com/sports/recommendations/geolocation?coordinates=-73.582,45.511"
```

> JSON Response

```json
[
    {
        "id": 224,
        "type": "sport",
        "attributes": {
            "name": "Swimming",
            "description": "Swimming includes several sports that are practiced on the surface and/or under the water. It allows you to use your whole body to move, sometimes in speed trials, sometimes in artistic routines, but requiring at all times a great coordination. Above all, thanks to the effect of gravity, swimming helps to minimize the impact of force on your body and joints, in addition to being a complete and very accessible sport that can easily allow you to feel like a fish in the water!\n",
            "parent_id": null,
            "decathlon_id": 224,
            "slug": "swimming",
            "locale": "en",
            "weather": []
        },
      //...
    },
    {
        "id": 219,
        "type": "sport",
        "attributes": {
            "name": "Aquafit",
      //...
    },
  }
]
```

From the coordinates, it'll find the nearest city with valid contextual data and return the most popular sports for your desired application.

### HTTP Request

`GET https://sports.api.decathlon.com/sports/recommendations/geolocation?coordinates=:coordinates"`

### Request Parameters

The only required parameter for this endpoint is the `:coordinates`.

Parameter | Example | Description
--------- | ------- | -----------
coordinates     | `-73.5826985,45.5119864` | (`longitude, latitude`) Sport popularity is geolocalized.
source             | `popular`                | Influence popularity indexing by application: `popular, decathlon, activities, places, events` (default: `popular`)
has_icon           | `true`  | Filter out sports without an associated icon.
parents_only       | `true`  | Filter out sports that are not considered _parent sports_.

## Listing Sport Groups

```shell
curl "https://sports.api.decathlon.com/groups"
```

> JSON response:

```json
{
    "data": [
        {
            "id": 1,
            "type": "group",
            "attributes": {
                "name": "Water Aerobics",
                "slug": "water-aerobics",
                "locale": "en"
            },
            "relationships": {
                "sports": {
                    "data": [
                        {
                            "id": 484,
                            "type": "sport"
                        },
                        {
                            "id": 331,
                            "type": "sport"
                        },
                        {
                            "id": 219,
                            "type": "sport"
                        },
                        // ...
                    ]
                }
            }
        },
        {
            "id": 2,
            "type": "group",
            "attributes": {
                "name": "Athletics",
                "slug": "athletics",
                "locale": "en"
            },
            "relationships": {
                "sports": {
                    "data": [
                        {
                            "id": 257,
                            "type": "sport"
                        },
                        {
                            "id": 390,
                            "type": "sport"
                        },
                        // ...
                    ]
                }
            }
        },
    ]
```

This endpoint retrieves all sport groups and allows users to have a bird's eye
view on how our sports are organized and related to one another.

### HTTP Request

`GET https://sports.api.decathlon.com/groups`

### Request Parameters

This endpoint accepts no parameters.

## Querying a single group

<aside class="warning">
	Deprecation incoming, will be replaced by an AI grouping solution in the near future.
</aside>

```shell
curl "https://sports.api.decathlon.com/groups/water-aerobics"
```

> JSON Response

```json
{
    "data": {
        "id": 1,
        "type": "group",
        "attributes": {
            "name": "Water Aerobics",
            "slug": "water-aerobics",
            "locale": "en"
        },
        "relationships": {
            "sports": {
                "data": [
                    {
                        "id": 484,
                        "type": "sport"
                    },
                    {
                        "id": 224,
                        "type": "sport"
                    },
                    {
                        "id": 331,
                        "type": "sport"
                    },
                    {
                        "id": 385,
                        "type": "sport"
                    },
                    {
                        "id": 406,
                        "type": "sport"
                    },
                    {
                        "id": 228,
                        "type": "sport"
                    },
                    {
                        "id": 405,
                        "type": "sport"
                    },
                    {
                        "id": 221,
                        "type": "sport"
                    },
                    {
                        "id": 500,
                        "type": "sport"
                    },
                    {
                        "id": 501,
                        "type": "sport"
                    },
                    {
                        "id": 502,
                        "type": "sport"
                    },
                    {
                        "id": 503,
                        "type": "sport"
                    },
                    {
                        "id": 504,
                        "type": "sport"
                    },
                    {
                        "id": 505,
                        "type": "sport"
                    },
                    {
                        "id": 506,
                        "type": "sport"
                    },
                    {
                        "id": 219,
                        "type": "sport"
                    }
                ]
            }
        }
    }
}
```

This endpoint retrieves a group (and its children, if any).
The ID parameter can be passed in as a `slug` or `id` for convenience.
In the case a group doesn't have any children, the relationship object will return `null`.

### HTTP Request

`GET https://sports.api.decathlon.com/groups/water-aerobics`

### Request Parameters

Search query errors will be rescued with specific error messages, and an `HTTP 404` status code.

<div style="display: none">


	Insipiration:
		https://www.flex.io/docs
    https://developers.cimediacloud.com/

	Ideas :
		Run in postman :
		https://developer.safaricom.co.ke/docs?ruby#introduction




</div>
