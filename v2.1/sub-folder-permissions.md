# Sub Folder Permissions

Folder Permissions is for Fine-grained Access Control.

## Get User Folder Permission

**GET** https://cloud.seafile.com/api2/repos/{repo_id}/user-folder-perm/?folder_path=/123

**Request parameters**

* repo_id
* folder_path

**Sample request**

```
curl -H 'Authorization: Token cbd7705c06846425ed5c46ae0313d5b098d24154' -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api2/repos/bdf816e6-aba8-468c-962f-77c2fcfd1d1c/user-folder-perm/?folder_path=/123"
```

**Sample response**

```
    [
        {
        "repo_id": "bdf816e6-aba8-468c-962f-77c2fcfd1d1c",
        "folder_path": "/123",
        "permission": "r",
        "folder_name": "123",
        "user_name": "1",
        "user_email": "1@1.com"
    },
    {
        "repo_id": "bdf816e6-aba8-468c-962f-77c2fcfd1d1c",
        "folder_path": "/123",
        "permission": "rw",
        "folder_name": "123",
        "user_name": "2",
        "user_email": "2@1.com"
    }
]
```

**Errors**

* 403 Permission denied.
* 404 Library not found.

## Set User Folder Permission

**POST** https://cloud.seafile.com/api2/repos/{repo_id}/user-folder-perm/

**Request parameters**

* repo_id
* folder_path
* user_email
* permission, `r` or `rw`

**Sample request**

```
curl -d "folder_path=/123&permission=rw&user_email=3@1.com&user_email=2@1.com" -H 'Authorization: Token cbd7705c06846425ed5c46ae0313d5b098d24154' -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api2/repos/bdf816e6-aba8-468c-962f-77c2fcfd1d1c/user-folder-perm/"
```

**Sample response**

```
{
    "failed": [
        {
            "error_msg": "Permission already exists.",
            "user_email": "2@1.com"
        }
    ],
    "success": [
        {
            "repo_id": "bdf816e6-aba8-468c-962f-77c2fcfd1d1c",
            "folder_path": "/123",
            "permission": "rw",
            "folder_name": "123",
            "user_name": "3",
            "user_email": "3@1.com"
        }
    ]
}
```

**Errors**

* 400 folder_path invalid.
* 400 permission invalid.
* 403 Permission denied.
* 404 Library not found.
* 404 Folder not found.

## Modify User Folder Permission

**PUT** https://cloud.seafile.com/api2/repos/{repo_id}/user-folder-perm/

**Request parameters**

* repo_id
* folder_path
* user_email
* permission, `r` or `rw`

**Sample request**

```
curl -X PUT -d "folder_path=/123&permission=r&user_email=3@1.com" -H 'Authorization: Token cbd7705c06846425ed5c46ae0313d5b098d24154' -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api2/repos/bdf816e6-aba8-468c-962f-77c2fcfd1d1c/user-folder-perm/"
```

**Sample response**

```
{
    "repo_id": "bdf816e6-aba8-468c-962f-77c2fcfd1d1c",
    "folder_path": "/123",
    "permission": "r",
    "folder_name": "123",
    "user_name": "3",
    "user_email": "3@1.com"
}
```

**Errors**

* 400 folder_path invalid.
* 400 permission invalid.
* 400 user_email invalid.
* 403 Permission denied.
* 404 Library not found.
* 404 Folder not found.
* 404 User not found.
* 404 Folder permission not found.
* 500 Internal Server Error

## Delete User Folder Permission

**DELETE** https://cloud.seafile.com/api2/repos/{repo_id}/user-folder-perm/

**Request parameters**

* repo_id
* folder_path
* user_email

**Sample request**

```
curl -X DELETE -d "folder_path=/123&user_email=3@1.com" -H 'Authorization: Token cbd7705c06846425ed5c46ae0313d5b098d24154' -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api2/repos/bdf816e6-aba8-468c-962f-77c2fcfd1d1c/user-folder-perm/"
```

**Sample response**

```
{
    "success": true
}
```

**Errors**

