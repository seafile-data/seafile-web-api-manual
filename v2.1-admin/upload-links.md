# Upload Links

## Get Shared Dir Info

**GET** https://cloud.seafile.com/api/v2.1/admin/upload-links/{token}/

**Request parameters**

* token

**Sample request**
```
curl -H 'Authorization: Token cbd7705c06846425ed5c46ae0313d5b098d24154' -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/admin/upload-links/360fe7d6dc684045b7f6/"
```

**Sample response**
```
{
    "view_cnt": 0,
    "ctime": "2017-06-20T08:37:22+00:00",
    "creator_name": "name of lian",
    "creator_email": "lian@lian.com",
    "creator_contact_email": "lian@lian.com",
    "token": "360fe7d6dc684045b7f6",
    "repo_id": "0a5647c8-7708-445a-bd80-49f04b85b153",
    "link": "https://cloud.seafile.com/u/d/360fe7d6dc684045b7f6/",
    "obj_name": "asdf",
    "path": "/asdf/",
    "repo_name": "sadfdaa"
}
```

**Errors**

* 403 Permission denied.
* 404 Upload link not found.

## Upload

**GET** https://cloud.seafile.com/api/v2.1/admin/upload-links/{token}/upload/

**Request parameters**

* token

**Sample request**
```
curl -H 'Authorization: Token cbd7705c06846425ed5c46ae0313d5b098d24154' -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/admin/upload-links/360fe7d6dc684045b7f6/upload/"
```

**Sample response**
```
{
    "upload_link": "http://192.168.1.124:8082/upload-api/b08b20e4-beb2-4c7a-af03-fed6be859330"
}
```

After get upload link, you can upload file to the shared dir, for more info, please see [Upload File](#upload-file-1).

**Errors**

* 403 Permission denied.
* 404 Upload link not found.
* 404 Folder not found.

#### <a id="admin-only-upload-link-check-password"></a>Check Password

**GET** https://cloud.seafile.com/api/v2.1/admin/upload-links/{token}/check-password/

**Request parameters**

* token
* password

**Sample request**
```
curl -d 'password=11111111' -H 'Authorization: Token cbd7705c06846425ed5c46ae0313d5b098d24154' -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/admin/upload-links/360fe7d6dc684045b7f6/check-password/"
```

**Sample response**
```
{
    "success": true
}
```

**Errors**

* 400 Upload link is not encrypted.
* 400 password invalid.
* 403 Permission denied.
* 403 Password is not correct.
* 404 Upload link not found.
