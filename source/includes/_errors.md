# Errors

The Tubman Project API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Application cannot handle your request.
401 | Unauthorized -- The user is not authorized to access the requested resource.
403 | Forbidden -- The user is authenticated but does not have permission to access the requested resource.
404 | Not Found -- Requested resource does not exist.
405 | Method Not Allowed -- The application cannot handle the requested method on the resource.
404 | Not Found -- Requested resource does not exist.
422 | Internal Server Error -- The request was well-formed but was unable to be followed due to semantic errors.
500 | Internal Server Error -- An unexpected condition was encountered.
502 | Bad Gateway -- Internal server error.  The application received an invalid response from the upstream server.
