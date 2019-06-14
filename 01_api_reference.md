# API Reference

## Listing Sports

```shell
curl "https://sports.api.decathlon.com/sports"
```

> JSON response:

```json
{
    "data": [
        {
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

This endpoint retrieves all sports meeting specific criteria


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

## Querying a single Sport

```shell
curl "https://sports.api.decathlon.com/sports/swimming"
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

## Fetching recommendations by popularity

```shell
curl
"https://sports.api.decathlon.com/sports/:sport_id/recommendations"
```

> JSON Response

```json
[ "123", "456", "789" ]
```

This endpoint provides sport recommendations based on machine learning algorithms.

Parameter | Example | Description
--------- | ------- | -----------
sport_id  | `175`   | Sport ID
count     | `5`     | Number of recommendations (Default: 3)

## Fetching recommendations by location

```shell
curl
"https://sports.api.decathlon.com/sports/:sport_id/recommendations/:location"
```

> JSON Response

```json
[ "123", "456", "789" ]
```

This endpoint provides sport recommendations based on popularity within a location and machine learning algorithms.

Parameter | Example       | Description
--------- | -------       | -----------
location  | `montreal_ca` | City name and 2-letter country code
sport_id  | `175`         | Sport ID
count     | `5`           | Number of recommendations (Default: 3)

## Fetching recommendations based on density of places per country

```shell
curl
"https://sports.api.decathlon.com/sports/:sport_id/recommendations/:country"
```

> JSON Response

```json
[ "123", "456", "789" ]
```

This endpoint provides sport recommendations based on an average density of
places in a specified country.

Parameter | Example       | Description
--------- | -------       | -----------
country   | `CA`          | 2-letter country code

### HTTP Request

`GET https://sports.api.decathlon.com/sports/175/recommendations`

### Query Parameters

Search query errors will be rescued with specific error messages, and an `HTTP 404` status code.

## Listing Sport Groups

```shell
curl "https://sports.api.decathlon.com/sports"
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
                            "id": 221,
                            "type": "sport"
                        },
                        {
                            "id": 405,
                            "type": "sport"
                        },
                        {
                            "id": 224,
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
                        {
                            "id": 339,
                            "type": "sport"
                        },
                        {
                            "id": 4,
                            "type": "sport"
                        },
                        {
                            "id": 340,
                            "type": "sport"
                        },
                        {
                            "id": 338,
                            "type": "sport"
                        },
                        {
                            "id": 389,
                            "type": "sport"
                        },
                        {
                            "id": 5,
                            "type": "sport"
                        },
                        {
                            "id": 341,
                            "type": "sport"
                        },
                        {
                            "id": 461,
                            "type": "sport"
                        },
                        {
                            "id": 12,
                            "type": "sport"
                        },
                        {
                            "id": 488,
                            "type": "sport"
                        },
                        {
                            "id": 261,
                            "type": "sport"
                        },
                        {
                            "id": 487,
                            "type": "sport"
                        },
                        {
                            "id": 507,
                            "type": "sport"
                        },
                        {
                            "id": 508,
                            "type": "sport"
                        },
                        {
                            "id": 509,
                            "type": "sport"
                        },
                        {
                            "id": 510,
                            "type": "sport"
                        },
                        {
                            "id": 511,
                            "type": "sport"
                        },
                        {
                            "id": 512,
                            "type": "sport"
                        },
                        {
                            "id": 513,
                            "type": "sport"
                        },
                        {
                            "id": 514,
                            "type": "sport"
                        },
                        {
                            "id": 515,
                            "type": "sport"
                        },
                        {
                            "id": 516,
                            "type": "sport"
                        },
                        {
                            "id": 517,
                            "type": "sport"
                        },
                        {
                            "id": 518,
                            "type": "sport"
                        },
                        {
                            "id": 519,
                            "type": "sport"
                        },
                        {
                            "id": 522,
                            "type": "sport"
                        },
                        {
                            "id": 520,
                            "type": "sport"
                        },
                        {
                            "id": 521,
                            "type": "sport"
                        },
                        {
                            "id": 523,
                            "type": "sport"
                        },
                        {
                            "id": 524,
                            "type": "sport"
                        },
                        {
                            "id": 525,
                            "type": "sport"
                        },
                        {
                            "id": 526,
                            "type": "sport"
                        },
                        {
                            "id": 527,
                            "type": "sport"
                        },
                        {
                            "id": 528,
                            "type": "sport"
                        },
                        {
                            "id": 529,
                            "type": "sport"
                        },
                        {
                            "id": 530,
                            "type": "sport"
                        },
                        {
                            "id": 531,
                            "type": "sport"
                        },
                        {
                            "id": 532,
                            "type": "sport"
                        },
                        {
                            "id": 533,
                            "type": "sport"
                        },
                        {
                            "id": 280,
                            "type": "sport"
                        }
                    ]
                }
            }
        },
       //
    ]
```

This endpoint retrieves all sport groups and allows users to have a bird's eye
view on how our sports are organized an related to one another.

### HTTP Request

`GET https://sports.api.decathlon.com/groups`

### Query Parameters

This endpoint accepts no parameters.

## Querying a single group

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
