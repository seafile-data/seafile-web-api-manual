# Seafile Web API

## Note

The API document has been moved to [https://seafile-api.readme.io/reference/introduction](https://seafile-api.readme.io/reference/introduction "https://seafile-api.readme.io/reference/introduction")

## API Basics

All API calls must be authenticated with a valid Seafile API key.

```
curl -H 'Authorization: Token 24fd3c026886e3121b2ca630805ed425c272cb96' https://cloud.seafile.com/api2/auth/ping/
```

The api key can be retrieved by the obtain auth api. See `Quick Start` below.

## Status Code

* 200: OK

* 201: CREATED

* 202: ACCEPTED

* 301: MOVED\_PERMANENTLY

* 400: BAD\_REQUEST

* 403: FORBIDDEN

* 404: NOT\_FOUND

* 409: CONFLICT

* 429: TOO\_MANY\_REQUESTS

* 440: REPO\_PASSWD\_REQUIRED

* 441: REPO\_PASSWD\_MAGIC\_REQUIRED

* 500: INTERNAL\_SERVER\_ERROR

* 520: OPERATION\_FAILED

## Quick Start

**ping**

```
curl https://cloud.seafile.com/api2/ping/
"pong"
```

**obtain auth token**

```
curl -d "username=username@example.com&password=123456" https://cloud.seafile.com/api2/auth-token/
{"token": "24fd3c026886e3121b2ca630805ed425c272cb96"}
```

you should use `--data-urlencode` if you want to process some special characters properly.

```
curl --data-urlencode username=user+name@example.com -d password=123456 https://cloud.seafile.com/api2/auth-token/
{"token":"265757b0a5aaf5d6b2e266d0c21791121ce6cdec"}
```

If you have enabled two-factor authentication, you need to add 2FA header in HTTP when getting the access token:

```
curl -d "username=username@example.com&password=123456" -H 'X-SEAFILE-OTP: <token>' https://cloud.seafile.com/api2/auth-token/
```

**auth ping**

```
curl -H 'Authorization: Token 24fd3c026886e3121b2ca630805ed425c272cb96' https://cloud.seafile.com/api2/auth/ping/
"pong"
```

