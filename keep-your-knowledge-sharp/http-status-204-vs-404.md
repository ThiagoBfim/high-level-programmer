---
description: Should I use 204 or 404 ?
---

# HTTP Status 204 vs 404

The HTTP Status 204 means that it's a successful request, but doesn't have a response body, while the 404 means the resource doesn't exist.

In the [RFC5789 - HTTP PATCH](https://datatracker.ietf.org/doc/html/rfc5789#section-2.2) we find that:

> _Resource not found: Can be specified with a 404 (Not Found) status code when the client attempted to apply a patch document to a non-existent resource, but the patch document chosen cannot be applied to a non-existent resource._

In the book _REST API - Design Rulebook by Mark Masse_ we find that:

> _Once a DELETE request has been processed for a given resource, the resource can no longer be found by clients. Therefore, any future attempt to retrieve the resource’s state representation, using either GET or HEAD, must result in a 404 (“Not Found”) status returned by the API._

On the other hand, the Azure API has this recommendation:

> _"DO return a 204-No Content without a resource/body for a DELETE operation (even if the URL identifies a resource that does not exist; do not return 404-Not Found)"_

### Conclusion

The good old answer is it depends. It depends on your API usage, for example, if it's a private API, maybe align with the team that's going to use it and create a common standard. The key here is having a common pattern and sticking to it.

### References:

**REST API - Design Rulebook**\
**-** Mark Masse

[AZURE API Guidelines](https://github.com/microsoft/api-guidelines/blob/vNext/azure/Guidelines.md)
