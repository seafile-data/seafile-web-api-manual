# Library API Tokens

## Library API tokens

### List repo api tokens

**GET** /api/v2.1/repos/{repo_id}/repo-api-tokens/

**Request parameters**

* repo_id

**Sample request**

```
curl -H "Authorization: Token 12c8afe4ce2aaa632a4110a2e6bdf1ad68d04e5a" -H 'Accept: application/json; indent=4' 'https://cloud.seafile.com/api/v2.1/repos/b8e06f24-edfe-44a3-b63b-ad9ecc59e1eb/repo-api-tokens/'

```

**Sample response**

```
{
    "repo_api_tokens": [
        {
            "repo_id": "b8e06f24-edfe-44a3-b63b-ad9ecc59e1eb",
            "app_name": "lian-test-2",
            "generated_by": "imwhatiam123@gmail.com",
            "permission": "r",
            "api_token": "05cd0945e412a0d6e955c2fe29e84efc4825ede1"
        },
        {
            "repo_id": "b8e06f24-edfe-44a3-b63b-ad9ecc59e1eb",
            "app_name": "lian-test",
            "generated_by": "imwhatiam123@gmail.com",
            "permission": "rw",
            "api_token": "fe6e0f511d7f11883fe95cea71020e698336220e"
        }
    ]
}

```

**Errors**

* 403 Permission denied.
* 404 repo not found.
* 500 Internal Server Error.

### Generate repo api token

**POST** /api/v2.1/repos/{repo_id}/repo-api-tokens/

**Request parameters**

* repo_id
* permission
* app_name

**Sample request**

```
curl -d "permission=r&app_name=lian-test-3" -H "Authorization: Token 12c8afe4ce2aaa632a4110a2e6bdf1ad68d04e5a" -H 'Accept: application/json; indent=4' 'https://cloud.seafile.com/api/v2.1/repos/b8e06f24-edfe-44a3-b63b-ad9ecc59e1eb/repo-api-tokens/'

```

**Sample response**

```
{
    "repo_id": "b8e06f24-edfe-44a3-b63b-ad9ecc59e1eb",
    "app_name": "lian-test-3",
    "generated_by": "imwhatiam123@gmail.com",
    "permission": "r",
    "api_token": "5213de63c247636fcd1808de00d64d21acc54129"
}

```

**Errors**

* 400 bad request
* 403 Permissio denied
* 404 repo not found
* 500 Internal Server Error

### Update repo api token

**PUT** /api/v2.1/repos/{repo_id}/repo-api-tokens/{app_name}/

**Request parameters**

* repo_id
* permission
* app_name

**Sample request**

```
curl -X PUT -d "permission=rw" -H "Authorization: Token 12c8afe4ce2aaa632a4110a2e6bdf1ad68d04e5a" -H 'Accept: application/json; indent=4' 'https://cloud.seafile.com/api/v2.1/repos/b8e06f24-edfe-44a3-b63b-ad9ecc59e1eb/repo-api-tokens/lian-test-3/'

```

**Sample response**

```
{
    "repo_id": "b8e06f24-edfe-44a3-b63b-ad9ecc59e1eb",
    "app_name": "lian-test-3",
    "generated_by": "imwhatiam123@gmail.com",
    "permission": "rw",
    "api_token": "5213de63c247636fcd1808de00d64d21acc54129"
}

```

**Errors**

* 400 bad request
* 403 permissio denied
* 404 repo/api-token not found
* 500 Internal Server Error

### Delete repo api-token

**DELETE** /api/v2.1/repos/{repo_id}/repo-api-tokens/{app_name}/

**Request parameters**

* repo_id
* app_name

**Sample request**

```
curl -X DELETE -H "Authorization: Token 12c8afe4ce2aaa632a4110a2e6bdf1ad68d04e5a" -H 'Accept: application/json; indent=4' 'https://cloud.seafile.com/api/v2.1/repos/b8e06f24-edfe-44a3-b63b-ad9ecc59e1eb/repo-api-tokens/lian-test-3/'

```

**Sample response**

```
{
    "success": true
}

```

**Errors**

* 403 permission denied
* 404 repo/api-token not found
* 500 Internal Server Error

## Access library with API token

### List Items in Directory

**GET** /api/v2.1/via-repo-token/dir/

**Request** **parameters**

* **path**: access path, it will be `/`  if not set
* **type**: items' type which will be list, limit in `f` and`d` , means file and directory
* **recursive**: list items recursively when it is `1` , limit in `0` and `1` , default  `0` 
* **with_thumbnail**: whether some kinds of files are with thumbnail, video, image, etc.
* **thumbnail_size**: thumbnail's size, default `48` 

**Sample request**

```
curl -H "Authorization: Token fe6e0f511d7f11883fe95cea71020e698336220e" -H 'Accept: application/json; indent=4' 'https://cloud.seafile.com/api/v2.1/via-repo-token/dir/'

```

