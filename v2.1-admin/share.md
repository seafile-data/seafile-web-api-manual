# Share

## Get Repo User Shares

Available for Seafile v6.0.1+

**GET** https://cloud.seafile.com/api/v2.1/admin/shares/?repo_id={repo_id)&share_type={share_type}

**Request parameters**

* repo_id
* share_type

**Sample request**

    curl -H "Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd" -H 'Accept: application/json; indent=4' 'https://cloud.seafile.com/api/v2.1/admin/shares/?repo_id=ddd42241-e003-425d-960e-0f9f7144866f&share_type=user'

**Sample response**

```
[
    {
        "repo_id": "ddd42241-e003-425d-960e-0f9f7144866f",
        "share_type": "user",
        "permission": "r",
        "path": "/",
        "user_name": "name of user 2",
        "user_email": "2@2.com"
    }
]
```

**Errors**

* 400 repo_id invalid.
* 400 share_type invalid.
* 403 Permission denied.
* 404 Library not found.
* 404 Folder not found.

## Get Repo Group Shares

Available for Seafile v6.0.1+

**GET** https://cloud.seafile.com/api/v2.1/admin/shares/?repo_id={repo_id)&share_type={share_type}

**Request parameters**

* repo_id
* share_type

**Sample request**

    curl -H "Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd" -H 'Accept: application/json; indent=4' 'https://cloud.seafile.com/api/v2.1/admin/shares/?repo_id=ddd42241-e003-425d-960e-0f9f7144866f&share_type=group'

**Sample response**

```
[
    {
        "repo_id": "ddd42241-e003-425d-960e-0f9f7144866f",
        "share_type": "group",
        "permission": "rw",
        "group_name": "group-of-lian-2",
        "path": "/",
        "group_id": 2
    }
]
```

**Errors**

* 400 repo_id invalid.
* 400 share_type invalid.
* 403 Permission denied.
* 404 Library not found.
* 404 Folder not found.

## Share Repo to User

Available for Seafile v6.0.1+

**POST** https://cloud.seafile.com/api/v2.1/admin/shares/

**Request parameters**

* repo_id
* share_type
* share_to (user email)
* permission

**Sample request**

    curl -d "repo_id=ddd42241-e003-425d-960e-0f9f7144866f&share_type=user&permission=r&share_to=1@1.com&share_to=invalid@email.com" -H "Authorization: Token 9c845638b855e549c07ff81be2a0471aa52810d7" -H 'Accept: application/json; indent=4' 'https://cloud.seafile.com/api/v2.1/admin/shares/'

**Sample response**

```
{
    "failed": [
        {
            "error_msg": "User invalid@email.com not found.",
            "user_email": "invalid@email.com"
        }
    ],
    "success": [
        {
            "repo_id": "ddd42241-e003-425d-960e-0f9f7144866f",
            "share_type": "user",
            "permission": "r",
            "path": "/",
            "user_name": "name of user 1",
            "user_email": "1@1.com"
        }
    ]
}
```

**Errors**

* 400 repo_id invalid.
* 400 share_type invalid.
* 403 Permission denied.
* 404 Library not found.
* 404 Folder not found.
* 500 Internal Server Error

## Share Repo to Group

Available for Seafile v6.0.1+

**POST** https://cloud.seafile.com/api/v2.1/admin/shares/

**Request parameters**

* repo_id
* share_type
* share_to (group_id)
* permission

**Sample request**

    curl -d "repo_id=ddd42241-e003-425d-960e-0f9f7144866f&share_type=group&permission=r&share_to=1&share_to=1232" -H "Authorization: Token 9c845638b855e549c07ff81be2a0471aa52810d7" -H 'Accept: application/json; indent=4' 'https://cloud.seafile.com/api/v2.1/admin/shares/'

**Sample response**

```
{
    "failed": [
        {
            "group_id": 1232,
            "error_msg": "Group %s not found"
        }
    ],
    "success": [
        {
            "repo_id": "ddd42241-e003-425d-960e-0f9f7144866f",
            "share_type": "group",
            "permission": "r",
            "group_name": "group-of-lian",
            "path": "/",
            "group_id": 1
        }
    ]
}
```

