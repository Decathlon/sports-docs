# Errors

The Sports API renders the following error codes:

Error Code | Meaning
---------- | -------
400        | Bad Request -- Your request is invalid - check the JSON format of your request.
401        | Unauthorized -- There's a problem with your credentials.
404        | Not Found -- We can't find the data you're looking for.
422        | Unprocessable Entity -- There was a validation error with your request.
500        | Internal Server Error -- We had a problem with our server. Try again later.
