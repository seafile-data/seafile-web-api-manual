# Share

## List Share

### List Shared Users of a Library

**GET** <https://cloud.seafile.com/api2/repos/7460f7ac-a0ff-4585-8906-bb5a57d2e118/dir/shared_items/?p=/&share_type=user>

**Request parameters**

* p, `/` means the **root** folder, which is equivalent to the library.
* share_type, `user`

**Sample request**

```
curl -v -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd' -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api2/repos/7460f7ac-a0ff-4585-8906-bb5a57d2e118/dir/shared_items/?p=/&share_type=user

```

**Sample response**

```
[
    {"user_info": {"nickname": "5", "name": "5@1.com"}, "share_type": "user", "permission": "r"},
    {"user_info": {"nickname": "name of 4", "name": "4@1.com"}, "share_type": "user", "permission": "r"}
]

```

**Errors**

* 400 share_type invalid.
* 403 Permission denied.
* 404 Library not found.

### List Shared Groups of a Library

**GET** <https://cloud.seafile.com/api2/repos/7460f7ac-a0ff-4585-8906-bb5a57d2e118/dir/shared_items/?p=/&share_type=group>

**Request parameters**

* p, `/` means the **root** folder, which is equivalent to the library.
* share_type, `group`

**Sample request**

```
curl -v -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd' -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api2/repos/7460f7ac-a0ff-4585-8906-bb5a57d2e118/dir/shared_items/?p=/&share_type=group

```

**Sample response**

```
[
    {"group_info": {"id": 65, "name": "group"}, "share_type": "group", "permission": "r"},
    {"group_info": {"id": 395, "name": "lsd"}, "share_type": "group", "permission": "rw"}
]

```

**Errors**

* 400 share_type invalid.
* 403 Permission denied.
* 404 Library not found.

### List Libraries Shared to me

**GET** <https://cloud.seafile.com/api2/beshared-repos/>

**Sample request**

```
curl -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd' "https://cloud.seafile.com/api2/beshared-repos/"

```

**Sample response**

```
"[{"user": "user@example.com", "repo_id": "989e3952-9d6f-4427-ab16-4bf9b53212eb", "share_type": "personal", "permission": "rw", "encrypted": false, "repo_desc": "lib shared to imwhatiam", "enc_version": false, "last_modified": 1398218747, "is_virtual": false, "group_id": 0, "repo_name": "lib shared to imwhatiam"}]"

```

## Share to User

### Share a Library to User

**PUT** <https://cloud.seafile.com/api2/repos/{repo_id}/dir/shared_items/?p=/>

**Request parameters**

* p, `/` means the **root** folder, which is equivalent to the library.
* share_type, `user`
* username, a email string or a list contains multi emails
* permission, `r`, `rw` or `admin`, default `r`.

**Sample request**

```
curl -X PUT -d "share_type=user&username=4@1.com&username=5@1.com&username=invalid@email.com&permission=r" -H 'Authorization: Token 0eb24ce5db35a31f70171eca2f760f03f59fa09a' -H 'Accept: application/json; charset=utf-8; indent=4' https://cloud.seafile.com/api2/repos/7460f7ac-a0ff-4585-8906-bb5a57d2e118/dir/shared_items/?p=/

```

**Sample response**

```
{
    "failed": [
        {"email": "invalid@email.com", "error_msg": "User invalid@email.com not found."}
    ],
    "success": [
        {"user_info": {"nickname": "name of 4", "name": "4@1.com"}, "share_type": "user", "permission": "r"},
        {"user_info": {"nickname": "5", "name": "5@1.com"}, "share_type": "user", "permission": "r"}
    ]
}

```

**Errors**

* 400 permission invalid.
* 400 share_type invalid.
* 403 Permission denied.
* 404 Library not found.

### Unshare a Library from User

**DELETE** <https://cloud.seafile.com/api2/repos/{repo_id}/dir/shared_items/?p=/&share_type=user&username=5@1.com>

**Request parameters**

* p, `/` means the **root** folder, which is equivalent to the library.
* share_type, `user`
* username, a email string

**Sample request**

```
curl -X DELETE -H 'Authorization: Token 0eb24ce5db35a31f70171eca2f760f03f59fa09a' -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api2/repos/7460f7ac-a0ff-4585-8906-bb5a57d2e118/dir/shared_items/?p=/&share_type=user&username=5@1.com"

```

**Sample response**

```
{"success": true}

```

