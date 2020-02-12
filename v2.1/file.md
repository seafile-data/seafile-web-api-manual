# Files

## Download File

**GET** <https://cloud.seafile.com/api2/repos/{repo-id}/file/?p=/foo>

**Request parameters**

* repo-id
* p
* reuse (optional): Set `reuse` to `1` if you want the generated download link can be accessed more than once in one hour.

**Sample request**

```
curl  -v  -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd' -H 'Accept: application/json; charset=utf-8; indent=4' 'https://cloud.seafile.com/api2/repos/dae8cecc-2359-4d33-aa42-01b7846c4b32/file/?p=/foo.c&reuse=1'

```

**Sample response**

```
"https://cloud.seafile.com:8082/files/adee6094/foo.c"

```

**Errors**

* 400 Path is missing
* 404 File not found
* 520 Operation failed.

## Get File Detail

**GET** <https://cloud.seafile.com/api2/repos/{repo-id}/file/detail/?p=/foo.c>

* repo-id
* p

**Sample request**

```
curl -H 'Authorization: Token f2210dacd3606d94ff8e61d99b477fd' -H 'Accept: application/json; charset=utf-8; indent=4' https://cloud.seafile.com/api2/repos/dae8cecc-2359-4d33-aa42-01b7846c4b32/file/detail/?p=/foo.c

```

**Sample response**

```
{
    "last_modifier_name": "\u8d85\u7ba1",
    "uploader_email": "03e7957e09ee43d9b57c9b2b4c741668@ifile.com",
    "upload_time": "2018-07-11T05:14:20+08:00",
    "name": "1.md",
    "permission": "rw",
    "uploader_name": "\u8d85\u7ba1",
    "uploader_contact_email": "03e7957e09ee43d9b57c9b2b4c741668@ifile.com",
    "last_modified": "2018-07-16T15:03:56+08:00",
    "mtime": 1531724636,
    "starred": false,
    "size": 2,
    "type": "file",
    "id": "86dd07538e51f8d437ecc25d9a48250041fef5a0",
    "last_modifier_email": "03e7957e09ee43d9b57c9b2b4c741668@ifile.com",
    "last_modifier_contact_email": "03e7957e09ee43d9b57c9b2b4c741668@ifile.com"
}

```

**Errors**

* 400 p invalid.
* 404 Library/File not found.
* 403 Permission denied.

## Create File

**POST** <https://cloud.seafile.com/api/v2.1/repos/{repo_id}/file/?p={file_path}>

**Request parameters**

* repo-id
* p
* operation

**Sample request**

```
curl -d 'operation=create' -H 'Authorization: Token c5de3074be40861f399f02c65149c6460bbf073f' "https://cloud.seafile.com/api/v2.1/repos/7460f7ac-a0ff-4585-8906-bb5a57d2e118/file/?p=/test.xlsx"

```

**Sample response**

```
{
    'is_locked': False,
    'mtime': '2017-09-12T14:57:42+08:00',
    'obj_id': u'44bdca6005429390d1ecc6943b05c821bd30917a',
    'obj_name': u'test.xlsx',
    'parent_dir': u'/',
    'repo_id': u'7460f7ac-a0ff-4585-8906-bb5a57d2e118',
    'size': 7631,
    'type': 'file'
}

```

**Errors**

* 400 operation/name invalid.
* 400 operation can only be 'create', 'rename', 'move', 'copy' or 'revert'.
* 404 Library/Folder not found.
* 403 Permission denied.
* 500 Internal Server Error

## Rename File

**POST** <https://cloud.seafile.com/api2/repos/{repo-id}/file/?p=/foo.c>

**Request parameters**

* repo-id
* p
* operation=rename
* newname

**Sample request**

```
curl -v -d "operation=rename&newname=newfoo.c" -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd' -H 'Accept: application/json; charset=utf-8; indent=4' https://cloud.seafile.com/api2/repos/dae8cecc-2359-4d33-aa42-01b7846c4b32/file/?p=/foo.c

```

**Sample response**

```
...
< HTTP/1.1 301 MOVED PERMANENTLY
...
"success"

```

**Success**

   Response code is 301, and a string `"success"` is returned.

**Errors**

* 400 BAD REQUEST, Path is missing or invalid(e.g. p=/) or newname is missing(newname too long)
* 403 FORBIDDEN, You do not have permission to rename file
* 404 NOT FOUND, repo not found
* 409 CONFLICT, the newname is the same to the old
* 520 OPERATION FAILED, fail to rename file

## Lock File

**PUT** <https://cloud.seafile.com/api2/repos/{repo-id}/file/>

**Request parameters**

* repo-id
* p
* operation

**Sample request**

```
curl -v -X PUT -d "operation=lock&p=/foo.c" -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd' -H 'Accept: application/json; charset=utf-8; indent=4' https://cloud.seafile.com/api2/repos/dae8cecc-2359-4d33-aa42-01b7846c4b32/file/

```

**Sample response**

```
...
< HTTP/1.0 200 OK
...
"success"

```

**Success**

   Response code is 200, and a string `"success"` is returned.

**Errors**