* 400 user_email invalid.
* 400 folder_path invalid.
* 403 Permission denied.
* 404 Library not found.
* 404 User not found.


## Get Group Folder Permission

**GET** https://cloud.seafile.com/api2/repos/{repo_id}/group-folder-perm/?folder_path=/123

**Request parameters**

* repo_id
* folder_path

**Sample request**

```
curl -H 'Authorization: Token cbd7705c06846425ed5c46ae0313d5b098d24154' -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api2/repos/bdf816e6-aba8-468c-962f-77c2fcfd1d1c/group-folder-perm/?folder_path=/123"
```

**Sample response**

```
[
    {
        "repo_id": "bdf816e6-aba8-468c-962f-77c2fcfd1d1c",
        "folder_path": "/123",
        "permission": "rw",
        "group_name": "group-2-of-lian",
        "folder_name": "123",
        "group_id": 586
    },
    {
        "repo_id": "bdf816e6-aba8-468c-962f-77c2fcfd1d1c",
        "folder_path": "/123",
        "permission": "r",
        "group_name": "group-of-lian",
        "folder_name": "123",
        "group_id": 65
    }
]
```

**Errors**

* 403 Permission denied.
* 404 Library not found.

## Set Group Folder Permission

**POST** https://cloud.seafile.com/api2/repos/{repo_id}/group-folder-perm/

**Request parameters**

* repo_id
* folder_path
* group_id
* permission, `r` or `rw`

**Sample request**
```
curl -d "folder_path=/123&permission=rw&group_id=586&group_id=65" -H 'Authorization: Token cbd7705c06846425ed5c46ae0313d5b098d24154' -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api2/repos/bdf816e6-aba8-468c-962f-77c2fcfd1d1c/group-folder-perm/"
```

**Sample response**

```
{
    "failed": [
        {
            "group_id": 65,
            "error_msg": "Permission already exists."
        }
    ],
    "success": [
        {
            "repo_id": "bdf816e6-aba8-468c-962f-77c2fcfd1d1c",
            "folder_path": "/123",
            "permission": "rw",
            "group_name": "group-2-of-lian",
            "folder_name": "123",
            "group_id": 586
        }
    ]
}
```

**Errors**

* 400 folder_path invalid.
* 400 permission invalid.
* 403 Permission denied.
* 404 Library not found.
* 404 Folder not found.


## Modify Group Folder Permission

**PUT** https://cloud.seafile.com/api2/repos/{repo_id}/group-folder-perm/

**Request parameters**

* repo_id
* folder_path
* group_id
* permission, `r` or `rw`

**Sample request**

```
curl -X PUT -d "folder_path=/123&permission=rw&group_id=65" -H 'Authorization: Token cbd7705c06846425ed5c46ae0313d5b098d24154' -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api2/repos/bdf816e6-aba8-468c-962f-77c2fcfd1d1c/group-folder-perm/"
```

**Sample response**

```
{
    "repo_id": "bdf816e6-aba8-468c-962f-77c2fcfd1d1c",
    "folder_path": "/123",
    "permission": "rw",
    "group_name": "group-of-lian",
    "folder_name": "123",
    "group_id": 65
}
```

**Errors**

* 400 folder_path invalid.
* 400 permission invalid.
* 400 group_id invalid.
* 403 Permission denied.
* 404 Library not found.
* 404 Folder not found.
* 404 Group not found.
* 404 Folder permission not found.


## Delete Group Folder Permission

**DELETE** https://cloud.seafile.com/api2/repos/{repo_id}/group-folder-perm/

**Request parameters**

* repo_id
* folder_path
* group_id

**Sample request**

    curl -X DELETE -d "folder_path=/123&group_id=65" -H 'Authorization: Token cbd7705c06846425ed5c46ae0313d5b098d24154' -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api2/repos/bdf816e6-aba8-468c-962f-77c2fcfd1d1c/group-folder-perm/"

**Sample response**

    {
        "success": true
    }

**Errors**

* 400 group_id invalid.
* 400 folder_path invalid.
* 403 Permission denied.
* 404 Library not found.
* 404 Group not found.
