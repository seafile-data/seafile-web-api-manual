# Batch Operation with Multiple Files/Directories

## Synchronized Operations

### Batch Copy Items Synchronously

**POST** [http://192.168.1.113:8000/api/v2.1/repos/sync-batch-copy-item/](http://192.168.1.113:8000/api/v2.1/repos/batch-copy-item/)

**Request parameters**

Content type of parameter must be `application/json` and passed through POST request's body.

```
{
    "src_repo_id":"7460f7ac-a0ff-4585-8906-bb5a57d2e118",
    "src_parent_dir":"/a/b/c/",
    "src_dirents":["1.md", "2.md"],
    
    "dst_repo_id":"a3fa768d-0f00-4343-8b8d-07b4077881db",
    "dst_parent_dir":"/x/y/",
}

```

**Sample request**

```
curl -d '{"src_repo_id":"b3e045da-0c2c-4e68-be15-7480f7aac717", "src_parent_dir":"/", "dst_parent_dir":"/", "dst_repo_id":"fb5b4682-a761-4a9d-810c-ebf72ac2926e", "src_dirents":["123", "test.md"]}' -H 'Authorization: Token 825d6877dc3474d952b1f5b0654aeaeb90c48281' -H 'Accept: application/json; charset=utf-8; indent=4' -H 'Content-Type: application/json' "http://127.0.0.1:8000/api/v2.1/repos/sync-batch-copy-item/"

```

**Sample response**

```
{
    "success": "true"
}

```

**Errors**

* 400 src_repo_id/dst_repo_id/src_parent_dir/dst_parent_dir/src_dirents invalid.
* 403 Permission denied.
* 404 Library/Folder not found.

### Batch Move Items Synchronously

**POST** [http://192.168.1.113:8000/api/v2.1/repos/sync-batch-move-item/](http://192.168.1.113:8000/api/v2.1/repos/batch-copy-item/)

**Request parameters**

Content type of parameter must be `application/json` and passed through POST request's body.

```
{
    "src_repo_id":"7460f7ac-a0ff-4585-8906-bb5a57d2e118",
    "src_parent_dir":"/a/b/c/",
    "src_dirents":["1.md", "2.md"],
    
    "dst_repo_id":"a3fa768d-0f00-4343-8b8d-07b4077881db",
    "dst_parent_dir":"/x/y/",
}

```

**Sample request**

```
curl -d '{"src_repo_id":"b3e045da-0c2c-4e68-be15-7480f7aac717", "src_parent_dir":"/", "dst_parent_dir":"/", "dst_repo_id":"fb5b4682-a761-4a9d-810c-ebf72ac2926e", "src_dirents":["123", "test.md"]}' -H 'Authorization: Token 825d6877dc3474d952b1f5b0654aeaeb90c48281' -H 'Accept: application/json; charset=utf-8; indent=4' -H 'Content-Type: application/json' "http://127.0.0.1:8000/api/v2.1/repos/sync-batch-move-item/"

```

**Sample response**

```
{
    "success": "true"
}

```

**Errors**

* 400 src_repo_id/dst_repo_id/src_parent_dir/dst_parent_dir/src_dirents invalid.
* 403 Permission denied.
* 404 Library/Folder not found.

### Delete

DELETE [https://cloud.seafile.com/](https://cloud.seafile.com/api2/repos/{repo_id}/fileops/delete/)api/v2.1/repos/batch-delete-item/

**Request parameters**

Content type of parameter must be `application/json` and passed through DELETE request's body.

```
{
    "repo_id":"7460f7ac-a0ff-4585-8906-bb5a57d2e118",
    "parent_dir":"/a/b/c/",
    "dirents":["1.md", "2.md"],
}

```

**Sample request**

```
curl -X DELETE -d '{"repo_id":"b3e045da-0c2c-4e68-be15-7480f7aac717", "parent_dir":"/", "dirents":["123", "test.md"]}' -H 'Authorization: Token 825d6877dc3474d952b1f5b0654aeaeb90c48281' -H 'Accept: application/json; charset=utf-8; indent=4' -H 'Content-Type: application/json' "http://127.0.0.1:8000/api/v2.1/repos/batch-delete-item/"

```

**Sample response**

```
{
    "success": true
}

```

**Errors**

* 400 repo_id/parent_dir/dirents invalid.
* 403 Permission denied.
* 403 File is locked.
* 403 Can't delete folder, please check its permission.
* 404 Library/Folder not found.
* 502 Internal Server Error

## Asynchronized Operations

### Batch Copy Items Asynchronously

**POST** [http://192.168.1.113:8000/api/v2.1/repos/async-batch-copy-item/](http://192.168.1.113:8000/api/v2.1/repos/batch-copy-item/)

**Request parameters**

Content type of parameter must be `application/json` and passed through POST request's body.

```
{
    "src_repo_id":"7460f7ac-a0ff-4585-8906-bb5a57d2e118",
    "src_parent_dir":"/a/b/c/",
    "src_dirents":["1.md", "2.md"],
    
    "dst_repo_id":"a3fa768d-0f00-4343-8b8d-07b4077881db",
    "dst_parent_dir":"/x/y/",
}

```

**Sample request**

```
curl -d '{"src_repo_id":"b3e045da-0c2c-4e68-be15-7480f7aac717", "src_parent_dir":"/", "dst_parent_dir":"/", "dst_repo_id":"fb5b4682-a761-4a9d-810c-ebf72ac2926e", "src_dirents":["123", "test.md"]}' -H 'Authorization: Token 825d6877dc3474d952b1f5b0654aeaeb90c48281' -H 'Accept: application/json; charset=utf-8; indent=4' -H 'Content-Type: application/json' "http://127.0.0.1:8000/api/v2.1/repos/async-batch-copy-item/"

```

**Sample response**

Note: if you copy files/folders in the same library, task_id in response will be empty string.

```
{
    "task_id": "3ebdbbcb-3f43-459b-87ee-6c89c192a810"
}

```

**Errors**

* 400 src_repo_id/dst_repo_id/src_parent_dir/dst_parent_dir/src_dirents invalid.
* 403 Permission denied.
* 404 Library/Folder not found.

### Batch Move Items Asynchronously

**POST** [http://192.168.1.113:8000/api/v2.1/repos/async-batch-move-item/](http://192.168.1.113:8000/api/v2.1/repos/batch-copy-item/)

**Request parameters**

Content type of parameter must be `application/json` and passed through POST request's body.

```
{
    "src_repo_id":"7460f7ac-a0ff-4585-8906-bb5a57d2e118",
    "src_parent_dir":"/a/b/c/",
    "src_dirents":["1.md", "2.md"],
    
    "dst_repo_id":"a3fa768d-0f00-4343-8b8d-07b4077881db",
    "dst_parent_dir":"/x/y/",
}

```

**Sample request**

```
curl -d '{"src_repo_id":"b3e045da-0c2c-4e68-be15-7480f7aac717", "src_parent_dir":"/", "dst_parent_dir":"/", "dst_repo_id":"fb5b4682-a761-4a9d-810c-ebf72ac2926e", "src_dirents":["123", "test.md"]}' -H 'Authorization: Token 825d6877dc3474d952b1f5b0654aeaeb90c48281' -H 'Accept: application/json; charset=utf-8; indent=4' -H 'Content-Type: application/json' "http://127.0.0.1:8000/api/v2.1/repos/async-batch-move-item/"

```

**Sample response**

Note: if you move files/folders in the same library, task_id in response will be empty string.

```
{
    "task_id": "d40df789-5e0b-4007-b590-203a04d6cb90"
}

```

**Errors**

* 400 src_repo_id/dst_repo_id/src_parent_dir/dst_parent_dir/src_dirents invalid.
* 403 Permission denied.
* 404 Library/Folder not found.

### Query Async Operation Progress

**GET** <https://cloud.seafile.com/api/v2.1/query-copy-move-progress/>

**Request parameters**

* task_id

**Sample request**

```
curl -H 'Authorization: Token ae265ae599a29c238ca25fb63087859798d5f55d' -H 'Accept: application/json; charset=utf-8; indent=4' 'https://cloud.seafile.com/api/v2.1/query-copy-move-progress/?task_id=d1ca2b8c-8ab8-4dd4-8ad7-842130764484'

```

**Sample response**

```
{
    "failed_reason": "",
    "failed": false,
    "successful": true,
    "canceled": false,
    "done": 1,
    "total": 1
}

```

**Errors**

* 400 task_id invalid.
* 500 Internal Server Error

### Cancel Async operation

**DELETE** <https://cloud.seafile.com/api/v2.1/copy-move-task/>

**Request parameters**

* task_id

**Sample request**

```
curl -X DELETE -d "task_id=d1ca2b8c-8ab8-4dd4-8ad7-842130764484" -H 'Authorization: Token ae265ae599a29c238ca25fb63087859798d5f55d' -H 'Accept: application/json; charset=utf-8; indent=4' 'https://cloud.seafile.com/api/v2.1/copy-move-task/'

```

**Sample response**

```
{
    "success": true
}

```

**Errors**

* 400 task_id invalid.

### Download Multiple Items

Perform the following two steps to download multiple files and directories.

#### Get Task Token

**POST** <https://cloud.seafile.com/api/v2.1/repos/{repo-id}/zip-task/>

**Request parameters**

* parent_dir
* dirents

**Sample request**

one dirent

```
curl -d 'parent_dir=/my_folder&dirents=pdfs' -H 'Authorization: Token 0eb24ce5db35a31f70171eca2f760f03f59fa09a' -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/repos/7460f7ac-a0ff-4585-8906-bb5a57d2e118/zip-task/"

```

mutiple dirents

```
curl -d 'parent_dir=/my_folder&dirents=pdfs&dirents=docs&dirents=images' -H 'Authorization: Token 0eb24ce5db35a31f70171eca2f760f03f59fa09a' -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/repos/7460f7ac-a0ff-4585-8906-bb5a57d2e118/zip-task/"

```

**Sample response**

```
{
    "zip_token": "b2272645-35ee-44ce-8f68-07c022107015"
}

```

**Errors**

* 400 parent_dir/dirents invalid.
* 400 Unable to download directory: size is too large.
* 403 Permission denied.
* 404 Library/Folder not found.
* 500 Internal Server Error

#### Query Task Progress

Use the token returned from previous request to check if task progress finished.

**GET** <https://cloud.seafile.com/api/v2.1/query-zip-progress/?token={token}>

* token

**Sample request**

```
curl -H 'Authorization: Token 0eb24ce5db35a31f70171eca2f760f03f59fa09a' -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/query-zip-progress/?token=b2272645-35ee-44ce-8f68-07c022107015"

```

**Sample response**

If `zipped` is equal to `total`, means task finished.

```
{
    "zipped":2,
    "total":2
}

```

**Errors**

* 400 token invalid.
* 500 Internal Server Error

After the task finished, you can access the zipped items with URL like:

```
FILE_SERVER_ROOT/zip/{zip_token}

```

For example, `https://cloud.seafile.com/seafhttp/zip/b2272645-35ee-44ce-8f68-07c022107015` is the final URL in this case.