* 400 BAD REQUEST, Path is missing or invalid(e.g. p=/)
* 403 FORBIDDEN, You do not have permission to lock file
* 404 NOT FOUND, repo not found
* 520 OPERATION FAILED, fail to lock file

## Unlock File

**PUT** <https://cloud.seafile.com/api2/repos/{repo-id}/file/>

**Request parameters**

* repo-id
* p
* operation

**Sample request**

```
curl -v -X PUT -d "operation=unlock&p=/foo.c" -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd' -H 'Accept: application/json; charset=utf-8; indent=4' https://cloud.seafile.com/api2/repos/dae8cecc-2359-4d33-aa42-01b7846c4b32/file/

```

**Sample response**

```
...
< HTTP/1.0 200 OK
...
"success"

```

**Success**

   Response code is 200, and a string `"success"` is returned.

**Errors**

* 400 BAD REQUEST, Path is missing or invalid(e.g. p=/)
* 403 FORBIDDEN, You do not have permission to lock file
* 404 NOT FOUND, repo not found
* 520 OPERATION FAILED, fail to unlock file

## Move File

**POST** <https://cloud.seafile.com/api2/repos/{repo-id}/file/?p=/foo.c>

**Request parameters**

* repo-id
* p
* operation
* dst_repo
* dst_dir

**Sample request**

```
curl -v -d "operation=move&dst_repo=affc837f-7fdd-4e91-b88a-32caf99897f2&dst_dir=/123" -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd' -H 'Accept: application/json; charset=utf-8; indent=4' https://cloud.seafile.com/api2/repos/dae8cecc-2359-4d33-aa42-01b7846c4b32/file/?p=/foo.c

```

**Sample response**

```
...
< HTTP/1.1 301 MOVED PERMANENTLY
...
{
    "repo_id": "affc837f-7fdd-4e91-b88a-32caf99897f2",
    "parent_dir": "/123",
    "obj_name": "foo.c"
}

```

**Success**

   Response code is 301, and a string `"success"` is returned.

**Errors**

* 400 BAD REQUEST, Path is missing or invalid(e.g. p=/)
* 403 FORBIDDEN, You do not have permission to move file
* 404 NOT FOUND, repo not found
* 500 INTERNAL SERVER ERROR

## Copy File

**POST** <https://cloud.seafile.com/api2/repos/{repo-id}/file/?p=/foo.c>

**Request parameters**

* repo-id
* p
* operation
* dst_repo
* dst_dir

**Sample request**

```
curl -v -d "operation=copy&dst_repo=73ddb2b8-dda8-471b-b7a7-ca742b07483c&dst_dir=/123" -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd' -H 'Accept: application/json; charset=utf-8; indent=4' https://cloud.seafile.com/api2/repos/c7436518-5f46-4296-97db-2fcba4c8c8db/file/?p=/foo.c

```

**Sample response**

```
...
< HTTP/1.1 200 OK
...
{
    "repo_id": "73ddb2b8-dda8-471b-b7a7-ca742b07483c",
    "parent_dir": "/123",
    "obj_name": "foo.c"
}

```

**Success**

   Response code is 200, and a string `"success"` is returned.

**Errors**

* 400 BAD REQUEST, Path is missing or invalid(e.g. p=/)
* 403 FORBIDDEN, You do not have permission to copy file
* 500 INTERNAL SERVER ERROR

## Delete File

**DELETE** <https://cloud.seafile.com/api2/repos/{repo-id}/file/?p=/foo>

**Request parameters**

* repo-id
* p

**Sample request**

```
curl -X DELETE -v  -H 'Authorization: Token f2210dacd3606d94ff8e61d99b477fd' -H 'Accept: application/json; charset=utf-8; indent=4' https://cloud.seafile.com/api2/repos/dae8cecc-2359-4d33-aa42-01b7846c4b32/file/?p=/foo.c

```

**Sample response**

```
...
< HTTP/1.0 200 OK
...
"success"

```

**Errors**

* 400 Path is missing
* 520 Operation failed.

**Note**

   This can also be used to delete directory.
   
   

## Get Smart Link for a File

**GET** "http://192.168.1.113:8000/api/v2.1/smart-link/?repo_id={repo_id}&path={path}&is_dir={is_dir}"

**Request parameters**

* `repo_id`
* `path`, path of file/folder.
* `is_dir`, `true` or `false`.

**Sample request for view**

```
curl -H "Authorization: Token 1cb7908b876d9b1708c757a347f2e6346456ab91" -H 'Accept: application/json; indent=4' "http://192.168.1.113:8000/api/v2.1/smart-link/?repo_id=d4f596ed-09ea-4ac6-8d59-12acbd089097&path=/8.md&is_dir=false"
```

**Sample response**

```
{
    "smart_link": "http://192.168.1.113:8000/smart-link/3eb1657f-db82-4329-a05e-9c087022fb2f/8.md"
}
```

**Errors**

* 400 repo_id/path/is_dir invalid.
* 400 is_dir can only be 'true' or 'false'.
* 403 Permission denied.
* 404 Library/Foldef/File/ not found.
* 500 Internal Server Error
