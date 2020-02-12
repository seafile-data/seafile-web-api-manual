# Share Links

## List all Share Links

This api will list all folder/file download share links in all libraries created by user.

**GET** <https://cloud.seafile.com/api/v2.1/share-links/>

**Sample request**

```
curl -H 'Authorization: Token 0eb24ce5db35a31f70171eca2f760f03f59fa09a' -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/share-links/"

```

**Sample response**

```
[
    {
        "username": "lian@lian.com",
        "repo_id": "c474a093-19dc-4ddf-b0b0-72b33214ba33",
        "ctime": "2017-04-01T02:35:57+00:00",
        "expire_date": "",
        "token": "6afa667ff2c248378b70",
        "view_cnt": 0,
        "link": "https://cloud.seafile.com/d/6afa667ff2c248378b70/",
        "obj_name": "/",
        "path": "/",
        "is_dir": true,
        "permissions": {
            "can_edit": false,
            "can_download": true
        },
        "is_expired": false,
        "repo_name": "seacloud.cc.124"
    },
    {
        "username": "lian@lian.com",
        "repo_id": "104f6537-b3a5-4d42-b8b5-8e47e494e4cf",
        "ctime": "2017-04-01T02:35:29+00:00",
        "expire_date": "",
        "token": "0c4eb0cb104a43caaeef",
        "view_cnt": 0,
        "link": "https://cloud.seafile.com/d/0c4eb0cb104a43caaeef/",
        "obj_name": "folder",
        "path": "/folder/",
        "is_dir": true,
        "permissions": {
            "can_edit": false,
            "can_download": true
        },
        "is_expired": false,
        "repo_name": "for-test-web-api"
    },
    {
        "username": "lian@lian.com",
        "repo_id": "104f6537-b3a5-4d42-b8b5-8e47e494e4cf",
        "ctime": "2017-04-01T02:35:35+00:00",
        "expire_date": "",
        "token": "8c05a00c44db4764b3a5",
        "view_cnt": 0,
        "link": "https://cloud.seafile.com/f/8c05a00c44db4764b3a5/",
        "obj_name": "tmp.md",
        "path": "/tmp.md",
        "is_dir": false,
        "permissions": {
            "can_edit": false,
            "can_download": true
        },
        "is_expired": false,
        "repo_name": "for-test-web-api"
    }
]

```

**Errors**

* 403 Permission denied.
* 500 Internal Server Error

## List Share Links of a Library

This api will list all folder/file download share links in a specific library.

**GET** <https://cloud.seafile.com/api/v2.1/share-links/?repo_id={repo_id}>

**Request parameters**

* repo-id

**Sample request**

```
curl -H 'Authorization: Token 0eb24ce5db35a31f70171eca2f760f03f59fa09a' -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/share-links/?repo_id=104f6537-b3a5-4d42-b8b5-8e47e494e4cf"

```

**Sample response**

```
[
    {
        "username": "lian@lian.com",
        "repo_id": "104f6537-b3a5-4d42-b8b5-8e47e494e4cf",
        "ctime": "2017-04-01T02:35:29+00:00",
        "expire_date": "",
        "token": "0c4eb0cb104a43caaeef",
        "view_cnt": 0,
        "link": "https://cloud.seafile.com/d/0c4eb0cb104a43caaeef/",
        "obj_name": "folder",
        "path": "/folder/",
        "is_dir": true,
        "permissions": {
            "can_edit": false,
            "can_download": true
        },
        "is_expired": false,
        "repo_name": "for-test-web-api"
    },
    {
        "username": "lian@lian.com",
        "repo_id": "104f6537-b3a5-4d42-b8b5-8e47e494e4cf",
        "ctime": "2017-04-01T02:35:35+00:00",
        "expire_date": "",
        "token": "8c05a00c44db4764b3a5",
        "view_cnt": 0,
        "link": "https://cloud.seafile.com/f/8c05a00c44db4764b3a5/",
        "obj_name": "tmp.md",
        "path": "/tmp.md",
        "is_dir": false,
        "permissions": {
            "can_edit": false,
            "can_download": true
        },
        "is_expired": false,
        "repo_name": "for-test-web-api"
    }
]

```

**Errors**

