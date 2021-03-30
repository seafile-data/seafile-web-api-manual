# invitations


### List invitations

**GET** <https://cloud.seafile.com/api/v2.1/invitations/>

**Sample request**

```
curl -H 'Authorization:Token 934e6351ab287c276a3970a5c32cb34dcec9b737' "https://cloud.seafile.com/api/v2.1/invitations/"

```

**Sample response**

```
[
  {
    "token": "023485d17c1e47f8832d71e3b5e119a9",
    "accept_time": "",
    "expire_time": "2019-07-26T04:07:04+00:00",
    "type": "Guest",
    "invite_time": "2019-07-23T04:07:04+00:00",
    "inviter": "123@qq.com",
    "id": 104,
    "accepter": "test_seafile@qq.com"
  },
  {
    "token": "8755156e210140329cb56504e7008048",
    "accept_time": "",
    "expire_time": "2019-05-23T06:51:57+00:00",
    "type": "Guest",
    "invite_time": "2019-05-20T06:51:57+00:00",
    "inviter": "123@qq.com",
    "id": 103,
    "accepter": "test_seahub@qq.com"
  }
]

```

### Add invitation

**POST** <https://cloud.seafile.com/api/v2.1/invitations/>

**Request parameters**

* type
* accepter

**Sample request**

```
curl -X POST -H 'Authorization:Token 934e6351ab287c276a3970a5c32cb34dcec9b737' "https://cloud.seafile.com/api/v2.1/invitations/"
-d "type=guest&accepter=test_seahub@qq.com"

```

**Sample response**

```
{
  "token": "4cbe5f7b87784d7681cec20bb51c0774",
  "accept_time": "",
  "expire_time": "2019-07-26T07:55:06+00:00",
  "type": "Guest",
  "invite_time": "2019-07-23T07:55:06+00:00",
  "inviter": "123@qq.com",
  "id": 105,
  "accepter": "test_seahub@qq.com"
}

```

**Errors**

* 400 type invalid.
* 400 accepter invalid.
* 400 Email %s invalid.
* 400 The email address is not allowed to be invited as a guest.
* 400 %s is already invited.
* 400 User %s already exists.

### Batch add invitations

**POST** <https://cloud.seafile.com/api/v2.1/invitations/batch/>

**Request parameters**

* type
* accepter

**Sample request**

```
curl -X POST -H 'Authorization:Token 934e6351ab287c276a3970a5c32cb34dcec9b737' "https://cloud.seafile.com/api/v2.1/invitations/batch/"
-d "type=guest&accepter=test_seahub@qq.com&accepter=test_seafile@qq.com"

```

**Sample response**

```
{
  "failed": [
    {
      "email": "test_seahub@qq.com",
      "error_msg": "用户 test_seahub@qq.com 已存在。"
    }
  ],
  "success": [
    {
      "token": "4cbe5f7b87784d7681cec20bb51c0774",
      "accept_time": "",
      "expire_time": "2019-07-26T07:55:06+00:00",
      "type": "Guest",
      "invite_time": "2019-07-23T07:55:06+00:00",
      "inviter": "123@qq.com",
      "id": 105,
      "accepter": "test_seafile@qq.com"
    }
  ]
}

```

**Errors**

* 400 type invalid.
* 400 accepter invalid.

### Get invitation

**GET** <https://cloud.seafile.com/api/v2.1/invitations/{token}/>

**Sample request**

```
curl -H 'Authorization:Token 934e6351ab287c276a3970a5c32cb34dcec9b737' "https://cloud.seafile.com/api/v2.1/invitations/{token}/"

```

**Sample response**

```
{
  "token": "4cbe5f7b87784d7681cec20bb51c0774",
  "accept_time": "",
  "expire_time": "2019-07-26T07:55:06+00:00",
  "type": "Guest",
  "invite_time": "2019-07-23T07:55:06+00:00",
  "inviter": "123@qq.com",
  "id": 105,
  "accepter": "test_seahub@qq.com"
}

```

**Errors**

* 403 Permission denied.
* 404 not found.

### Delete invitation

**DELETE** <https://cloud.seafile.com/api/v2.1/invitations/{token}/>

**Sample request**

```
curl -X DELETE -H 'Authorization:Token 934e6351ab287c276a3970a5c32cb34dcec9b737' "https://cloud.seafile.com/api/v2.1/invitations/{token}/"

```

**Sample response**

```
null

```

**Errors**

* 403 Permission denied.
* 404 not found.

### Revoke invitation

_Note:_ Revoke invitation when the accepter successfully creates an account. And set the account to inactive.

**DELETE** [https://cloud.seafile.com/api/v2.1/invitations/{token}/revoke/](https://cloud.seafile.com/api/v2.1/invitations/%7Btoken%7D/revoke/)

**Sample request**

```
curl -X DELETE -H 'Authorization:Token 934e6351ab287c276a3970a5c32cb34dcec9b737' "https://cloud.seafile.com/api/v2.1/invitations/{token}/revoke/"

```

**Sample response**

```
{"success": true}

```

**Errors**

* 400 The email address didn't accept the invitation.
* 403 Permission denied.
* 404 User %s not found.
* 404 Invitation not found.