**Errors**

* 400 share_type invalid.
* 400 email invalid.
* 403 Permission denied.
* 404 Library not found.

### Update User Share Permission of a Library

**POST** <https://cloud.seafile.com/api2/repos/{repo_id}/dir/shared_items/?p=/&share_type=user&username=5@1.com>

**Request parameters**

* p, `/` means the **root** folder, which is equivalent to the library.
* share_type, `user`
* username, a email string
* permisson, `r` or `rw`

**Sample request**

```
curl -d "permission=r" -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd' -H 'Accept: application/json; indent=4' "https://cloud.seafile.com/api2/repos/2deffbac-d7be-4ace-b406-efb799083ee9/dir/shared_items/?p=/&share_type=user&username=5@1.com"

```

**Sample response**

```
{"success": true}

```

**Errors**

* 400 share_type invalid.
* 403 permission invalid.
* 403 Permission denied.
* 404 Library not found.
* 404 Folder not found.

### Delete a library shared to me (leave the share)

**DELETE** <https://cloud.seafile.com/api2/beshared-repos/{repo_id}/?share_type=personal&from=from_user@name.com>

**Sample request**

```
curl -X DELETE -H "Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api2/beshared-repos/{repo_id}/?share_type=personal&from=from_user@name.com

```

**Sample response**

```
{"success": true}

```

**Errors**

* 400 Invalid argument
* 400 Library does not exist

## Share to Group

### Share a Library to Group

**PUT** <https://cloud.seafile.com/api2/repos/{repo_id}/dir/shared_items/?p=/>

**Request parameters**

* p, `/` means the **root** folder, which is equivalent to the library.
* share_type, `group`
* group_id , an integer or a list contains multi integers
* permission, `r`, `rw` or `admin`, default `r`.

**Sample request**

```
curl -X PUT -d "share_type=group&group_id=65&group_id=395&group_id=invalid_group_id&group_id=111&permission=rw" -H 'Authorization: Token 0eb24ce5db35a31f70171eca2f760f03f59fa09a' -H 'Accept: application/json; charset=utf-8; indent=4' https://cloud.seafile.com/api2/repos/7460f7ac-a0ff-4585-8906-bb5a57d2e118/dir/shared_items/?p=/

```

**Sample response**

```
{
    "failed": [],
    "success": [
        {"group_info": {"id": 65, "name": "group"}, "share_type": "group", "permission": "rw"},
        {"group_info": {"id": 395, "name": "lsd"}, "share_type": "group", "permission": "rw"}
    ]
}

```

**Errors**

* 400 permission invalid.
* 400 group_id invalid.
* 400 share_type invalid.
* 403 Permission denied.
* 404 Library not found.

### Unshare a Library from Group

**DELETE** <https://cloud.seafile.com/api2/repos/{repo_id}/dir/shared_items/?p=/&share_type=group&group=65>

**Request parameters**

* p, `/` means the **root** folder, which is equivalent to the library.
* share_type, `group`
* group_id , an integer

**Sample request**

```
curl -X DELETE -H 'Authorization: Token 0eb24ce5db35a31f70171eca2f760f03f59fa09a' -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api2/repos/7460f7ac-a0ff-4585-8906-bb5a57d2e118/dir/shared_items/?p=/&share_type=group&group_id=65"

```

**Sample response**

```
{"success": true}

```

**Errors**

* 400 share_type invalid.
* 400 group_id invalid.
* 403 Permission denied.
* 404 Library not found.

### Update Share Permission of Group Shared Library

**POST** <https://cloud.seafile.com/api2/repos/{repo_id}/dir/shared_items/?p=/&share_type=group&group_id=65>

**Request parameters**

* p, `/` means the **root** folder, which is equivalent to the library.
* share_type, `group`
* group_id , an integer
* permisson, `r` or `rw`

**Sample request**

```
curl -d "permission=r" -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd' -H 'Accept: application/json; indent=4' "https://cloud.seafile.com/api2/repos/2deffbac-d7be-4ace-b406-efb799083ee9/dir/shared_items/?p=/&share_type=group&group_id=65"

```

**Sample response**

```
{"success": true}

```

**Errors**

* 400 share_type invalid.
* 403 permission invalid.
* 403 Permission denied.
* 404 Library not found.



## Shared-with-all Libraries

### Create shared-with-all Library

**POST** https\://cloud.seafile.com/api2/repos/public

**Request parameters**