* 403 Permission denied.
* 404 library not found.
* 500 Internal Server Error

## List Share Link of a Folder (File)

This api will list download share link info of a specific folder/file.

**GET** <https://cloud.seafile.com/api/v2.1/share-links/?repo_id={rpeo_id}&path={path}>

**Request parameters**

* repo-id
* path, could be path of a foler or a file.

**Sample request**

Get folder download share link.

```
curl -H 'Authorization: Token 0eb24ce5db35a31f70171eca2f760f03f59fa09a' -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/share-links/?repo_id=104f6537-b3a5-4d42-b8b5-8e47e494e4cf&path=/folder/"

```

**Sample response**

```
[
    {
        "username": "lian@lian.com",
        "repo_id": "104f6537-b3a5-4d42-b8b5-8e47e494e4cf",
        "ctime": "2017-04-01T02:35:29+00:00",
        "expire_date": "",
        "token": "0c4eb0cb104a43caaeef",
        "view_cnt": 0,
        "link": "https://cloud.seafile.com/d/0c4eb0cb104a43caaeef/",
        "obj_name": "folder",
        "path": "/folder/",
        "is_dir": true,
        "permissions": {
            "can_edit": false,
            "can_download": true
        },
        "is_expired": false,
        "repo_name": "for-test-web-api"
    }
]

```

or a empty list `[]` if this folder has no download share link.

Get file download share link.

```
curl -H 'Authorization: Token 0eb24ce5db35a31f70171eca2f760f03f59fa09a' -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/share-links/?repo_id=104f6537-b3a5-4d42-b8b5-8e47e494e4cf&path=/tmp.md"

```

**Sample response**

```
[
    {
        "username": "lian@lian.com",
        "repo_id": "104f6537-b3a5-4d42-b8b5-8e47e494e4cf",
        "ctime": "2017-04-01T02:35:35+00:00",
        "expire_date": "",
        "token": "8c05a00c44db4764b3a5",
        "view_cnt": 0,
        "link": "https://cloud.seafile.com/f/8c05a00c44db4764b3a5/",
        "obj_name": "tmp.md",
        "path": "/tmp.md",
        "is_dir": false,
        "permissions": {
            "can_edit": false,
            "can_download": true
        },
        "is_expired": false,
        "repo_name": "for-test-web-api"
    }
]

```

or a empty list `[]` if this file has no download share link.

**Errors**

* 403 Permission denied.
* 404 folder/library not found.
* 500 Internal Server Error

## Create Share Link

**POST** <https://cloud.seafile.com/api/v2.1/share-links/>

**Request parameters**

Content type of parameter must be `application/json` and passed through POST request's body.

* repo-id
* path (file/folder path)
* password (not necessary)
* expire_days (not necessary)
* permissions (not necessary): {"can_edit":"false(or true)","can_download":"false(or true)"}

**Sample request**

Create download link for file with can_edit permission is false and can_download permission is false.

```
curl -d '{"repo_id":"795f0080-2fca-432e-9317-ac7ae884a0b3", "path":"/123.md", "permissions":{"can_edit":false,"can_download":false}}' -H 'Authorization: Token f651b0fb62978961b68e1bf8d740647d2fc4be8b' -H 'Content-type: application/json' -H 'Accept: application/json; indent=4' https://demo.seafile.top/api/v2.1/share-links/

```

**Sample response**

```
{
    "username": "admin@seafile.com",
    "repo_id": "795f0080-2fca-432e-9317-ac7ae884a0b3",
    "ctime": "2019-06-10T11:30:26+08:00",
    "expire_date": "",
    "token": "c67c8093b1df4c28bd59",
    "view_cnt": 0,
    "link": "https://demo.seafile.top/f/c67c8093b1df4c28bd59/",
    "obj_name": "123.md",
    "path": "/123.md",
    "is_dir": false,
    "permissions": {
        "can_edit": false,
        "can_download": false
    },
    "is_expired": false,
    "repo_name": "123"
}

```

**Sample request**

Create download link for directory with password and expire date

```
curl -d "path=/bar/&repo_id=62ca6cf9-dab6-47e5-badc-bab13d9220ce&password=password&expire_days=6" -H 'Authorization: Token ef12bf1e66a1aa797a1d6556fdc9ae84f1e9249f' -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api/v2.1/share-links/

```

