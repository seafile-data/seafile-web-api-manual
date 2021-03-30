# Deprecated

## Get Download Links of a Library

**GET** <https://cloud.seafile.com/api2/repos/{repo-id}/download-shared-links/>

**Request parameters**

* repo-id

**Sample request**

```
curl -H 'Authorization: Token 24fd3c026886e3121b2ca630805ed425c272cb96' -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api2/repos/632ab8a8-ecf9-4435-93bf-f495d5bfe975/download-shared-links/

```

**Sample response**

```
[
    {
        "view_count": 0,
        "name": "/",
        "share_type": "d",
        "creator_name": "lian",
        "create_by": "lian@lian.com",
        "token": "105f108fb6",
        "create_time": "2016-01-18T15:03:10+0800",
        "path": "/",
        "size": ""
    },
    {
        "view_count": 3,
        "name": "1.md",
        "share_type": "f",
        "creator_name": "lian",
        "create_by": "lian@lian.com",
        "token": "a626012c1b",
        "create_time": "2016-01-19T11:27:43+0800",
        "path": "/1.md",
        "size": "4"
    }
]

```

**Errors**

* 403 Permission denied.
* 404 Library not found.

## Get Upload Links of a Library

**GET** <https://cloud.seafile.com/api2/repos/{repo-id}/upload-shared-links/>

**Request parameters**

* repo-id

**Sample request**

```
curl -H 'Authorization: Token 24fd3c026886e3121b2ca630805ed425c272cb96' -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api2/repos/632ab8a8-ecf9-4435-93bf-f495d5bfe975/upload-shared-links/

```

**Sample response**

```
[
    {
        "view_count": 3,
        "name": "/",
        "creator_name": "lian",
        "create_by": "lian@lian.com",
        "token": "43340efca5",
        "create_time": "2016-01-18T15:03:12+0800",
        "path": "/"
    },
    {
        "view_count": 8,
        "name": "a&b",
        "creator_name": "lian",
        "create_by": "lian@lian.com",
        "token": "f1e49d445a",
        "create_time": "2016-01-18T15:03:18+0800",
        "path": "/a&b/"
    }
]

```

**Errors**

* 403 Permission denied.
* 404 Library not found.

## Delete Download Links of a Library

**GET** <https://cloud.seafile.com/api2/repos/{repo-id}/download-shared-links/{token}/>

**Request parameters**

* repo-id
* token

**Sample request**

```
curl -X DELETE -H 'Authorization: Token 24fd3c026886e3121b2ca630805ed425c272cb96' -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api2/repos/632ab8a8-ecf9-4435-93bf-f495d5bfe975/download-shared-links/105f108fb6/

```

**Sample response**

```
{"success": true}

```

**Errors**

* 403 Permission denied.
* 404 Library not found.
* 404 Link not found.

## Delete Upload Link of a Library

**GET** <https://cloud.seafile.com/api2/repos/{repo-id}/upload-shared-links/{token}/>

**Request parameters**

* repo-id
* token

**Sample request**

```
curl -X DELETE -H 'Authorization: Token 24fd3c026886e3121b2ca630805ed425c272cb96' -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api2/repos/632ab8a8-ecf9-4435-93bf-f495d5bfe975/upload-shared-links/f1e49d445a/

```

**Sample response**

```
{"success": true}

```

**Errors**

* 403 Permission denied.
* 404 Library not found.
* 404 Link not found.





## Batch Copy Items (Deprecated)

**POST** <http://192.168.1.113:8000/api/v2.1/repos/batch-copy-item/>

**Request parameters**

Content type of parameter must be `application/json` and passed through POST request's body.

```
{
    "src_repo_id":"",
    "dst_repo_id":"",
    "paths":[
        {"src_path":"","dst_path":""},
        {"src_path":"","dst_path":""},
    ]
}

```

**Sample request**

