# API Reference

<div id="isearch"></div>

## Search

Given an application source <i>(or multiple)</i>, coordinates and a search query: the endpoint will return you with a list of <u><i>relevant sports</i></u> based on language recognition, synonyms, lexical champ, tags, descriptions. Prior to being returned, the list will be <u><i>reindexed based on the popularity</i></u> of each sport in the vicinity of the given coordinates.

**Showcase**

To easily play around with the various parameters, we built a <a style="font-style: bold" href="https://quiet-mesa-31414.herokuapp.com/" target="_blank">showcase</a>

```shell
curl "https://sports.api.decathlon.com/sports/search/:query?source=:source&coordinates=:coordinates"
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
```

### Query parameters
Parameter    | Default  | Example | Description
:---    | :---:  | :---: | :---
query        |   | water |Filter sports by their relevance to your query.
source       | `popular`| One of : |`popular, decathlon, activities, places, events`
coordinates  |\***required**  |-73.5826985,45.5119864| (`longitude, latitude`) Sport popularity is geolocalized.
has\_decathlon\_id | false | true | Will only return sports containing a Decathlon ID
has_icon    | false | true  | Filter by sports which have an associated icon
parents_only | false | true | Will only return sports that have parent_id: null
details      | true  | false | If false, will return a minified payload
strict       | false | true  | If true, will strictly search for sport who's name contains the query

## Listing

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
                        {
                            "id": "219",
                            "type": "sport"
                        },
                        {
                            "id": "405",
                            "type": "sport"
                        },
                        {
                            "id": "449",
                            "type": "sport"
                        },
                        {
                            "id": "224",
                            "type": "sport"
                        }
                    ]
                }
            }
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
                    }
                }
            }
        },
        //...
    ]
}

```

While the search endpoint has a looser interpretation, the sports endpoint is considered strict<br/>
Default when not passing a query is to return the entire list.


### HTTP Request

`GET https://sports.api.decathlon.com/sports`

### Query Parameters

Search query errors will be rescued with specific error messages, and an `HTTP 404` status code.

Parameter    | Example  | Description
---------    | -------  | -----------
q            | `socc`   | Query a sport by its name, using a string for searching
tag          | `winter` | Filter sports by a tag.
decathlon_id | `175`    | Search sports by Decathlon's legacy ID
parents_only | `true`   | Boolean parameter to display parent-sports only.
has\_decahtlon\_id | `true`   | Boolean parameter to display decathlon legacy sports only.
has_icon    | _true_ or _false_ | Filter by sports which have an associated icon

## Querying a single Sport

```shell
curl "https://sports.api.decathlon.com/sports/:id"
```

> JSON Response

```json
{
    "data": {
        "id": "278",
        "type": "sport",
        "attributes": {
            "name": "Swimming",
            "description": null,
            "parent_id": null,
            "slug": "swimming",
            "locale": "en"
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
                    {
                        "id": "405",
                        "type": "sport"
                    },
                    {
                        "id": "449",
                        "type": "sport"
                    },
                    {
                        "id": "224",
                        "type": "sport"
                    }
                ]
            }
        }
    }
}
```

This endpoint retrieves a sport (and its children, if any).
The ID parameter can be passed in as a `slug` or `id` for convenience.
In the case a sport doesn't have children, or if it's already a child, the relationship object will return `null`.
If a sport is a child, the `parent_id` column will display the ID of its parent.

### HTTP Request

`GET https://sports.api.decathlon.com/sports/278`

### Query Parameters

Search query errors will be rescued with specific error messages, and an `HTTP 404` status code.

## Location based recommendations
<div id="recommendations"></div>

```shell
curl
"https://sports.api.decathlon.com/sports/recommendations/geolocation?coordinates=-73.582,45.511&count=3"
```

> JSON Response

```json
[ "123", "456", "789" ]
```

From the coordinates, it'll find the nearest city with valid contextual data and return the most popular sports for your desired application. <a href="https://fr.batchgeo.com/map/08103d15ce7f0a4e1f6a7cf3115583a6">View the web traffic coverage</a>

Parameter | Example | Description
--------- | ------- | -----------
coordinates     | `-73,45` | \***Required** `Longitude, latitude` for the geolocation filter
count     | `5`     | Number of recommendations (Default: 3)
source    | `popular` | One of : `popular, decathlon, activities, places, amilia`
has_icon    | _true_ or _false_ | Filter by sports which have an associated icon
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

### Query Parameters

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

### Query Parameters

Search query errors will be rescued with specific error messages, and an `HTTP 404` status code.

<div style="display: none">


	Insipiration:
		https://www.flex.io/docs
    https://developers.cimediacloud.com/

	Ideas :
		Run in postman :
		https://developer.safaricom.co.ke/docs?ruby#introduction




</div>