**Sample response**

```
{
    "username": "foo@foo.com",
    "repo_id": "e1da66f3-1c36-4eb9-9dee-39d01ba282b0",
    "ctime": "2019-05-23T06:50:05+00:00",
    "expire_date": "",
    "token": "78aa8573ffec440eba36",
    "view_cnt": 0,
    "link": "http://127.0.0.1:8000/d/78aa8573ffec440eba36/",
    "obj_name": "foo",
    "path": "/foo/",
    "is_dir": true,
    "permissions": {
        "can_edit": false,
        "can_download": true
    },
    "is_expired": false,
    "repo_name": "My Library"
}

```

**Errors**

* 400 path/repo_id invalid
* 403 Permission denied.
* 404 file/folder/library not found.
* 500 Internal Server Error

## Delete Share Link

**DELETE** <https://cloud.seafile.com/api/v2.1/share-links/{token}/>

**Sample request**

```
curl -X DELETE -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd' "https://cloud.seafile.com/api/v2.1/share-links/0ae587a7d1/"

```

**Sample response**

```
{"success":true}

```

#### <a id="send-share-link-email"></a>Send Share Link Email

**POST** <https://cloud.seafile.com/api2/send-share-link/>

**Request parameters**

* token
* email
* extra_msg (not necessary)

**Sample request**

```
curl -d "email=sample@eamil.com,invalid-email&token=4cbd625c5e" -H 'Authorization: Token ef12bf1e66a1aa797a1d6556fdc9ae84f1e9249f' -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api2/send-share-link/

```

**Sample response**

```
{
    "failed": [
        {
            "email": "invalid-email",
            "error_msg": "email invalid."
        }
    ],
    "success": [
        "sample@eamil.com"
    ]
}

```

**Errors**

* 400 token/repo_id invalid
* 403 Permission denied.
* 403 Sending shared link failed. Email service is not properly configured, please contact administrator.
* 404 token/library not found

## List items in Folder Download Link

**GET** <https://cloud.seafile.com/api2/d/{token}/dir/>

**Request parameters**

* token (upload link token)
* p (sub folder path)
* password (if link is encrypted)

**Sample request**

```
curl -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd' "https://cloud.seafile.com/api2/d/3af7c46595/dir/?path=/subfolder/"

```

**Sample response**

```
[{"mtime": 1436846750, "type": "dir", "name": "sadof", "id": "1806dbdb700b7bcd49e6275107c7ccf7b3ea1776"}, {"id": "bdb06f6de972c42893fda590ac954988b562429c", "mtime": 1436431020, "type": "file", "name": "test.mdert", "size": 20}]

```

## List Direntry in Dir Download Link

**GET** <http://192.168.1.113:8000/api/v2.1/share-links/dd4c8f4445f44ae48728/dirents/?path=/>

**Request parameters**

* `token`: Folder share link token.
* `path`: Sub folder path in folder share link. Default is `/`.

**Sample request**

```
curl -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd' -H 'Accept: application/json; indent=4' "http://192.168.1.113:8000/api/v2.1/share-links/dd4c8f4445f44ae48728/dirents/?path=/"

```

**Sample response**

```
{
    "dirent_list": [
        {
            "is_dir": true,
            "last_modified": "2019-04-03T11:44:56+08:00",
            "folder_path": "/folder/",
            "folder_name": "folder",
            "size": 0
        },
        {
            "file_name": "1.txt",
            "is_dir": false,
            "last_modified": "2019-04-03T11:44:56+08:00",
            "file_path": "/1.txt",
            "size": 3
        },
        {
            "file_name": "Screenshot from 2019-03-15 15-23-00.png",
            "last_modified": "2019-04-08T15:48:16+08:00",
            "encoded_thumbnail_src": "thumbnail/5df4fcee99e04e869d18/48/Screenshot%20from%202019-03-15%2015-23-00.png",
            "is_dir": false,
            "file_path": "/Screenshot from 2019-03-15 15-23-00.png",
            "size": 214653
        }
    ]
}

```

**Errors**

* 403 Permission denied.
* 404 token/library/folder not found.
* 500 Internal Server Error


