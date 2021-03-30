# Upload Links

## List Upload Links

**GET** https://cloud.seafile.com/api/v2.1/upload-links/

**Sample request**

    curl -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd' "https://cloud.seafile.com/api/v2.1/upload-links/"

**Sample response**

    [{"username":"lian@lian.com","repo_id":"62ca6cf9-dab6-47e5-badc-bab13d9220ce","ctime":"2016-03-03T15:26:15.223","token":"9a5d5c8391","link":"https://cloud.seafile.com/u/d/9a5d5c8391/","path":"/"},{"username":"lian@lian.com","repo_id":"78c620ee-2989-4427-8eff-7748f4fbebc0","ctime":"2016-03-04T05:37:17.968","token":"d17d87ea4d","link":"https://cloud.seafile.com/u/d/d17d87ea4d/","path":"/yutong/"}]

## Create Upload Link

**POST** https://cloud.seafile.com/api/v2.1/upload-links/

**Request parameters**

* repo-id
* path (file/folder path)
* password (not necessary)

**Sample request**

Create upload link for directory with password

    curl -d "path=/bar/&repo_id=afc3b694-7d4c-4b8a-86a4-89c9f3261b12&password=password" -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd' -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api/v2.1/upload-links/

**Sample response**

```
{
    "username": "lian@lian.com",
    "repo_id": "62ca6cf9-dab6-47e5-badc-bab13d9220ce",
    "ctime": "2016-03-04T05:51:34.022",
    "token": "dce40e8594",
    "link": "https://cloud.seafile.com/u/d/dce40e8594/",
    "path": "/bar/"
}
```

**Errors**

* 400 path/repo_id invalid
* 403 Permission denied.
* 500 Internal Server Error

## Delete Upload Link

**DELETE** https://cloud.seafile.com/api/v2.1/upload-links/{token}/

**Sample request**

    curl -X DELETE -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd' "https://cloud.seafile.com/api/v2.1/upload-links/0ae587a7d1/"

**Sample response**

    {"success":true}

## Send Upload Link Email

**POST** https://cloud.seafile.com/api2/send-upload-link/

**Request parameters**

* token
* email
* extra_msg (not necessary)

**Sample request**

    curl -d "email=sample@eamil.com,invalid-email&token=4cbd625c5e" -H 'Authorization: Token ef12bf1e66a1aa797a1d6556fdc9ae84f1e9249f' -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api2/send-upload-link/

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
* 400 token/repo_id invalid
* 403 Permission denied.
* 403 Sending shared link failed. Email service is not properly configured, please contact administrator.
* 404 token/library not found

## Upload File

**GET** http://192.168.1.113:8000/api/v2.1/upload-links/{token}/upload/

**Request parameters**

* token

**Sample request**
```
curl -H 'Accept: application/json; indent=4' "http://192.168.1.113:8000/api/v2.1/upload-links/08452f9b1e454ea78e66/upload/"
```

**Sample response**
```
{
    "upload_link": "http://192.168.1.113:8082/upload-api/4b75c020-d175-4d8e-a233-37d98609bef3"
}
```

After get upload link, you can upload file to the shared dir, for more info, please see [Upload File](#upload-file-1).

**Errors**

* 404 Library not found.
* 404 Upload link not found.
* 404 Folder not found.