```
curl -d '{"src_repo_id":"d4aac5b9-28d4-4372-a4b3-d6de171402df", "dst_repo_id":"09b7d3c0-5f0d-49be-9318-7ca136f386cd", "paths":[{"src_path":"/folder-1","dst_path":"/"},{"src_path":"/file-1","dst_path":"/"},{"src_path":"/file-2","dst_path":"/dst-folder"}]}' -H 'Authorization: Token 2bac21cab9eb0c4baac10d1e6fc3cf590f0dcf17' -H 'Accept: application/json; charset=utf-8; indent=4' -H 'Content-Type: application/json' "http://192.168.1.113:8000/api/v2.1/repos/batch-copy-item/"

```

**Sample response**

```
{
    "failed": [
        {
            "src_repo_id": "d4aac5b9-28d4-4372-a4b3-d6de171402df",
            "dst_path": "/dst-folder/",
            "dst_repo_id": "09b7d3c0-5f0d-49be-9318-7ca136f386cd",
            "src_path": "/file-2/",
            "error_msg": "Folder /dst-folder/ not found."
        }
    ],
    "success": [
        {
            "src_repo_id": "d4aac5b9-28d4-4372-a4b3-d6de171402df",
            "dst_path": "/",
            "dst_repo_id": "09b7d3c0-5f0d-49be-9318-7ca136f386cd",
            "src_path": "/folder-1/",
            "dst_obj_name": "folder-1 (2)"
        },
        {
            "src_repo_id": "d4aac5b9-28d4-4372-a4b3-d6de171402df",
            "dst_path": "/",
            "dst_repo_id": "09b7d3c0-5f0d-49be-9318-7ca136f386cd",
            "src_path": "/file-1/",
            "dst_obj_name": "file-1 (2)"
        }
    ]
}

```

**Errors**

* 400 src_repo_id/dst_repo_id/paths invalid.
* 403 Permission denied.
* 404 Library not found.

## Batch Move Items (Deprecated)

**POST** <http://192.168.1.113:8000/api/v2.1/repos/batch-move-item/>

**Request parameters**

Content type of parameter must be `application/json` and passed through POST request's body.

```
{
    "src_repo_id":"",
    "dst_repo_id":"",
    "paths":[
        {"src_path":"","dst_path":""},
        {"src_path":"","dst_path":""},
    ]
}

```

**Sample request**

```
curl -d '{"src_repo_id":"d4aac5b9-28d4-4372-a4b3-d6de171402df", "dst_repo_id":"09b7d3c0-5f0d-49be-9318-7ca136f386cd", "paths":[{"src_path":"/folder-1","dst_path":"/"},{"src_path":"/file-1","dst_path":"/"},{"src_path":"/file-2","dst_path":"/dst-folder"}]}' -H 'Authorization: Token 2bac21cab9eb0c4baac10d1e6fc3cf590f0dcf17' -H 'Accept: application/json; charset=utf-8; indent=4' -H 'Content-Type: application/json' "http://192.168.1.113:8000/api/v2.1/repos/batch-move-item/"

```

**Sample response**

```
{
    "failed": [
        {
            "src_repo_id": "d4aac5b9-28d4-4372-a4b3-d6de171402df",
            "dst_path": "/dst-folder/",
            "dst_repo_id": "09b7d3c0-5f0d-49be-9318-7ca136f386cd",
            "src_path": "/file-2/",
            "error_msg": "Folder /dst-folder/ not found."
        }
    ],
    "success": [
        {
            "src_repo_id": "d4aac5b9-28d4-4372-a4b3-d6de171402df",
            "dst_path": "/",
            "dst_repo_id": "09b7d3c0-5f0d-49be-9318-7ca136f386cd",
            "src_path": "/folder-1/",
            "dst_obj_name": "folder-1 (4)"
        },
        {
            "src_repo_id": "d4aac5b9-28d4-4372-a4b3-d6de171402df",
            "dst_path": "/",
            "dst_repo_id": "09b7d3c0-5f0d-49be-9318-7ca136f386cd",
            "src_path": "/file-1/",
            "dst_obj_name": "file-1 (4)"
        }
    ]
}

```

**Errors**

* 400 src_repo_id/dst_repo_id/paths invalid.
* 403 Permission denied.
* 404 Library not found.

## Copy (Deprecated)

**POST** <https://cloud.seafile.com/api2/repos/{repo_id}/fileops/copy/>

**Request parameters**

