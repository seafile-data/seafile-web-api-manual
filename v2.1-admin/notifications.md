# notifications

## Get notifications

### admin get notifications

**GET** https\://cloud.seafile.com/api/v2.1/admin/notifications/

**Request parameters**

* per_page (default 100)
* page (default 1)
* username (name of the user whose notifications you want to get. If no uesrname past, get all notifications of all users)

**Sample request**

```
without username:
curl -H 'Authorization: Token d8c517a01d9ba43a532801fbb3cd07d03b03ea17' "https://cloud.seafile.com/api/v2.1/admin/notifications/"

with username:
curl -H 'Authorization: Token d8c517a01d9ba43a532801fbb3cd07d03b03ea17' "https://cloud.seafile.com/api/v2.1/admin/notifications/?username=myUserName"

```

**Sample response**

```
200 Response(
{
    "count": 2,
    "notification_list": [
        {
            "detail": {
                "share_from_user_avatar_url": "http://127.0.0.1:8000/media/avatars/default.png",
                "repo_id": "7a2b0bbf-babb-4c7c-ac73-02f4ca765cf5",
                "share_from_user_contact_email": "851958789@qq.com",
                "path": "/",
                "share_from_user_name": "851958789",
                "share_from_user_email": "851958789@qq.com",
                "repo_name": "8519testtset"
            },
            "type": "repo_share",
            "id": 8,
            "time": "2019-04-13T03:55:36+00:00"
        },
        {
            "detail": {
                "share_from_user_avatar_url": "http://127.0.0.1:8000/media/avatars/default.png",
                "repo_id": "7a2b0bbf-babb-4c7c-ac73-02f4ca765cf5",
                "share_from_user_contact_email": "851958789@qq.com",
                "path": "/",
                "share_from_user_name": "851958789",
                "share_from_user_email": "851958789@qq.com",
                "repo_name": "8519testtset"
            },
            "type": "repo_share",
            "id": 7,
            "time": "2019-04-12T04:08:58+00:00"
        }
    ]
}
)

```


