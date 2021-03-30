# Avatars

## Update User Avatar

**POST** https://cloud.seafile.com/api/v2.1/user-avatar/

**Request parameters**

* `avatar`: image file
* `avatar_size`: avatar size (default value is 64)

**Sample request**

    curl -H "Authorization: Token cbd7705c06846425ed5c46ae0313d5b098d24154" -F "avatar=@1.jpg" -F "avatar_size=64" https://cloud.seafile.com/api/v2.1/user-avatar/

**Sample response**

    {"avatar_url":"https://cloud.seafile.com/media/avatars/2/4/fa66e6b3a50e2707997ec5eed3eda0/resized/64/a92f89f3e23c7fe9cc708454cdd010df_Y7zJE8v.png"}

**Errors**

* 400 invalid avatar size
* 400 invalid file extension
* 400 file is too big
* 500 Internal Server Error

## Get User Avatar

**GET** https://cloud.seafile.com/api2/avatars/user/{user}/resized/{size}/

**Request parameters**

* user
* size

**Sample request**

    curl -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd' "https://cloud.seafile.com/api2/avatars/user/user@example.com/resized/80/"

**Sample response**

    {
        "url": "http://127.0.0.1:8000/media/avatars/default.png",
        "is_default": true,
        "mtime": 0
    }