* p: source folder path, defaults to `"/"`
* file_names: list of file/folder names to copy. Multiple file/folder names can be seperated by `:`.
* dst_repo: the destination repo id
* dst_dir: the destination folder in `dst_repo`

**Sample request**

```
curl -d "dst_repo=bdf816e6-aba8-468c-962f-77c2fcfd1d1c&dst_dir=/1&file_names=1.md:2.md:test" -H 'Authorization: Token cbd7705c06846425ed5c46ae0313d5b098d24154' -H 'Accept: application/json; indent=4' "https://cloud.seafile.com/api2/repos/bdf816e6-aba8-468c-962f-77c2fcfd1d1c/fileops/copy/?p=/1/test-2"

```

**Sample response**

```
[
    {
        "repo_id": "bdf816e6-aba8-468c-962f-77c2fcfd1d1c",
        "parent_dir": "/1",
        "obj_name": "1 (2).md"
    },
    {
        "repo_id": "bdf816e6-aba8-468c-962f-77c2fcfd1d1c",
        "parent_dir": "/1",
        "obj_name": "2 (2).md"
    },
    {
        "repo_id": "bdf816e6-aba8-468c-962f-77c2fcfd1d1c",
        "parent_dir": "/1",
        "obj_name": "test (2)"
    }
]

```

**Errors**

* 400 missing argument
* 403 You do not have permission to copy file
* 404 repo not found
* 502 failed to copy file

## Move (Deprecated)

**POST** <https://cloud.seafile.com/api2/repos/{repo_id}/fileops/move/>

**Request parameters**

* p: source folder path, defaults to `"/"`
* file_names: list of file/folder names to move. Multiple file/folder names can be seperated by `:`.
* dst_repo: the destination repo id
* dst_dir: the destination folder in `dst_repo`

**Sample request**

```
curl -d "dst_repo=bdf816e6-aba8-468c-962f-77c2fcfd1d1c&dst_dir=/1&file_names=1.md:2.md:test" -H 'Authorization: Token cbd7705c06846425ed5c46ae0313d5b098d24154' -H 'Accept: application/json; indent=4' "https://cloud.seafile.com/api2/repos/bdf816e6-aba8-468c-962f-77c2fcfd1d1c/fileops/move/?p=/1/test-2"

```

**Sample response**

```
[
    {
        "repo_id": "bdf816e6-aba8-468c-962f-77c2fcfd1d1c",
        "parent_dir": "/1",
        "obj_name": "1 (3).md"
    },
    {
        "repo_id": "bdf816e6-aba8-468c-962f-77c2fcfd1d1c",
        "parent_dir": "/1",
        "obj_name": "2 (3).md"
    },
    {
        "repo_id": "bdf816e6-aba8-468c-962f-77c2fcfd1d1c",
        "parent_dir": "/1",
        "obj_name": "test (3)"
    }
]

```

**Errors**

* 400 missing argument
* 403 You do not have permission to move file
* 404 repo not found
* 502 failed to move file

## Copy and Move A Single Item (Deprecated)

**POST** <https://cloud.seafile.com/api/v2.1/copy-move-task/>

**Request parameters**

* src_repo_id
* src_parent_dir
* src_dirent_name
* dst_repo_id
* dst_parent_dir
* operation, `copy` or `move`
* dirent_type, `file` or `dir`

**Sample request**

Sample for copy file.

```
curl -d "src_repo_id=534258e2-761b-465c-9e2c-56e021d3853f&src_parent_dir=/&src_dirent_name=file.md&dst_repo_id=a3fa768d-0f00-4343-8b8d-07b4077881db&dst_parent_dir=/&operation=copy&dirent_type=file" -H 'Authorization: Token ae265ae599a29c238ca25fb63087859798d5f55d' -H 'Accept: application/json; charset=utf-8; indent=4' 'https://cloud.seafile.com/api/v2.1/copy-move-task/'

```

**Sample response**

```
{
    "task_id": "d1ca2b8c-8ab8-4dd4-8ad7-842130764484"
}

```

**Errors**

* 400 path/operation/dirent_type invalid.
* 404 Library/Folder not found.
* 403 Permission denied.
* 500 Internal Server Error

### 


