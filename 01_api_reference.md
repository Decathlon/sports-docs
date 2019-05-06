# API Reference

## List Sports

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

## Sport recommendations by popularity

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

## Sport recommendations by location

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


### HTTP Request

`GET https://sports.api.decathlon.com/sports/175/recommendations`

### Query Parameters

Search query errors will be rescued with specific error messages, and an `HTTP 404` status code.
