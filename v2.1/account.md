# Account

## Check Account Info

**GET** <https://cloud.seafile.com/api2/account/info/>

**Sample request**

```
curl -H "Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api2/account/info/

```

**Sample response**

```
{
    "login_id": "",
    "is_staff": true,
    "name": "foo",
    "email_notification_interval": 0,
    "institution": "",
    "department": "",
    "avatar_url": "http://127.0.0.1:8000/media/avatars/default.png",
    "contact_email": null,
    "space_usage": "73.40217%",
    "usage": 22020651,
    "total": 30000000,
    "email": "foo@foo.com"
}

```

**Errors**

* 403 Invalid token

## Get Client Login URL

You can use this API to get a URL to login into the Web interface. The usage case is to provide the feature of "Visit web site" in the clients.

**GET** <https://cloud.seafile.com/api2/client-login/>

**Sample request**

```
curl -H "Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd" https://cloud.seafile.com/api2/client-login/

```

**Sample response**

_Note_:

* If the user has two way authentication enabled, the server will respond with an empty JSON object (`{}`).


```
"https://cloud.seafile.com/client-login/?token=000f1f83d612836c65fed087fb9c4ca40852d0f9"

```

**Errors**

* 403 Invalid token


