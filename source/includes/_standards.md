# Standards

## Versioning

Since `V2` of our API, we've adopted a header-based versioning rather than a
path-based standard.

To select the version of our API you would like to use, simply pass in the
following header parameter with your request. (Replace `v2` with the desired
version)

```Accept: application/vnd.decathlon.v2+json```

If no parameters are passed in, we'll serve up the latest stable version of our
API

<aside class="notice">
  For legacy purposes, the V1 of this API is still accessible at /api/v1/sports.
</aside>

## Pagination

Pagination links (next, previous, first and last) are part of the response
header `Link`. 
For convenience we've added the number of results `Per-Page` and the `Total` of
results returned.

This follows the [RFC 5988 Proposal](https://tools.ietf.org/html/rfc5988) for
standard Web Linking.

## Localization

Our API supports localization of the sports names. Such data can be retrieved by
passing in the preferred locale in the request header, as such:

`Accept-Language: fr-CA`

<h2> </h2>
