# Sports

## List Sports

```shell
curl "https://sports-decathlon.herokuapp.com/sports"
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
                "slug": "body-building-cross-training-dc159b85-6e37-4910-8f78-011ec1c2a041",
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

`GET https://sports-decathlon.herokuapp.com/sports`

### Query Parameters

Search query errors will be responded to with specific error information, and an `HTTP 404` status code.

Parameter | Example          | Description
--------- | -------          | -----------
page      | `1`              | For performance reasons, results are paginated by 10 items per page
q         | `soccer`         | Query a sport by its name, using a string for searching

## Querying a single Sport

```shell
curl "https://sports-decathlon.herokuapp.com/sports/swimming"
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

This endpoint retrieves a sport and its children, if any.
The ID can be passed in as either the `slug` column or the `id` column, for
convenience.
If a sport does not have children, or if it's already a child, the relationship
object will return `null`.
If a sport is a child, the `parent_id` column will display the ID of its parent.

### HTTP Request

`GET https://sports-decathlon.herokuapp.com/sports/278`

### Query Parameters

Search query errors will be responded to with specific error information, and an `HTTP 404` status code.

## Sport Recommendations

```shell
curl
"https://sports-decathlon.herokuapp.com/sports/:sport_id/recommendations"
```

> JSON Response

```json
[ "123", "456", "789" ]
```

This endpoint provides sport recommendations based on AI.

Parameter | Example | Description
--------- | ------- | -----------
sport_id  | `175`   | Sport ID
count     | `5`     | Number of recommendations (Default: 3)


### HTTP Request

`GET https://sports-decathlon.herokuapp.com/sports/175/recommendations`

### Query Parameters

Search query errors will be responded to with specific error information, and an `HTTP 404` status code.
