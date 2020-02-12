# Directories

## List Items in Directory

**GET** <https://cloud.seafile.com/api2/repos/{repo-id}/dir/>

* repo-id
* p (optional): The path to a directory. If `p` is missing, then defaults to '/' which is the top directory.
* oid (optional): The object id of the directory. The object id is the checksum of the directory contents.
* t (optional): If set `t` argument as `f`, will only return file entries, and `d` for only dir entries.
* recursive (optional): If set `t` argument as `d` **AND** `recursive` argument as `1`, return all dir entries recursively

**Sample request**

request file/dir list of a folder.

```
curl -H "Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d9b477fd" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api2/repos/99b758e6-91ab-4265-b705-925367374cf0/dir/?p=/foo

```

**Sample response**

   If oid is the same as the current oid of the directory, returns `"uptodate"` , else returns

```
[
{
    "id": "0000000000000000000000000000000000000000",
    "type": "file",
    "name": "test1.c",
    "size": 0
},
{
    "id": "e4fe14c8cda2206bb9606907cf4fca6b30221cf9",
    "type": "dir",
    "name": "test_dir"
}
]

```

**Sample request**

request recursive dir list of a folder.

```
curl -H "Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d9b477fd" -H 'Accept: application/json; indent=4' 'https://cloud.seafile.com/api2/repos/99b758e6-91ab-4265-b705-925367374cf0/dir/?t=d&recursive=1'

```

**Sample response**

```
[{'id': u'5e307101cad46398fb5fe52d9177836f73c4bae8',
  'mtime': 1471490386,
  'name': u'123',
  'parent_dir': u'/video',
  'permission': u'rw',
  'type': 'dir'},
 {'id': u'0000000000000000000000000000000000000000',
  'mtime': 1471490391,
  'name': u'123-2',
  'parent_dir': u'/video',
  'permission': u'rw',
  'type': 'dir'},
 {'id': u'0000000000000000000000000000000000000000',
  'mtime': 1471490379,
  'name': u'456',
  'parent_dir': u'/video/123',
  'permission': u'rw',
  'type': 'dir'},
 {'id': u'0000000000000000000000000000000000000000',
  'mtime': 1471490386,
  'name': u'456-2',
  'parent_dir': u'/video/123',
  'permission': u'rw',
  'type': 'dir'},
 {'id': u'd8f5f80fbd89bf5634dcf9e21b569c487541d34e',
  'mtime': 1471490391,
  'name': u'video',
  'parent_dir': '/',
  'permission': u'rw',
  'type': 'dir'}
]

```

**Errors**

* 404 The path is not exist.
* 440 Repo is encrypted, and password is not provided.
* 520 Operation failed..

## Get Directory Detail

**GET** <https://cloud.seafile.com/api/v2.1/repos/{repo_id}/dir/detail/?path={path}>

* repo_id
* path, should not be `/`.

**Sample request**

```
curl -H "Authorization: Token e71c00e93af863ba9bcddb61a46bb4de11d713fc" -H 'Accept: application/json; indent=4' "https://cloud.seafile.com/api/v2.1/repos/d4f596ed-09ea-4ac6-8d59-12acbd089097/dir/detail/?path=Develop"

```

**Sample response**

```
{
    "repo_id": "d4f596ed-09ea-4ac6-8d59-12acbd089097",
    "name": "Develop",
    "mtime": "2018-01-05T17:45:41+08:00",
    "path": "/Develop/",
}

```

**Errors**

* 400 path invalid.
* 403 Permission denied.
* 404 Folder not found.
* 404 Library not found.
* 500 Internal Server Error

## Move Directory

Use the batch operation API to move a single directory: [batch operations for files and directories](files-directories-batch-op.md)

## Copy Directory

Use the batch operation API to copy a single directory: [batch operations for files and directories](files-directories-batch-op.md)

## Create New Directory

**POST** <https://cloud.seafile.com/api2/repos/{repo-id}/dir/>

* repo-id
* p
* operation=mkdir (post)

**Sample request**

```
curl -d "operation=mkdir" -v -H 'Authorization: Token 076de58233c09f19e7a5179abff14ad55987350e' -H 'Accept: application/json; charset=utf-8; indent=4' https://cloud.seafile.com/api2/repos/21b941c2-5411-4372-a514-00b62ab99ef2/dir/?p=/foo

```

**Sample response**

```
...
< HTTP/1.0 201 CREATED
< Location: https://cloud.seafile.com/api2/repos/dae8cecc-2359-4d33-aa42-01b7846c4b32/dir/?p=/foo
...

"success"

```

