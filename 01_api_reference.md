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

Sports are dynamically displayed regarding their popularity in Canada


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
        "id": "224",
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
In the case a sport is a parent, the relationship object return a `relateds` column wich display parent sports ID's powered by AI algorithms on a corpus of sports descriptions.
### HTTP Request

`GET https://sports.api.decathlon.com/sports/224`

### Query Parameters

Search query errors will be rescued with specific error messages, and an `HTTP 404` status code.

## Fetching recommendations by city

```shell
curl
"https://sports.api.decathlon.com/sports/recommendations/:location"
```

> JSON Response

```json
 "data": [
    {
            "id": 147,
            "type": "sport",
            "attributes": {
                "name": "Hiking",
                "description": null,
                "parent_id": null,
                "decathlon_id": 458,
                "slug": "hiking",
                "locale": "en"
            },
            "relationships": {
                "children": {
                    "data": [
                        {
                            "id": 46,
                            "type": "sport"
                        },
                        {
                            "id": 438,
                            "type": "sport"
                        },
                        {
                            "id": 441,
                            "type": "sport"
                        },
                        {
                            "id": 440,
                            "type": "sport"
                        },
                        {
                            "id": 625,
                            "type": "sport"
                        },
                        {
                            "id": 626,
                            "type": "sport"
                        },
                        {
                            "id": 627,
                            "type": "sport"
                        },
                        {
                            "id": 439,
                            "type": "sport"
                        }
                    ]
                },
                "parent": {
                    "data": null
                },
                "group": {
                    "data": {
                        "id": 9,
                        "type": "group"
                    }
                },
                "tags": {
                    "data": ""
                },
                "images": {
                    "data": []
                }
            }
        },
        {
            "id": 284,
            "type": "sport",
            "attributes": {
                "name": "Hybrid biking",
                "description": null,
                "parent_id": null,
                "decathlon_id": 284,
                "slug": "hybrid-biking",
                "locale": "en"
            },
            "relationships": {
                "children": {
                    "data": [
                        {
                        ...
```

This endpoint provides sport recommendations based on popularity within a city and AI algorithms.

Parameter | Example       | Description
--------- | -------       | -----------
location  | `montreal_ca` | City name and 2-letter country code
count     | `5`           | Number of recommendations (Default: 3)


### HTTP Request

`GET https://sports.api.decathlon.com/sports/recommendations/montreal_ca`

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
