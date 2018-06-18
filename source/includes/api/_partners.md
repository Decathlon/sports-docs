# Partners

## Search for Partners

```shell
curl "https://partners-api.herokuapp.com/api/v1/partners"
```

> JSON response:

```json
{
  "title": "Running Group",
  "source": "meetup",
  "description": null,
  "link": "http://meetup.com/runninggroupMTL",
  "featured": true,
  "partner": false,
  "city": "Montreal",
  "country": "Canada",
  "lat": "45.522938",
  "lng": "-73.581507",
  "radius": 10,
  "province": "QC",
  "image_ref": null,
  "uuid": "1cf32619-eb83-488d-bbf0-2a72b7f8fd79",
  "user_id": 0,
  "sports": [
    { "sport": 123 },
    { "sport": 456 },
    { "sport": 789 }
  ]
}

```

This endpoint retrieves all partners meeting specific criteria


### HTTP Request

`GET https://partners-api.herokuapp.com/api/v1/partners`

### Query Parameters

Most parameters are optional.

Coordinates (`lat`, `lng`) are comma separated string representations of geographic locations.

Search query errors will be responded to with specific error information, and an `HTTP 422` status code.

Parameter | Example          | Description
--------- | -------          | -----------
sport     | `175`            | Filters results based on Decathlon Sport ID
nearby[]  | `'45.91,-73,58'` | The current location of the end-user making the request. Used to calculate proximity.
featured  | `true`           | Boolean representing whether a partner should be featured or not
partner   | `false`          | Boolean representing whether a partner is a Décathlon partner
page      | `1`              | For performance reasons, results are paginated by 25 items per page


## Adding Communities

```shell
curl 
  -X POST 
  -H "Content-Type: application/json" 
  -d "@data.json" 
  https://partners-api.herokuapp.com/api/v1/partners
```

> JSON request [@data.json]

```json
{
  "partner": {
    "title": "hello",
    "featured": false,
    "partner": false,
    "link": "http://example.com",
    "source": "google",
    "lat": 45.522938,
    "lng": -73.581507,
    "city": "Montreal",
    "province": "QC",
    "country": "CA",
    "description": "lorem ipsum dolor amet sit...",
    "sports_attributes": [
      { "sport": 123 },
      { "sport": 789 }
    ]
  }
}
```

This endpoint creates partners based on a Sport ID.

### HTTP Request

`POST https://partners-api.herokuapp.com/api/v1/partners`

### Request Parameters

`user_id`, `title`, `source`, `link`, `lat`, `lng` and the `sport_attributes` array are mandatory.

`country` accepts a 2-letter country code according to the [ISO 3166-1 alpha 2 standard](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2)

The `sport_attributes` must carry at least 1 sport.

## Updating/Editing Communities
```shell
curl
  -X PUT
  -H "Content-Type: application/json"
  -d "@data.json"
  https://partners-api.herokuapp.com/api/v1/partners/:partner_id
```

> JSON request [@data.json]

```json
{
  "partner": {
    "title": "Updated Title"
  }
}
```
This endpoint updates partners parameters.

### HTTP Request

`POST https://partners-api.herokuapp.com/api/v1/partners/:partner_id`

> JSON response

```json

{
  "partner": {
    "title": "Updated Title",
    "featured": false,
    "partner": false,
    "link": "http://example.com",
    "source": "google",
    "lat": "45.522938",
    "lng": "-73.581507",
    "city": "Montreal",
    "province": "QC",
    "country": "CA",
    "description": "lorem ipsum dolor amet sit...",
    "sports_attributes": [
      { "sport": 123 },
      { "sport": 789 }
    ]
  }
}
```
> Errors

Errors will be responded to with specific error information, and an `HTTP 422` status code.