**Errors**

* 400 repo_id invalid.
* 400 share_type invalid.
* 403 Permission denied.
* 404 Library not found.
* 404 Folder not found.
* 500 Internal Server Error

## Modify Repo User Share Permission

Available for Seafile v6.0.1+

**PUT** https://cloud.seafile.com/api/v2.1/admin/shares/

**Request parameters**

* repo_id
* share_type
* share_to (user email)
* permission

**Sample request**

    curl -X PUT -d "repo_id=ddd42241-e003-425d-960e-0f9f7144866f&share_type=user&permission=rw&share_to=1@1.com" -H "Authorization: Token 9c845638b855e549c07ff81be2a0471aa52810d7" -H 'Accept: application/json; indent=4' 'https://cloud.seafile.com/api/v2.1/admin/shares/'

**Sample response**

```
{
    "repo_id": "ddd42241-e003-425d-960e-0f9f7144866f",
    "share_type": "user",
    "permission": "rw",
    "path": "/",
    "user_name": "name of user 1",
    "user_email": "1@1.com"
}
```

**Errors**

* 400 repo_id invalid.
* 400 share_type invalid.
* 403 Permission denied.
* 404 Library not found.
* 404 Folder not found.
* 500 Internal Server Error

## Modify Repo Group Share Permission

Available for Seafile v6.0.1+

**PUT** https://cloud.seafile.com/api/v2.1/admin/shares/

**Request parameters**

* repo_id
* share_type
* share_to (group_id)
* permission

**Sample request**

    curl -X PUT -d "repo_id=ddd42241-e003-425d-960e-0f9f7144866f&share_type=group&permission=rw&share_to=1" -H "Authorization: Token 9c845638b855e549c07ff81be2a0471aa52810d7" -H 'Accept: application/json; indent=4' 'https://cloud.seafile.com/api/v2.1/admin/shares/'

**Sample response**

```
{
    "repo_id": "ddd42241-e003-425d-960e-0f9f7144866f",
    "share_type": "group",
    "permission": "rw",
    "group_name": "group-of-lian",
    "path": "/",
    "group_id": 1
}
```

**Errors**

* 400 repo_id invalid.
* 400 share_type invalid.
* 403 Permission denied.
* 404 Library not found.
* 404 Folder not found.
* 500 Internal Server Error

## Delete Repo User Share

Available for Seafile v6.0.1+

**DELETE** https://cloud.seafile.com/api/v2.1/admin/shares/

**Request parameters**

* repo_id
* share_type
* share_to (user email)

**Sample request**

    curl -X DELETE -d "repo_id=ddd42241-e003-425d-960e-0f9f7144866f&share_type=user&share_to=1@1.com" -H "Authorization: Token 9c845638b855e549c07ff81be2a0471aa52810d7" -H 'Accept: application/json; indent=4' 'https://cloud.seafile.com/api/v2.1/admin/shares/'

**Sample response**

```
{
    "success": true
}
```

**Errors**

* 400 repo_id invalid.
* 400 share_type invalid.
* 403 Permission denied.
* 404 Library not found.
* 404 Folder not found.
* 500 Internal Server Error

## Delete Repo Group Share

Available for Seafile v6.0.1+

**DELETE** https://cloud.seafile.com/api/v2.1/admin/shares/

**Request parameters**

* repo_id
* share_type
* share_to (group id)

**Sample request**

    curl -X DELETE -d "repo_id=ddd42241-e003-425d-960e-0f9f7144866f&share_type=group&share_to=1" -H "Authorization: Token 9c845638b855e549c07ff81be2a0471aa52810d7" -H 'Accept: application/json; indent=4' 'https://cloud.seafile.com/api/v2.1/admin/shares/'

**Sample response**

```
{
    "success": true
}
```

**Errors**

* 400 repo_id invalid.
* 400 share_type invalid.
* 403 Permission denied.
* 404 Library not found.
* 404 Folder not found.