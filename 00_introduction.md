<span class="product-title">Sports API</span>

sports.api.decathlon.com provides a RESTful API that allows you to lookup intelligence, data and content related to sports.

#Getting started

> Sport Data Structure

```json
    {
    "id": 66,
    "type": "sport",
    "attributes": {
        "name": "Skiing",
        "description": "On your skis, these longs and narrows kinds of skates, you can practice several disciplines that will transport you, for fun or during competitions, in the heart of the most beautiful winter landscapes. You’ll be able to ride down the hills at a fast pace and execute controlled turns, allowing you to take fresh air and strengthen your cardiovascular system. Have a fun ride!",
        "parent_id": null,
        "decathlon_id": 66,
        "slug": "skiing",
        "locale": "en",
        "weather": []
    },
    "relationships": {
        "children": {
            "data": [
                {
                    "id": 67,
                    "type": "sport"
                },
                {
                    "id": 785,
                    "type": "sport"
                },
                {
                    "id": 786,
                    "type": "sport"
                },
                {
                    "id": 787,
                    "type": "sport"
                },
                {
                    "id": 788,
                    "type": "sport"
                },
                {
                    "id": 789,
                    "type": "sport"
                },
                {
                    "id": 790,
                    "type": "sport"
                },
                {
                    "id": 791,
                    "type": "sport"
                },
                {
                    "id": 792,
                    "type": "sport"
                },
                {
                    "id": 68,
                    "type": "sport"
                }
            ]
        },
        "parent": {
            "data": null
        },
        "group": {
            "data": {
                "id": 22,
                "type": "group"
            }
        },
        "related": {
            "data": [
                {
                    "id": 156,
                    "type": "sport"
                },
                {
                    "id": 328,
                    "type": "sport"
                },
                {
                    "id": 70,
                    "type": "sport"
                }
            ]
        },
        "tags": {
            "data": [
                "downhill-skiing",
                "extreme-skiing",
                "giant-slalom",
                "glade-skiing",
                "grass-skiing",
                "skiing-on-grass",
                "para-alpine-skiing",
                "slalom",
                "speed-skiing",
                "super-g",
                "skis",
                "descent",
                "ski-station",
                "ski-slope",
                "glading"
            ]
        },
        "images": {
            "data": [
                {
                    "id": 170,
                    "url": "https://sports.api.decathlon.com/rails/active_storage/blobs/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBYW89IiwiZXhwIjpudWxsLCJwdXIiOiJibG9iX2lkIn19--150627d59a77c19909396ed9ee88146eb35f2f26/ski.jpg",
                    "meta": {
                        "width": 500,
                        "height": 333
                    },
                    "variants": [
                        {
                            "thumbnail": {
                                "url": "https://sports.api.decathlon.com/rails/active_storage/representations/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBYW89IiwiZXhwIjpudWxsLCJwdXIiOiJibG9iX2lkIn19--150627d59a77c19909396ed9ee88146eb35f2f26/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaDdCam9MY21WemFYcGxTU0lJTWpBd0Jqb0dSVlE9IiwiZXhwIjpudWxsLCJwdXIiOiJ2YXJpYXRpb24ifX0=--8ed889d31ac3a5e9d5446846a4f7747f8eaa0bc1/ski.jpg"
                            },
                            "medium": {
                                "url": "https://sports.api.decathlon.com/rails/active_storage/representations/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaHBBYW89IiwiZXhwIjpudWxsLCJwdXIiOiJibG9iX2lkIn19--150627d59a77c19909396ed9ee88146eb35f2f26/eyJfcmFpbHMiOnsibWVzc2FnZSI6IkJBaDdCam9MY21WemFYcGxTU0lKTVRBeU5BWTZCa1ZVIiwiZXhwIjpudWxsLCJwdXIiOiJ2YXJpYXRpb24ifX0=--0e36b4a54e8a5057a18945f67d3ad11a9ef22382/ski.jpg"
                            }
                        }
                    ]
                }
            ]
        }
    }
}
```

**Authentication**

No authentication is required. The API is fully OPEN and will stay as such. Keep in mind that a throttle will eventually be imposed on users that have not registered for an key.


**Make your first API call**

You are ready to go! We suggest making your first API call by querying for popular <a href="#recommendations">sports recommendations near you </a>


<div style="display: none">
Signup to our newsletter to be made aware of the upcoming changes

 ##Tutorial

<div style="margin-left:14px">
<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/EwGpd5bnrzU" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

</div>
