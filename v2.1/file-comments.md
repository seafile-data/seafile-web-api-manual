# File Comments

## Get Comment

**GET** <https://cloud.seafile.com/api2/repos/{repo_id}/file/comments/{pk}/>

* rpeo_id
* pk

**Sample request**

```
curl -H "Authorization: Token 05b05e30ee979e333ff33a437988820494fb0afd"  https://cloud.seafile.com/api2/repos/4674c2bb-3702-4dd0-b768-8952db27ac87/file/comments/1/

```

**Sample response**

```
{
    "comment": "welcome",
    "repo_id": "4674c2bb-3702-4dd0-b768-8952db27ac87",
    "item_name": "q",
    "created_at": "2017-10-10T02:42:20+00:00",
    "parent_path": "/",
    "avatar_url": "https://cloud.seafile.com/media/avatars/default.png",
    "user_name": "admin",
    "id": 3,
    "user_email": "admin@admin.com",
    "user_contact_email": "admin@admin.com"
}

```

**Errors**

* 400 Wrong comment id
* 403 Can not access repo

## Delete Comment

**Delete** <https://cloud.seafile.com/api2/repos/{repo_id}/file/comments/{pk}/>

* rpeo_id
* pk

**Sample request**

```
curl -X DELETE -H "Authorization: Token 05b05e30ee979e333ff33a437988820494fb0afd"  https://cloud.seafile.com/api2/repos/4674c2bb-3702-4dd0-b768-8952db27ac87/file/comments/1/

```

**Sample response**

```
None

```

**Errors**

* 400 Wrong comment id
* 403 Can not access repo
* 403 Permission denied

## Update Comment

**PUT** <https://cloud.seafile.com/api2/repos/{repo_id}/file/comments/{pk}/>

**Request parameters:**

* repo_id
* comment_id
* detail
* resolved(true or false)

**Sample request:**

```
curl -X PUT -d "detail=abc&resolved=true" -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' "http://127.0.0.1:8000/api2/repos/dd185436-68bb-44fa-90ff-cd8bb4a04558/file/comments/35/"

```

**Sample response：**

```
{
    "comment": "yes",
    "resolved": true,
    "repo_id": "dd185436-68bb-44fa-90ff-cd8bb4a04558",
    "item_name": "2.md",
    "created_at": "2018-10-10T05:53:40+00:00",
    "detail": "abc",
    "parent_path": "/",
    "avatar_url": "http://127.0.0.1:8000/media/avatars/default.png",
    "user_name": "hello",
    "id": 35,
    "user_email": "hello@hello.com",
    "user_contact_email": "hello@hello.com"
}

```

**Success**

```
Return a file_comment object.

```

**Errors**

* 400 BAD REQUEST, resolved invalid
* 403 FORBIDDEN, Permission denied
* 404 NOT FOUND, FileComment not found
* 500 INTERNAL SERVER ERROR, Internal error

## List Comments

**GET** <https://cloud.seafile.com/api2/repos/{repo_id}/file/comments/?p=/doc/doc>

* rpeo_id
* p

**Sample request**

```
curl -H "Authorization: Token 05b05e30ee979e333ff33a437988820494fb0afd"  https://cloud.seafile.com/api2/repos/4674c2bb-3702-4dd0-b768-8952db27ac87/file/comments/?p=%2Fdoc%2Fdoc

```

**Sample response**

```
{
    "comments": [
        {
            "comment": "word",
            "repo_id": "4674c2bb-3702-4dd0-b768-8952db27ac87",
            "item_name": "doc",
            "created_at": "2017-10-11T02:49:42+00:00",
            "parent_path": "/doc",
            "avatar_url": "https://cloud.seafile.com/media/avatars/default.png",
            "user_name": "admin",
            "id": 7,
            "user_email": "admin@admin.com",
            "user_contact_email": "admin@admin.com"
        },
        {
            "comment": "help",
            "repo_id": "4674c2bb-3702-4dd0-b768-8952db27ac87",
            "item_name": "doc",
            "created_at": "2017-10-11T02:49:44+00:00",
            "parent_path": "/doc",
            "avatar_url": "https://cloud.seafile.com/media/avatars/default.png",
            "user_name": "admin",
            "id": 8,
            "user_email": "admin@admin.com",
            "user_contact_email": "admin@admin.com"
        },
        {
            "comment": "test",
            "repo_id": "4674c2bb-3702-4dd0-b768-8952db27ac87",
            "item_name": "doc",
            "created_at": "2017-10-11T03:32:37+00:00",
            "parent_path": "/doc",
            "avatar_url": "https://cloud.seafile.com/media/avatars/default.png",
            "user_name": "admin",
            "id": 10,
            "user_email": "admin@admin.com",
            "user_contact_email": "admin@admin.com"
        }
    ]
}

```

**Errors**

* 400 Wrong path
* 403 Can not access repo

## Post Comments

**POST** <https://cloud.seafile.com/api2/repos/{repo_id}/file/comments/?p=/doc/doc>

* rpeo_id
* p
* comment

**Sample request**

```
curl -X POST -d "comment=hello" -H "Authorization: Token 05b05e30ee979e333ff33a437988820494fb0afd"  https://cloud.seafile.com/api2/repos/4674c2bb-3702-4dd0-b768-8952db27ac87/file/comments/?p=%2Fdoc%2Fdoc

```

**Sample response**

```
{
    "comment": "hello",
    "repo_id": "4674c2bb-3702-4dd0-b768-8952db27ac87",
    "item_name": "doc",
    "created_at": "2017-10-11T06:43:31+00:00",
    "parent_path": "/doc",
    "avatar_url": "https://cloud.seafile.com/media/avatars/default.png",
    "user_name": "admin",
    "id": 11,
    "user_email": "admin@admin.com",
    "user_contact_email": "admin@admin.com"
}

```

**Errors**

* 400 Wrong path
* 400 Comment can not be empty
* 403 Can not access repo
* 404 File not found

## Get Number of Comments

**GET** <https://cloud.seafile.com/api2/repos/{repo_id}/file/comments/counts/?p=/doc>

* `repo_id`
* `p`, if represents a folder, this api will return comment count of all files in this folder. If represents a file, only return comment count of this file.

**Sample request**

`get the number of file comment correspoding to the file under the folder`

```
curl -H "Authorization: Token 05b05e30ee979e333ff33a437988820494fb0afd"  -sS 'https://cloud.seafile.com/api2/repos/4674c2bb-3702-4dd0-b768-8952db27ac87/file/comments/counts/?p=/doc'

```

**Sample response**

```
[
    {
        "doc": 3
    },
    {
        "pdfs": 1
    }
]

```

**Sample request**

get comment count of a single file

```
curl -H "Authorization: Token 05b05e30ee979e333ff33a437988820494fb0afd"  -sS 'https://cloud.seafile.com/api2/repos/4674c2bb-3702-4dd0-b768-8952db27ac87/file/comments/counts/?p=/doc/1.txt'

```

```
{
    "1.txt": 2
}

```

**Errors**

* 400 p invalid.
* 403 Permission denied.
* 404 Folder/File not found.
* 500 Internal Server Error


