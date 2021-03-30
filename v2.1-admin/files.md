# Files

If you want to use APIs, you must set `ENABLE_SYS_ADMIN_VIEW_REPO` to `True` in `seahub_settings.py`.

## List folder

**GET** https://cloud.seafile.com/api/v2.1/admin/libraries/{repo_id}/dirents/?parent_dir={parent_dir}

* repo-id
* parent_dir

**Sample request**

    curl -H "Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api/v2.1/admin/libraries/104f6537-b3a5-4d42-b8b5-8e47e494e4cf/dirents/?parent_dir=/asd

**Sample response**

```
{
    "repo_id": "c474a093-19dc-4ddf-b0b0-72b33214ba33",
    "dirent_list": [
        {
            "file_size": "",
            "last_update": "2016-12-19T03:35:14+00:00",
            "is_file": false,
            "obj_name": "book"
        },
        {
            "file_size": "",
            "last_update": "2016-10-12T07:43:32+00:00",
            "is_file": false,
            "obj_name": "image"
        },
        {
            "file_size": "47.0 KB",
            "last_update": "2017-02-13T02:41:05+00:00",
            "is_file": true,
            "obj_name": "123.md"
        }
    ],
    "is_system_library": false,
    "repo_name": "seacloud.cc.124"
}
```

**Errors**

* 400 parent_dir invalid.
* 403 Feature disabled.
* 403 Permission error, only administrator can perform this action
* 404 Library not found.
* 404 Folder not found.


## Copy item


**PUT** https://cloud.seafile.com/api/v2.1/admin/libraries/{repo_id}/dirent/?path={path}

* `repo_id`, source library id when copy file/folder.
* `path`, full path of source file/folder.
* `dst_repo_id`, destination library id. (source library id will be used if not provided.)
* `dst_dir`, destination folder's path. (root path '/'  will be used if not provided.)

**Sample request**

```
curl -X PUT -d "dst_repo_id=0d38067b-ca3f-4160-8e1c-504feae25fd5&dst_dir=/Develop/" -H "Authorization: Token e71c00e93af863ba9bcddb61a46bb4de11d713fc" -H 'Accept: application/json; indent=4' "http://192.168.1.113:8000/api/v2.1/admin/libraries/d4f596ed-09ea-4ac6-8d59-12acbd089097/dirent/?path=/Test/"
```

**Sample response**

```
{
    "success": true
}
```

**Errors**

* 400 path invalid.
* 403 Feature disabled.
* 403 Permission error, only administrator can perform this action
* 404 Repo not found.
* 404 File/Folder not found.
