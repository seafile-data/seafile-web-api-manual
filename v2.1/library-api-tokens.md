# Library API Tokens

## Library API tokens

### List repo api tokens

**GET** <http://127.0.0.1:8000/api/v2.1/repos/repo-id/repo-api-tokens/>

**Sample request**

```
curl -X GET \
  http://127.0.0.1:8000/api/v2.1/repos/5394b44b-6e41-42fc-90b7-49955547f4f0/repo-api-tokens/ \
  -H 'authorization: token 64b9ee55dc4ab902ff36763ef5c604a76d52875e' \
  -H 'cache-control: no-cache' \
  -H 'postman-token: 542c278d-3c6b-693e-1577-5768c82317b6'

```

**_Sample response_**

```
{
    "repo_api_tokens": [
        {
            "repo_id": "5394b44b-6e41-42fc-90b7-49955547f4f0",
            "app_name": "app-2",
            "generated_by": "xiongchao.cheng@seafile.com",
            "permission": "r",
            "api_token": "2f43a8f52e1dc54f45b31640b62d3c349a2ecbe6"
        },
        {
            "repo_id": "5394b44b-6e41-42fc-90b7-49955547f4f0",
            "app_name": "app-1",
            "generated_by": "xiongchao.cheng@seafile.com",
            "permission": "rw",
            "api_token": "1dcb4e95af32a6d5181b976e01b9b84e3b00f9b5"
        }
    ]
}

```

**_Errors_**

* 403 Permission denied.
* 404 repo not found.
* 500 Internal Server Error.

### Generate repo api token

**POST** <http://127.0.0.1:8000/api/v2.1/repos/repo-id/repo-api-tokens/>

**Sample request**

```
curl -X POST \
  http://127.0.0.1:8000/api/v2.1/repos/5394b44b-6e41-42fc-90b7-49955547f4f0/repo-api-tokens/ \
  -H 'authorization: token 64b9ee55dc4ab902ff36763ef5c604a76d52875e' \
  -H 'cache-control: no-cache' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -H 'postman-token: ec48947a-0815-620a-bd3d-eaf69ef3978a' \
  -F permission=r \
  -F app_name=time

```

**Sample response**

```
{
    "repo_id": "5394b44b-6e41-42fc-90b7-49955547f4f0",
    "app_name": "time",
    "generated_by": "xiongchao.cheng@seafile.com",
    "permission": "r",
    "api_token": "12ddb3cbe80e7b421909cfe328ef2c8d04a99102"
}

```

**Errors**

* 400 bad request
* 403 Permissio denied
* 404 repo not found
* 500 Internal Server Error

### Update repo api token

**PUT** <http://127.0.0.1:8000/api/v2.1/repos/repo-id/repo-api-token/app-name>

**Sample request**

```
curl -X PUT \
  http://127.0.0.1:8000/api/v2.1/repos/5394b44b-6e41-42fc-90b7-49955547f4f0/repo-api-tokens/time/ \
  -H 'authorization: token 64b9ee55dc4ab902ff36763ef5c604a76d52875e' \
  -H 'cache-control: no-cache' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -H 'postman-token: f9016e4c-d927-e7ef-cae2-77f6740c8fe9' \
  -F permission=r

```

**Sample response**

```
{
    "repo_id": "5394b44b-6e41-42fc-90b7-49955547f4f0",
    "app_name": "time",
    "generated_by": "xiongchao.cheng@seafile.com",
    "permission": "r",
    "api_token": "12ddb3cbe80e7b421909cfe328ef2c8d04a99102"
}

```

**Errors**

* 400 bad request
* 403 permissio denied
* 404 repo/api-token not found
* 500 Internal Server Error

### Delete repo api-token

**DELETE** <http://127.0.0.1:8000/api/v2.1/repos/repo-id/repo-api-token/app-name>

**Sample request**

```
curl -X DELETE \
  http://127.0.0.1:8000/api/v2.1/repos/5394b44b-6e41-42fc-90b7-49955547f4f0/repo-api-tokens/time/ \
  -H 'authorization: token 64b9ee55dc4ab902ff36763ef5c604a76d52875e' \
  -H 'cache-control: no-cache' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -H 'postman-token: f9016e4c-d927-e7ef-cae2-77f6740c8fe9' \
  -F permission=r

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

**GET** <http://127.0.0.1:8000/api/v2.1/via-repo-token/dir/>

**Request** **parameters**

* **path**: access path, it will be `/`  if not set
* **type**: items' type which will be list, limit in `f` and`d` , means file and directory
* **recursive**: list items recursively when it is `1` , limit in `0` and `1` , default  `0` 
* **with_thumbnail**: whether some kinds of files are with thumbnail, video, image, etc.
* **thumbnail_size**: thumbnail's size, default `48` 

**Sample request**

```
curl -X GET \
  'http://127.0.0.1:8000/api/v2.1/via-repo-token/dir/?recursive=1' \
  -H 'authorization: token 2f43a8f52e1dc54f45b31640b62d3c349a2ecbe6' \
  -H 'cache-control: no-cache' \
  -H 'postman-token: 1ebd63cc-0155-959a-9852-e2463e9e3cab'

