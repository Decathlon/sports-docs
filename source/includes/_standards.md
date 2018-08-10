# Standards

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
