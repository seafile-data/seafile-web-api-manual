# Department Libraries

The department library is also called group owned library.

## Add Group Owned Library

**POST** http://192.168.1.113:8000/api/v2.1/groups/{group_id}/group-owned-libraries/

**Request parameters**

* `group_id`
* `repo_name`
* `password`
* `permission`, default `rw`.

**Sample request**

```
curl -d "repo_name=group-owned-repo-4&permission=r" -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd' "http://192.168.1.113:8000/api/v2.1/groups/53/group-owned-libraries/"
```

**sample response**

```
{
    "repo_id": "9bc59af9-265e-4110-a0e2-619450a5cb35",
    "permission": "r",
    "encrypted": false,
    "owner_email": "53@seafile_group",
    "mtime": "2018-04-23T17:25:37+08:00",
    "repo_name": "group-owned-repo-4",
    "size": 0
}
```

**Errors**

* 400 repo_name/permission invalid.
* 403 NOT allow to create encrypted library..
* 403 Permission denied.
* 403 No group quota.
* 404 Group not found.

## Delete Group Owned Library

**DELETE** http://192.168.1.113:8000/api/v2.1/groups/{group_id}/group-owned-libraries/{repo_id}/

**Request parameters**

* `group_id`
* `repo_id`

**Sample request**

```
curl -X DELETE -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd' "http://192.168.1.113:8000/api/v2.1/groups/53/group-owned-libraries/9bc59af9-265e-4110-a0e2-619450a5cb35/"
```

**sample response**

```
{"success":true}
```

**Errors**

* 403 Permission denied.
* 404 Group/Library not found.
* 500 Internal Server Error

#### <a id="get-group-owned-library-user-share-info"></a>Get Group Owned Library User Share Info

**GET** http://192.168.1.113:8000/api/v2.1/group-owned-libraries/{repo_id}/user-share/

**Request parameters**

* `repo_id`

**Sample request**

```
curl -H 'Authorization: Token 5eba8c2f983404e33b140b13a1d050b9a4440e03' -H 'Accept: application/json; charset=utf-8; indent=4' "http://192.168.1.113:8000/api/v2.1/group-owned-libraries/4902dcc7-29be-4020-81e9-4e512f97db1e/user-share/"
```

**sample response**

```
[
    {
        "permission": "rw",
        "user_name": "1",
        "user_email": "1@1.com",
        "user_contact_email": "1@1.com"
    },
    {
        "permission": "rw",
        "user_name": "1",
        "user_email": "1@111.com",
        "user_contact_email": "1@111.com"
    },
    {
        "permission": "rw",
        "user_name": "10",
        "user_email": "10@10.com",
        "user_contact_email": "10@10.com"
    }
]
```

**Errors**

* 403 Permission denied.
* 404 Group/Library not found.

## Share Group Owned Library to User

**POST** http://192.168.1.113:8000/api/v2.1/group-owned-libraries/{repo_id}/user-share/

**Request parameters**

* `repo_id`
* `permission`, `r` or `rw`.
* `username`

**Sample request**

```
curl -d "permission=r&username=1@1.com&username=2@1.com" -H 'Authorization: Token 5eba8c2f983404e33b140b13a1d050b9a4440e03' -H 'Accept: application/json; charset=utf-8; indent=4' "http://192.168.1.113:8000/api/v2.1/group-owned-libraries/4902dcc7-29be-4020-81e9-4e512f97db1e/user-share/"
```

**sample response**

```
{
    "failed": [
        {
            "email": "2@1.com",
            "error_msg": "User 2@1.com not found."
        }
    ],
    "success": [
        {
            "permission": "r",
            "user_name": "1",
            "user_email": "1@1.com",
            "user_contact_email": "1@1.com"
        }
    ]
}
```

**Errors**

* 400 permission invalid.
* 403 Permission denied.
* 404 Group/Library not found.

## Modify Group Owned Library User Share Permission

**PUT** http://192.168.1.113:8000/api/v2.1/group-owned-libraries/{repo_id}/user-share/

**Request parameters**

* `repo_id`
* `permission`, `r` or `rw`.
* `username`

**Sample request**

```
curl -X PUT -d "permission=rw&username=1@1.com" -H 'Authorization: Token 5eba8c2f983404e33b140b13a1d050b9a4440e03' -H 'Accept: application/json; charset=utf-8; indent=4' "http://192.168.1.113:8000/api/v2.1/group-owned-libraries/4902dcc7-29be-4020-81e9-4e512f97db1e/user-share/"
```

**sample response**

```
{
    "success": true
}
```

**Errors**

* 400 permission invalid.
* 403 Permission denied.
* 404 Group/Library not found.

## Delete Group Owned Library User Share

**DELETE** http://192.168.1.113:8000/api/v2.1/group-owned-libraries/{repo_id}/user-share/

