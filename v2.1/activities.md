# Activities

## Get File Activities

**GET** <https://cloud.seafile.com/api/v2.1/activities/>

**Request parameters**

* page(default 1)
* per_page(default 25)
* avatar_size(default 72)

**Sample request**

```
curl -H 'Authorization:Token 934e6351ab287c276a3970a5c32cb34dcec9b737' -H 'Accept: application/json; indent=4' "https://cloud.seafile.com/api/v2.1/activities/"

```

**Sample response**

```
{
    "events": [
        {
            "commit_id": "56ad4dfa70f79d2c7a8a6e032acda65d824e7946",
            "obj_type": "file",
            "repo_id": "231afed9-9e6c-4314-9247-dfc3ee0ac734",
            "name": "temp.md",
            "author_email": "a@a.com",
            "author_contact_email": "a@a.com",
            "time": "2019-05-14T09:42:48+00:00",
            "author_name": "aaa",
            "avatar_url": "http://127.0.0.1:8000/media/avatars/d/1/0ca8d11301c2f4993ac2279ce4b930/resized/72/03e77af8819c66f25260297dd5e97dc7.png",
            "op_type": "edit",
            "path": "/temp.md",
            "repo_name": "documents"
        },
        {
            "commit_id": "03bb96d2294d125b3823d3e45c3ded9745ed4382",
            "obj_type": "repo",
            "repo_id": "ea37800a-32af-4e68-b21d-b0d5b44e8ab2",
            "name": "",
            "author_email": "a@a.com",
            "author_contact_email": "a@a.com",
            "time": "2019-05-14T09:12:12+00:00",
            "author_name": "aaa",
            "old_repo_name": "\u6d4b\u8bd5\u8d44\u6599\u5e93",
            "avatar_url": "http://127.0.0.1:8000/media/avatars/d/1/0ca8d11301c2f4993ac2279ce4b930/resized/72/03e77af8819c66f25260297dd5e97dc7.png",
            "op_type": "rename",
            "path": "/",
            "repo_name": "\u6d4b\u8bd5\u8d44\u6599\u5e93"
        },
        ...
    ]
}

```

**Sample request for more activities**

```
curl -H 'Authorization:Token 934e6351ab287c276a3970a5c32cb34dcec9b737' "https://cloud.seafile.com/api/v2.1/activities/?page=2"

```

**Sample response for more activities**

```
{
    "events": [
        {
            "commit_id": null,
            "obj_type": "repo",
            "repo_id": "231afed9-9e6c-4314-9247-dfc3ee0ac734",
            "name": "",
            "author_email": "a@a.com",
            "author_contact_email": "a@a.com",
            "time": "2019-05-13T03:11:27+00:00",
            "days": 0,
            "author_name": "aaa",
            "avatar_url": "http://127.0.0.1:8000/media/avatars/d/1/0ca8d11301c2f4993ac2279ce4b930/resized/72/03e77af8819c66f25260297dd5e97dc7.png",
            "op_type": "clean-up-trash",
            "path": "/",
            "repo_name": "documents"
        },
        {
            "commit_id": "0f4293075e2cf2285414814b691d509b6763c9de",
            "obj_type": "dir",
            "repo_id": "231afed9-9e6c-4314-9247-dfc3ee0ac734",
            "name": "\u6d4b\u8bd5-\u6587\u4ef6\u5939",
            "author_email": "a@a.com",
            "author_contact_email": "a@a.com",
            "time": "2019-05-13T02:56:38+00:00",
            "author_name": "aaa",
            "avatar_url": "http://127.0.0.1:8000/media/avatars/d/1/0ca8d11301c2f4993ac2279ce4b930/resized/72/03e77af8819c66f25260297dd5e97dc7.png",
            "op_type": "delete",
            "path": "/\u6d4b\u8bd5-\u6587\u4ef6\u5939",
            "repo_name": "documents"
        },
        ...
    ]
}

```