**Success**

   Response code 201(Created) is returned, and Location header provides the url of created directory.

**Errors**

* 400 Path is missing or invalid(e.g. p=/)
* 520 Operation failed.

**Notes**

   Newly created directory will be renamed if the name is duplicated.

## Rename Directory

**POST** <https://cloud.seafile.com/api2/repos/{repo-id}/dir/?p=/foo>

**Parameters**

* repo-id
* p (path)
* operation=rename
* newname (the new name of the directory)

**Sample request**

```
curl -d  "operation=rename&newname=pinkfloyd_newfolder" -v  -H 'Authorization: Tokacd9c6ccb8133606d94ff8e61d99b477fd' -H 'Accept: application/json; charset=utf-8; indent=4' https://cloud.seafile.com/api2/repos/dae8cecc-2359-4d33-aa42-01b7846c4b32/dir/?p=/foo

```

**Success**

   Response code 200 if everything is ok

**Errors**

* 403 if You do not have permission to rename a folder
* 400 if newname is not given
* 520 if Failed to rename directory (generic problem)

**Notes**

   If the new name is the same of the old name no operation will be done.

## Delete Directory

**DELETE** <https://cloud.seafile.com/api2/repos/{repo-id}/dir/>

* repo-id
* p

**Sample request**

```
curl -X DELETE -v  -H 'Authorization: Token f2210dacd3606d94ff8e61d99b477fd' -H 'Accept: application/json; charset=utf-8; indent=4' https://cloud.seafile.com/api2/repos/dae8cecc-2359-4d33-aa42-01b7846c4b32/dir/?p=/foo

```

**Sample response**

```
...
< HTTP/1.0 200 OK
...
"success"

```

**Success**

   Response code is 200(OK), and a string `"success"` is returned.

**Errors**

* 400 Path is missing or invalid(e.g. p=/)
* 520 Operation failed.

## Revert Directory to a History Status

**PUT** <https://cloud.seafile.com/api2/repos/7460f7ac-a0ff-4585-8906-bb5a57d2e118/dir/revert/>

* repo_id
* p
* commit_id

**Sample request**

```
curl -X PUT -d "p=/456&commit_id=b1a33768517f65ac7d618ff078dd27855374c7e0" -H 'Authorization: Token 0eb24ce5db35a31f70171eca2f760f03f59fa09a' -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api2/repos/7460f7ac-a0ff-4585-8906-bb5a57d2e118/dir/revert/"

```

**Sample response**

```
{
    "success": true
}

```

**Errors**

* 400 path invalid.
* 400 commit_id invalid.
* 404 Library/Folder not found.
* 403 Permission denied.
* 500 Internal Server Error

## Download Directory

Perform the following two steps to download directory

### Get Task Token

**GET** <https://cloud.seafile.com/api/v2.1/repos/{repo-id}/zip-task/?parent_dir={parent_dir}&dirents={dir}>

* repo-id
* parent_dir
* dirents

**Sample request**

```
curl -H 'Authorization: Token 0eb24ce5db35a31f70171eca2f760f03f59fa09a' -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/repos/7460f7ac-a0ff-4585-8906-bb5a57d2e118/zip-task/?parent_dir=/&dirents=my_dir_name"

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
* 404 Library/Folder not found.
* 403 Permission denied.

### Query Task Progress

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

After the task finished, you can access the Zipped directory using URL like:

```
FILE_SERVER_ROOT/zip/{zip_token}

```

For example, `https://cloud.seafile.com/seafhttp/zip/b2272645-35ee-44ce-8f68-07c022107015` is the final URL in this case.

## Move directory with items merged

**POST** <http://192.168.1.113:8000/api/v2.1/move-folder-merge/>

* src_repo_id
* src_parent_dir
* src_dirent_name
* dst_repo_id
* dst_parent_dir

**Sample request**

```
curl -d 'src_repo_id=09b7d3c0-5f0d-49be-9318-7ca136f386cd&src_parent_dir=/&src_dirent_name=1&dst_repo_id=d4aac5b9-28d4-4372-a4b3-d6de171402df&dst_parent_dir=/' -H 'Authorization: Token 2bac21cab9eb0c4baac10d1e6fc3cf590f0dcf17' -H 'Accept: application/json; charset=utf-8; indent=4' "http://192.168.1.113:8000/api/v2.1/move-folder-merge/"

```

**Sample response**

```
{
    "success": true
}

```

**Errors**

* 400 parameter invalid.
* 404 Library/Folder not found.
* 403 Permission denied.
* 443 Out of quota.


