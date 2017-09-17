# Errors

The WebCode.How API uses the following error codes to give context to why requests failed.

Please review the codes and try to resolve issues on your own before contacting us. You can
check our status page at [status.webcode.how](http://status.webcode.how) to see if there's
a larger issue affecting multiple clients.

Our status page checks all of our endpoints, so you can see if a particular endpoint is having
issues.

## Client Errors

```json
{
  "error": {
    "code": 400,
    "message": "Bad Request: Your request is invalid"
  }
}
```

```xml
<?xml version="1.0" encoding="utf-8" ?>
<error>
  <code>400</code>
  <message>Bad Request: Your request is invalid</message>
</error>
```

If you get a 400-series error code, it's an issue on your end. Please review documentation on
the endpoints you're using as well as your own code before filing an issue.

Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is invalid.
403 | Forbidden -- You are not allowed to access the resource.
404 | Not Found -- Requested object could not be found.
405 | Method Not Allowed | Given HTTP method is not available on a resource.
410 | Gone -- Request object has been deleted.
415 | Unsupported Type -- Request not available in the given format.
418 | I'm a Teapot -- Pour yourself some tea over at `/teapot`.
429 | Too Many Requests -- You have made too many requests in too short of a time.
451 | Blocked for Legal Reasons -- Request object has been denied because of legal issues.

## Server Errors

```json
{
  "error": {
    "code": 500,
    "message": "Internal Server Error: Could not respond"
  }
}
```

```xml
<?xml version="1.0" encoding="utf-8" ?>
<error>
  <code>500</code>
  <message>Internal Server Error: Could not respond</message>
</error>
```

If you get a 500-series error code, it's an issue on our end. We review erorr logs frequently
and will attempt to resolve them as fast as possible.

Error Code | Meaning
---------- | -------
500 | Internal Server Error -- We had a problem with our server. Try again later.
501 | Not Implemented -- This endpoint has not been implemented. Submit a request to info@webcode.how for more info.
502 | Bad Gateway -- Our load balancers are having issues. Please try again with exponential backoff.
503 | Service Unavailable -- Our servers are down. Please try again with exponential backoff.
504 | Timeout -- Our servers are having a hard time keeping up with load. Please try again with exponential backoff.