**Sample response**

```
{
    "user_perm": "rw",
    "dir_id": "dc561abe027728f36ea6d02b7b4439ba1aba1b3b",
    "dirent_list": [
        {
            "type": "dir",
            "id": "04f3fb2b992c7aa1eb897a4e2c46b3212def1028",
            "name": "123 in lian test",
            "mtime": 1575514722,
            "permission": "rw",
            "parent_dir": "/",
            "starred": false
        },
        {
            "type": "file",
            "id": "0000000000000000000000000000000000000000",
            "name": "123.md",
            "mtime": 1576548579,
            "permission": "rw",
            "parent_dir": "/",
            "size": 0,
            "modifier_email": "imwhatiam123@gmail.com",
            "modifier_name": "lian",
            "modifier_contact_email": "imwhatiam123@gmail.com",
            "is_locked": false,
            "lock_time": 0,
            "lock_owner": "",
            "lock_owner_name": "",
            "lock_owner_contact_email": "",
            "locked_by_me": false,
            "starred": false
        },
        {
            "type": "file",
            "id": "5a82a5c0e2263451c219bbec36dc285fdede4312",
            "name": "123.xlsx",
            "mtime": 1574744620,
            "permission": "rw",
            "parent_dir": "/",
            "size": 9836,
            "modifier_email": "imwhatiam123@gmail.com",
            "modifier_name": "lian",
            "modifier_contact_email": "imwhatiam123@gmail.com",
            "is_locked": false,
            "lock_time": 0,
            "lock_owner": "",
            "lock_owner_name": "",
            "lock_owner_contact_email": "",
            "locked_by_me": false,
            "starred": false
        }
    ]
}

```

**Errors**

* 403 permission denied
* 404 repo/api-token not found
* 500 Internal Server Error

### Create New Directory

**POST** /api/v2.1/via-repo-token/dir/

**Request** **parameters**

* **path**: access path, it can't be `/` 
* **operation**: make new directory or rename, limit in `mkdir` and `rename` 

**Sample request**

```
curl -d "operation=mkdir" -H "Authorization: Token fe6e0f511d7f11883fe95cea71020e698336220e" -H 'Accept: application/json; indent=4' 'https://cloud.seafile.com/api/v2.1/via-repo-token/dir/?path=/new-dir'

```

**Sample response**

```
{
    "type": "dir",
    "repo_id": "b8e06f24-edfe-44a3-b63b-ad9ecc59e1eb",
    "parent_dir": "/",
    "obj_name": "new-dir",
    "obj_id": "0000000000000000000000000000000000000000",
    "mtime": "2020-02-24T15:50:27+08:00"
}

```

**Errors**

* 400 bad request
* 403 permission denied
* 404 repo/api-token not found
* 500 Internal Server Error

### Get Upload Link

**GET** /api/v2.1/via-repo-token/upload-link/

**Request** **parameters**

* **path**: the path which you will upload file in, default `/` if not set

**Sample request**

```
curl -H "Authorization: Token fe6e0f511d7f11883fe95cea71020e698336220e" -H 'Accept: application/json; indent=4' 'https://cloud.seafile.com/api/v2.1/via-repo-token/upload-link/?path=/new-dir'

```

**Sample response**

```
"https://cloud.seafile.com/seafhttp/upload-api/62fdd868-ee80-4acb-b1ce-362de3fc0a63"

```

**Errors**

* 403 permission denied
* 404 repo/api-token not found
* 500 Internal Server Error

### Get File Download Link

**GET** /api/v2.1/via-repo-token/download-link/

**Request** **parameters**

* **path**: the file's path which you will download

**Sample request**

```
curl -H "Authorization: Token fe6e0f511d7f11883fe95cea71020e698336220e" -H 'Accept: application/json; indent=4' 'https://cloud.seafile.com/api/v2.1/via-repo-token/download-link/?path=/123.md'

```

**Sample response**

```
"https://cloud.seafile.com/seafhttp/files/28ed9480-f48e-4734-b972-2e0d27167dd5/123.md"

```

**Errors**

* 400 Bad denied
* 404 File not found
* 500 Internal Server Error

### Get Repo Info

**GET** /api/v2.1/via-repo-token/repo-info/

**Sample request**

```
curl -H "Authorization: Token fe6e0f511d7f11883fe95cea71020e698336220e" -H 'Accept: application/json; indent=4' 'https://cloud.seafile.com/api/v2.1/via-repo-token/repo-info/'

```

**Sample response**

```
{
    "repo_id": "b8e06f24-edfe-44a3-b63b-ad9ecc59e1eb",
    "repo_name": "lian-test"
}

```

**Errors**

* 400 Bad Request
* 500 Internal Server Error