* name
* permission, r or rw, default r.
* passwd (optional).

**Sample request**

```
curl -X POST -d "name=test-public-repo&permission=rw&passwd=password" -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d9b477fd' -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api2/repos/public/

```

**Sample response**

```
{
    "owner_nickname": "851958789",
    "owner_name": "851958789",
    "permission": "rw",
    "encrypted": false,
    "mtime_relative": "<time datetime=\"2019-07-03T10:02:06\" is=\"relative-time\" title=\"Wed, 3 Jul 2019 10:02:06 +0000\" >Just now</time>",
    "mtime": 1562148126,
    "owner": "851958789@qq.com",
    "id": "99d67972-d214-47c4-af98-19b2dd158446",
    "size": 0,
    "name": "test-public-repo",
    "desc": "",
    "size_formatted": "0 bytes"
}

```

**Errors**

* 400 Library name is required.
* 400 Invalid permission
* 403 You do not have permission to create library.
* 403 NOT allow to create encrypted library.

### Share Existing Library as shared-with-all

**PUT** <https://cloud.seafile.com/api/v2.1/shared-repos/{repo-id}/>

**Request parameters**

* repo_id
* share_type, must be public
* permission, r or rw.

**Sample request**

```
curl -X PUT -d "share_type=public&password=rw" -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d9b477fd' -H 'Accept: application/json; indent=4' 'https://cloud.seafile.com/api/v2.1/shared-repos/99d67972-d214-47c4-af98-19b2dd158446/'

```

**Sample response**

```
success

```

**Errors**

* 400 Share_type invalid.
* 400 Share_type can only be 'personal' or 'group' or 'public'.
* 400 Permission need to be rw or r.
* 403 Permission invalid.
* 404 Library not found.
* 500 Internal Server Error.

### Remove Library from shared-with-all

**DELETE** <https://cloud.seafile.com/api/v2.1/shared-repos/{repo-id}/>

**Request parameters**

* share_type, must be public

**Sample request**

```
curl -X DELETE -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d9b477fd' -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api/v2.1/shared-repos/dae8cecc-2359-4d33-aa42-01b7846c4b32/?share_type=public

```

**Sample response**

```
success

```

**Errors**

* 400 Share type invalid.
* 400 Share type can only be personal or group or public.
* 403 Permission denied.
* 404 Library not found.
* 500 Internal Server Error.

## Batch Share Operation

### Batch Share Libraries to User

**POST** <https://cloud.seafile.com/api/v2.1/repos/batch/>

**Request parameters**

* operation, `share`
* share_type, `user`
* username, email of a user
* permission, default is `rw`
* repo_id

**Sample request**

```
curl -d "operation=share&share_type=user&username=2@org.com&repo_id=b6cfa05d-07af-422b-924e-45202dc1cbb5&repo_id=48aa475d-deb0-40f0-ab9b-22ec84989a58" -H 'Authorization: Token 40c89d06a2beeec672d091156de4cc163c6aa31a' -H 'Accept: application/json; charset=utf-8; indent=4' https://cloud.seafile.com/api/v2.1/repos/batch/

```

**Sample response**

```
{
    "failed": [
        {"repo_id": "3761ade3-100b-4c3b-9508-79b3a510e6f6", "error_msg": "This item has been shared to 1@1.com."}
    ],
    "success": [
        {"username": "1@1.com", "repo_id": "f820bd12-0511-4542-b14b-3e48d8efc294", "permission": "rw"}
    ]
}

```

**Errors**

* 400 permission invalid.
* 400 share_type invalid.
* 403 Permission denied.
* 404 Library not found.
* 404 User not found.
* 500 Internal Server Error

### Batch Share Libraries to Group

**POST** <https://cloud.seafile.com/api/v2.1/repos/batch/>

**Request parameters**

* operation, `share`
* share_type, `group`
* group_id
* permission, default is `rw`
* repo_id

**Sample request**

```
curl -d "operation=share&share_type=group&group_id=540&repo_id=b6cfa05d-07af-422b-924e-45202dc1cbb5&repo_id=48aa475d-deb0-40f0-ab9b-22ec84989a58" -H 'Authorization: Token 40c89d06a2beeec672d091156de4cc163c6aa31a' -H 'Accept: application/json; charset=utf-8; indent=4' https://cloud.seafile.com/api/v2.1/repos/batch/

```

**Sample response**

