# 15. Errors

The Joinup API uses the following error status codes:


Status Code | Meaning
---------- | -------
400 | Bad Request -- Your request is invalid. Your request does not pass some validation
401 | Unauthorized -- Your auth header is wrong or it was not provided
403 | Forbidden -- User in impersonate header can not do this action
404 | Not Found -- The resource does not exists or the resource belongs to another user
405 | Method Not Allowed -- You tried to access our API with an invalid method
500 | Internal Server Error -- We had a problem with our server. Try again later
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later
