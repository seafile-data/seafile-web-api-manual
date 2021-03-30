# Seafile Web API

## API Basics

All API calls must be authenticated with a valid Seafile API key.

```
curl -H 'Authorization: Token 24fd3c026886e3121b2ca630805ed425c272cb96' https://cloud.seafile.com/api2/auth/ping/

```

The api key can be retrieved by the obtain auth api. See `Quick Start` below.

For each API, we provide `curl` examples to illustrate the usage. We also provide `python` and `javascript` examples, please refer to <https://github.com/haiwen/webapi-examples> for details.

## Status Code

* 200: OK
* 201: CREATED
* 202: ACCEPTED
* 301: MOVED_PERMANENTLY
* 400: BAD_REQUEST
* 403: FORBIDDEN
* 404: NOT_FOUND
* 409: CONFLICT
* 429: TOO_MANY_REQUESTS
* 440: REPO_PASSWD_REQUIRED
* 441: REPO_PASSWD_MAGIC_REQUIRED
* 500: INTERNAL_SERVER_ERROR
* 520: OPERATION_FAILED

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

## User APIs

See [v2.1 User APIs](v2.1)

## Admin APIs

See [v2.1 Admin APIs](v2.1-admin)
