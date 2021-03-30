# User Activities

## Get One User's Activities

**GET** http\://192.168.1.113:8000/api/v2.1/admin/user-activities/

**Request parameters**

* user, user's email.
* page, default value is 1.
* per_page, default value is 25.
* avatar_size, default value is 72.

**Sample request**

```
curl -H 'Authorization: Token d6e1942800107cf682e29b28bd3ec0a92352aae6' -H 'Accept: application/json; charset=utf-8; indent=4' "http://192.168.1.113:8000/api/v2.1/admin/user-activities/?user=lian@lian.com"

```

**Sample response**

```
{
    "events": [
        {
            "commit_id": "110d26aeb4b3f492c51270b6c1dda115138a46ac",
            "obj_type": "file",
            "repo_id": "d4f596ed-09ea-4ac6-8d59-12acbd089097",
            "name": "asynchronous-test.py",
            "author_email": "lian@lian.com",
            "author_contact_email": "lian-contact@email.com",
            "time": "2019-01-05T15:34:01+08:00",
            "author_name": "name of lian sd",
            "avatar_url": "http://192.168.1.113:8000/media/avatars/0/1/a72299021077701e7c522c46fdaa87/resized/72/f1624528379862140839578963eb24f2.png",
            "op_type": "delete",
            "path": "/asynchronous-test.py",
            "repo_name": "lib-of-lian"
        },
        {
            "commit_id": "740cc4ae773fb913a4ef8a413e9e2dc240f0bbe4",
            "obj_type": "file",
            "repo_id": "564dd12c-d804-4ea6-96af-7843e3c56e35",
            "name": "1.md",
            "author_email": "lian@lian.com",
            "author_contact_email": "lian-contact@email.com",
            "time": "2018-09-20T14:58:55+08:00",
            "author_name": "name of lian sd",
            "avatar_url": "http://192.168.1.113:8000/media/avatars/0/1/a72299021077701e7c522c46fdaa87/resized/72/f1624528379862140839578963eb24f2.png",
            "op_type": "edit",
            "path": "/1.md",
            "repo_name": "chain111"
        },
        ...
    ]
}

```

**Errors**

* 404 Events not enabled, user not found.
* 400 user invalid.
* 500 Internal Server Error.