**Request parameters**

* `repo_id`
* `username`

**Sample request**

```
curl -X DELETE -d "username=1@1.com" -H 'Authorization: Token 5eba8c2f983404e33b140b13a1d050b9a4440e03' -H 'Accept: application/json; charset=utf-8; indent=4' "http://192.168.1.113:8000/api/v2.1/group-owned-libraries/4902dcc7-29be-4020-81e9-4e512f97db1e/user-share/"
```

**sample response**

```
{
    "success": true
}
```

**Errors**

* 403 Permission denied.
* 404 Group/Library not found.

## Get Group Owned Library Group Share Info

**GET** http://192.168.1.113:8000/api/v2.1/group-owned-libraries/{repo_id}/group-share/

**Request parameters**

* `repo_id`

**Sample request**

```
curl -H 'Authorization: Token 5eba8c2f983404e33b140b13a1d050b9a4440e03' -H 'Accept: application/json; charset=utf-8; indent=4' "http://192.168.1.113:8000/api/v2.1/group-owned-libraries/4902dcc7-29be-4020-81e9-4e512f97db1e/group-share/"
```

**sample response**

```
[
    {
        "permission": "r",
        "group_id": 71,
        "group_name": "asd"
    },
    {
        "permission": "r",
        "group_id": 70,
        "group_name": "group-of-lian"
    }
]
```

**Errors**

* 403 Permission denied.
* 404 Group/Library not found.

## Share Group Owned Library to Group

**POST** http://192.168.1.113:8000/api/v2.1/group-owned-libraries/{repo_id}/group-share/

**Request parameters**

* `repo_id`
* `permission`, `r` or `rw`.
* `group_id`

**Sample request**

```
curl -d "permission=r&group_id=89&group_id=71&group_id=70" -H 'Authorization: Token 5eba8c2f983404e33b140b13a1d050b9a4440e03' -H 'Accept: application/json; charset=utf-8; indent=4' "http://192.168.1.113:8000/api/v2.1/group-owned-libraries/4902dcc7-29be-4020-81e9-4e512f97db1e/group-share/"
```

**sample response**

```
{
    "failed": [
        {
            "error_msg": "Group 89 not found"
        },
        {
            "error_msg": "This item has been shared to asd.",
            "group_name": "asd"
        }
    ],
    "success": [
        {
            "permission": "r",
            "group_id": 70,
            "group_name": "group-of-lian"
        }
    ]
}
```

**Errors**

* 400 permission invalid.
* 403 Permission denied.
* 404 Group/Library not found.

## Modify Group Owned Library Group Share Permission

**PUT** http://192.168.1.113:8000/api/v2.1/group-owned-libraries/{repo_id}/group-share/

**Request parameters**

* `repo_id`
* `permission`, `r` or `rw`.
* `group_id`

**Sample request**

```
curl -X PUT -d "permission=rw&group_id=70" -H 'Authorization: Token 5eba8c2f983404e33b140b13a1d050b9a4440e03' -H 'Accept: application/json; charset=utf-8; indent=4' "http://192.168.1.113:8000/api/v2.1/group-owned-libraries/4902dcc7-29be-4020-81e9-4e512f97db1e/group-share/"
```

**sample response**

```
{
    "success": true
}
```

**Errors**

* 400 permission invalid.
* 403 Permission denied.
* 404 Group/Library not found.

## Delete Group Owned Library Group Share

**DELETE** http://192.168.1.113:8000/api/v2.1/group-owned-libraries/{repo_id}/group-share/

**Request parameters**

* `repo_id`
* `group_id`

**Sample request**

```
curl -X DELETE -d "group_id=71" -H 'Authorization: Token 5eba8c2f983404e33b140b13a1d050b9a4440e03' -H 'Accept: application/json; charset=utf-8; indent=4' "http://192.168.1.113:8000/api/v2.1/group-owned-libraries/4902dcc7-29be-4020-81e9-4e512f97db1e/group-share/"
```

**sample response**

```
{
    "success": true
}
```

**Errors**

* 403 Permission denied.
* 404 Group/Library not found.

## Modify Group Owned Library Sub-Folder Permission

**PUT** http://192.168.1.113:8000/api/v2.1/groups/{group_id}/group-owned-libraries/{repo_id}/

**Request parameters**

* `group_id`
* `repo_id`
* `path`, path of sub folder.
* `permission`: `r` or `rw`.

**Sample request**

```
curl -X PUT -d "path=/tmp/&permission=r" -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd' "http://192.168.1.113:8000/api/v2.1/groups/53/group-owned-libraries/9bc59af9-265e-4110-a0e2-619450a5cb35/"
```

**sample response**

```
{"success":true}
```

**Errors**

* 400 path/permission invalid.
* 403 Permission denied.
* 404 Group/Library/Folder not found.
* 500 Internal Server Error
