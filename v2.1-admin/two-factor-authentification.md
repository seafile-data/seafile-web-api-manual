# Two Factor Authentification

## Set/Unset Force 2FA for User

**PUT** <https://cloud.seafile.com/api2/two-factor-auth/{email}/>

**Request parameters**

* force_2fa, 1 or 0, represent set or unset force 2FA for user.

**Sample request**

```
curl -X PUT -d "force_2fa=1" -H "Authorization: Token 4c3fa38f9f2fee40485446afdee7a23749cb6911" -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api2/two-factor-auth/foo@foo.com/"

```

**Sample response**

```
{
    "success": true
}

```

**Errors**

* 400 user not found.
* 500 Internal Server Error.

## Delete Verified Devices

**DELETE** <https://cloud.seafile.com/api2/two-factor-auth/{email}/>

Remove records from devices that have been verified by 2-step verification. These devices will require 2-step verification the next time they log in.

**Sample request**

```
curl -X DELETE -H "Authorization: Token 4c3fa38f9f2fee40485446afdee7a23749cb6911" -H 'Accept: application/json; charset=utf-8; indent=4' https://cloud.seafile.com/api2/two-factor-auth/foo@foo.com/

```

**Sample response**

```
{
    "success": true
}

```

**Errors**

* 400 email can not be empty, or user not found.
* 500 Internal Server Error.