```
{
    "failed": [
        {"repo_id": "f820bd12-0511-4542-b14b-3e48d8efc294", "error_msg": "This item has been shared to group-of-lian."}
    ],
    "success": [
        {"permission": "rw", "repo_id": "3761ade3-100b-4c3b-9508-79b3a510e6f6", "group_id": 65, "group_name": "group-of-lian"}
    ]
}

```

**Errors**

* 400 permission invalid.
* 400 share_type invalid.
* 403 Permission denied.
* 404 Library not found.
* 404 Group not found.
* 500 Internal Server Error

## Folder Share

### Share a Folder

**PUT** <https://cloud.seafile.com/api2/repos/{repo-id}/dir/shared_items/?p={path}>

* repo-id
* path
* permission, `r` or `rw`
* share_type, `user` or `group`
* username, necessary if share_type is user
* group_id, necessary if share_type is group

**Sample request for share folder to user**

```
curl -X PUT -d "username=2@1.com&share_type=user&permission=r" -H 'Authorization: Token ef12bf1e66a1aa797a1d6556fdc9ae84f1e9249f' -H 'Accept: application/json; charset=utf-8; indent=4' https://cloud.seafile.com/api2/repos/78c620ee-2989-4427-8eff-7748f4fbebc0/dir/shared_items/?p=/q

```

**Sample response for share folder to user**

```
{"failed": [], "success": [{"user_info": {"nickname": "2", "name": "2@1.com"}, "share_type": "user", "permission": "r"}]}

```

**Sample request for share folder to group**

```
curl -X PUT -d "group_id=772&share_type=group&permission=rw" -H 'Authorization: Token ef12bf1e66a1aa797a1d6556fdc9ae84f1e9249f' -H 'Accept: application/json; charset=utf-8; indent=4' https://cloud.seafile.com/api2/repos/78c620ee-2989-4427-8eff-7748f4fbebc0/dir/shared_items/?p=/q

```

**Sample response for share folder to group**

```
{"failed": [], "success": [{"group_info": {"id": 772, "name": "group-2"}, "share_type": "group", "permission": "rw"}]}

```

**Errors**

* 400 share_type/permission/group_id invalid.
* 403 Permission denied.
* 404 Library/Folder/Group not found.
* 500 Failed to get sub repo.

### List Shared Folders

**GET** <https://cloud.seafile.com/api/v2.1/shared-folders/>

**Sample request**

```
curl -v -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd' -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api/v2.1/shared-folders/

```

**Sample response**

```
[
    {
        "share_permission": "rw",
        "repo_id": "2deffbac-d7be-4ace-b406-efb799083ee9",
        "share_type": "personal",
        "folder_name": "asd",
        "path": "/asd",
        "user_name": "1",
        "contact_email": "contact@email.com",
        "user_email": "1@1.com"
    },
    {
        "share_permission": "r",
        "repo_id": "2deffbac-d7be-4ace-b406-efb799083ee9",
        "share_type": "group",
        "group_name": "test_group",
        "folder_name": "asd",
        "path": "/asd",
        "group_id": 1448
    }
]

```

**Errors**

* 500 Internal Server Error

### Update Folder Share Permission

**POST** <https://cloud.seafile.com/api2/repos/2deffbac-d7be-4ace-b406-efb799083ee9/dir/shared_items/?p=/asd&share_type=user&username=1@1.com>

**Sample request**

```
curl -d "permission=r" -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd' -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api2/repos/2deffbac-d7be-4ace-b406-efb799083ee9/dir/shared_items/?p=/asd&share_type=user&username=1@1.com

```

**Sample response**

```
{"success":true}

```

**Errors**

* 400 permission invalid.
* 400 Email invalid.
* 403 Permission denied.
* 404 Library not found.
* 404 Folder not found.
* 500 Internal Server Error

### Unshare a Folder

**POST** <https://cloud.seafile.com/api2/repos/2deffbac-d7be-4ace-b406-efb799083ee9/dir/shared_items/?p=/asd&share_type=group&group_id=1448>

**Sample request**

```
curl -X DELETE -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd' -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api2/repos/2deffbac-d7be-4ace-b406-efb799083ee9/dir/shared_items/?p=/asd&share_type=group&group_id=1448

```

**Sample response**

```
{"success":true}

```

**Errors**

* 400 Email invalid.
* 403 Permission denied.
* 404 Library not found.
* 404 Folder not found.
* 500 Internal Server Error


