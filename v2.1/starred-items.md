# Starred Items

## List Starred Items

**GET**  https://cloud.seafile.com/api/v2.1/starred-items/

**Sample request**

```
curl -H "Authorization: Token 076de58233c09f19e7a5179abff14ad55987350f" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api/v2.1/starred-items/

```

**Sample response**

```
{
    "starred_item_list": [
        {
            "repo_encrypted": false,
            "mtime": "2019-02-27T13:52:30+08:00",
            "repo_id": "663d57b8-1602-4d6c-a8e3-1b237ca3a766",
            "obj_name": "spec",
            "path": "/",
            "is_dir": true,
            "user_contact_email": "imwhatiam123@gmail.com",
            "user_name": "lian-name",
            "user_email": "imwhatiam123@gmail.com",
            "repo_name": "spec"
        },
        {
            "repo_encrypted": false,
            "mtime": "2019-02-27T16:24:48+08:00",
            "repo_id": "21b941c2-5411-4372-a514-00b62ab99ef2",
            "obj_name": "My Photos",
            "path": "/My Photos/",
            "is_dir": true,
            "user_contact_email": "imwhatiam123@gmail.com",
            "user_name": "lian-name",
            "user_email": "imwhatiam123@gmail.com",
            "repo_name": "lib-on-dev"
        },
        {
            "repo_encrypted": false,
            "mtime": "2019-02-28T13:48:46+08:00",
            "repo_id": "21b941c2-5411-4372-a514-00b62ab99ef2",
            "obj_name": "test.md",
            "path": "/test.md",
            "is_dir": false,
            "user_contact_email": "imwhatiam123@gmail.com",
            "user_name": "lian-name",
            "user_email": "imwhatiam123@gmail.com",
            "repo_name": "lib-on-dev"
        },
    ]
}

```

**Errors**

* 403 Permission denied.

## Star a Library/Folder/File

**POST** https://cloud.seafile.com/api/v2.1/starred-items/

**Request parameters**


* `repo_id`
* `path`: path of folder/file, `/` stands for star a library.

**Sample request**

```
curl -d "repo_id=21b941c2-5411-4372-a514-00b62ab99ef2&path=/" -H "Authorization: Token 076de58233c09f19e7a5179abff14ad55987350f" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api/v2.1/starred-items/

```

**Sample response**

```
{
    "repo_encrypted": false,
    "mtime": "2019-02-28T13:48:46+08:00",
    "repo_id": "21b941c2-5411-4372-a514-00b62ab99ef2",
    "obj_name": "lib-on-dev",
    "path": "/",
    "is_dir": true,
    "user_contact_email": "imwhatiam123@gmail.com",
    "user_name": "lian-name",
    "user_email": "imwhatiam123@gmail.com",
    "repo_name": "lib-on-dev"
}

```



**Errors**

* 400 repo_id/path invalid.
* 403 Permission denied.
* 404 Library/item not found.
* 500 Internal Server Error

## Unstar a Library/Folder/File

**DELETE** https://cloud.seafile.com/api/v2.1/starred-items/?repo_id=21b941c2-5411-4372-a514-00b62ab99ef2&path=/test.md

**Request parameters**

* `repo_id`
* `path`: path of folder/file, `/` stands for unstar a library.

**Sample request**

```
curl -X DELETE -H "Authorization: Token 076de58233c09f19e7a5179abff14ad55987350f" -H 'Accept: application/json; indent=4' "https://cloud.seafile.com/api/v2.1/starred-items/?repo_id=21b941c2-5411-4372-a514-00b62ab99ef2&path=/test.md"

```

**Sample response**

```
{
    "success": true
}

```


**Errors**

* 400 repo_id/path invalid.
* 403 Permission denied.
* 500 Internal Server Error

