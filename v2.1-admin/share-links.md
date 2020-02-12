# Share Links

## Get Shared File/Dir Info

**GET** https://cloud.seafile.com/api/v2.1/admin/share-links/{token}/

**Request parameters**

* token

**Sample request**
```
curl -H 'Authorization: Token cbd7705c06846425ed5c46ae0313d5b098d24154' -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/admin/share-links/db62f56baf1b4460996e/"
```

**Sample response**
```
{
    "repo_id": "0a5647c8-7708-445a-bd80-49f04b85b153",
    "ctime": "2017-06-20T08:37:13+00:00",
    "creator_name": "name of lian",
    "creator_email": "lian@lian.com",
    "obj_name": "asdf",
    "token": "db62f56baf1b4460996e",
    "view_cnt": 8,
    "link": "https://cloud.seafile.com/d/db62f56baf1b4460996e/",
    "expire_date": "2017-06-23T08:37:13+00:00",
    "path": "/asdf/",
    "creator_contact_email": "lian@lian.com",
    "is_dir": true,
    "permissions": {
        "can_preview": true,
        "can_download": true
    },
    "is_expired": false,
    "repo_name": "sadfdaa"
}
```

**Errors**

* 403 Permission denied.
* 404 Share link not found.

## List Items in Folder Shared Links 

**GET** https://cloud.seafile.com/api/v2.1/admin/share-links/{token}/dirents/

**Request parameters**

* token
* path, sub-folder of shared dir, default is `/`.

**Sample request**
```
curl -H 'Authorization: Token cbd7705c06846425ed5c46ae0313d5b098d24154' -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/admin/share-links/db62f56baf1b4460996e/dirents/?path=/sdf"
```

**Sample response**
```
[
    {
        "path": "/sdf/1122",
        "is_dir": true,
        "size": 0,
        "last_modified": "2017-06-21T02:18:40+00:00",
        "obj_name": "1122"
    },
    {
        "path": "/sdf/12.docx",
        "is_dir": false,
        "size": 457426,
        "last_modified": "2017-06-20T10:09:53+00:00",
        "obj_name": "12.docx"
    },
    {
        "path": "/sdf/slack-desktop-2.3.3-amd64.deb",
        "is_dir": false,
        "size": 47434600,
        "last_modified": "2017-06-20T10:27:47+00:00",
        "obj_name": "slack-desktop-2.3.3-amd64.deb"
    }
]
```

**Errors**

* 403 Permission denied.
* 404 Share link not found.

## Download File/Dir

**GET** https://cloud.seafile.com/api/v2.1/admin/share-links/{token}/download/

**Request parameters**

* token
* type, only used for download (sub) file/folder of shared dir, `file` or `folder`.
* path, only used for download (sub) file/folder of shared dir.

**Sample request for download (sub) folder in shared dir**
```
curl -H 'Authorization: Token cbd7705c06846425ed5c46ae0313d5b098d24154' -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/admin/share-links/db62f56baf1b4460996e/download/?path=/sdf&type=folder"
```

**Sample response for download (sub) folder in shared dir**
```
{
    "download_link": "http://192.168.1.124:8082/zip/395e0ea8-3936-4084-b650-64a93d8a313d"
}
```

After you get the download link for the (sub) folder, you should use the token in the download link (here's `395e0ea8-3936-4084-b650-64a93d8a313d`) to check if the background compression packaging has been completed by [Query Task Progress](#download-directory-query-task-progress), once it is finished, you can use the download link to download the (sub) folder.

**Sample request for download (sub) file in shared dir**
```
curl -H 'Authorization: Token cbd7705c06846425ed5c46ae0313d5b098d24154' -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/admin/share-links/db62f56baf1b4460996e/download/?path=/sdf/12.docx&type=file"
```

**Sample response for download (sub) file in shared dir**
```
{
    "download_link": "http://192.168.1.124:8082/files/2fec8ae7-ffd5-4586-b125-7234e7a69656/12.docx"
}
```

**Sample request for download shared file**
```
curl -H 'Authorization: Token cbd7705c06846425ed5c46ae0313d5b098d24154' -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/admin/share-links/dac219add64f4a4b9c51/download/"
```

**Sample response for download shared file**
```
{
    "download_link": "http://192.168.1.124:8082/files/a34af6cb-4762-4eea-b5a4-0b924e6767d0/excel-view.xlsx"
}
```

**Errors**

* 403 Permission denied.
* 404 Share link not found.
* 404 File not found.
* 404 Folder not found.
* 404 Library not found.
* 500 Internal Server Error

## Check Password

**GET** https://cloud.seafile.com/api/v2.1/admin/share-links/{token}/check-password/

**Request parameters**

* token
* password

**Sample request**
```
curl -d 'password=11111111' -H 'Authorization: Token cbd7705c06846425ed5c46ae0313d5b098d24154' -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/admin/share-links/db62f56baf1b4460996e/check-password/"
```

**Sample response**
```
{
    "success": true
}
```

**Errors**

* 400 Share link is not encrypted.
* 400 password invalid.
* 403 Permission denied.
* 403 Password is not correct.
* 404 Share link not found.
