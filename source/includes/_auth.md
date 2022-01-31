# Authentication, Authorization & Impersonate

> To authorization, use this code when we are creating an user:


```shell
curl "api_endpoint_here" \
  -H "Authorization: JWT beep-beep-beep-beep-beep"
```

> Or use this another code when we are accessing to another endpoint (authorization with your private token, and authentication with username of the user):

```shell
curl "api_endpoint_here" \
  -H "Authorization: JWT beep-beep-beep-beep-beep" \
  -H "Impersonate: foo.bar@example.com"
```

> Make sure to replace `beep-beep-beep-beep-beep` with your private token.

Joinup API expects for the token to be included in all API requests to the server in a header that looks like the following:

`Authorization: beep-beep-beep-beep-beep`

<aside class="notice">
You must replace <code>beep-beep-beep-beep-beep</code> with your token.
</aside>