```

**Sample response**

```
{
    "dirent_list": [
        {
            "type": "dir",
            "parent_dir": "/",
            "id": "0000000000000000000000000000000000000000",
            "name": "new-first",
            "mtime": 1572583204
        },
        {
            "type": "file",
            "modifier_email": null,
            "size": 0,
            "is_locked": false,
            "lock_owner": null,
            "lock_time": 0,
            "parent_dir": "/",
            "id": "0000000000000000000000000000000000000000",
            "name": "first-changed.md",
            "mtime": 1572516254,
            "modifier_contact_email": "",
            "modifier_name": ""
        }
    ]
}

```

**Errors**

* 403 permission denied
* 404 repo/api-token not found
* 500 Internal Server Error

### Create New Directory

**POST** <http://127.0.0.1:8000/api/v2.1/via-repo-token/dir/>

**Request** **parameters**

* **path**: access path, it can't be `/` 
* **operation**: make new directory or rename, limit in `mkdir` and `rename` 

**Sample request**

```
curl -X POST \
  'http://127.0.0.1:8000/api/v2.1/via-repo-token/dir/?path=%2Fapi-token-dirs-1' \
  -H 'authorization: token 1dcb4e95af32a6d5181b976e01b9b84e3b00f9b5' \
  -H 'cache-control: no-cache' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -H 'postman-token: 5c41e654-2c38-9beb-b44a-ec4152c66ac8' \
  -F operation=mkdir

```

**Sample response**

```
{
    "type": "dir",
    "repo_id": "5394b44b-6e41-42fc-90b7-49955547f4f0",
    "parent_dir": "/",
    "obj_name": "api-token-dirs-1",
    "obj_id": "0000000000000000000000000000000000000000",
    "mtime": "2019-11-02T15:20:48+00:00"
}

```

**Errors**

* 400 bad request
* 403 permission denied
* 404 repo/api-token not found
* 500 Internal Server Error

### Get Upload Link

**GET** <http://127.0.0.1:8000/api/v2.1/via-repo-token/upload-link/>

**Request** **parameters**

* **path**: the path which you will upload file in, default `/` if not set

**Sample request**

```
curl -X GET \
  http://127.0.0.1:8000/api/v2.1/via-repo-token/upload-link/ \
  -H 'authorization: token 1dcb4e95af32a6d5181b976e01b9b84e3b00f9b5' \
  -H 'cache-control: no-cache' \
  -H 'postman-token: 16ac85c6-8dcc-582d-1f72-824537b326c0'

```

**Sample response**

```
"http://127.0.0.1:8082/upload-api/abde41ee-9d4b-4474-a0b0-23aedc68feda"

```

**Errors**

* 403 permission denied
* 404 repo/api-token not found
* 500 Internal Server Error

### Get File Download Link

**GET** <http://127.0.0.1:8000/api/v2.1/via-repo-token/download-link/>

**Request** **parameters**

* **path**: the file's path which you will download

**Sample request**

```
curl -X GET \
  'http://127.0.0.1:8000/api/v2.1/via-repo-token/download-link/?path=new-first' \
  -H 'authorization: token 2f43a8f52e1dc54f45b31640b62d3c349a2ecbe6' \
  -H 'cache-control: no-cache' \
  -H 'postman-token: bb21dc20-c026-4870-ce5b-ede8372034fe'

```

**Sample response**

```
"http://127.0.0.1:8082/files/191a98b0-b998-423e-a17a-8c6b08b0791c/new-first"

```

**Errors**

* 400 Bad denied
* 404 File not found
* 500 Internal Server Error

### Get Repo Info

**GET** <http://127.0.0.1:8000/api/v2.1/via-repo-token/repo-info/>

**Sample request**

```
curl -X GET \
  http://127.0.0.1:8000/api/v2.1/via-repo-token/repo-info	/ \
  -H 'authorization: token 90604e26da9cec1610c4a39840eb810f3824258d' \
  -H 'cache-control: no-cache' \
  -H 'postman-token: 7cd2a2ea-31e8-1a40-3055-2d15e44d833f'

```

**Sample response**

```
{
    "repo_id": "9d67d0e5-0c84-4b5a-a876-365481a94791",
    "repo_name": "Personal library"
}

```

**Errors**

* 400 Bad Request
* 500 Internal Server Error


