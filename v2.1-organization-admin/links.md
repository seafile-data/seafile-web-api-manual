# links

## Get Links

**GET** <https://cloud.seafile.com/api/v2.1/org/admin/links/>

**Sample request**

```
curl -H "Authorization: Token 3f1e23157c3a1fd740e9dc1c5d748929fe319b95" -H 'Accept: application/json; indent=4' http://127.0.0.1:8000/api/v2.1/org/admin/links/
```

**Sample response**

```
{
    "link_list": [
        {
            "id": 20,
            "owner_name": "o2",
            "owner_email": "o2@o2.com",
            "owner_contact_email": "o2@o2.com",
            "created_time": "2019-11-04T07:14:08+00:00",
            "view_count": 0,
            "token": "e367afdcd33444c2912a",
            "name": "/"
        }
    ],
    "page": 1,
    "page_next": false
}
```

## Delete Link

**GET** <https://cloud.seafile.com/api/v2.1/org/admin/links/{token}/>

**Sample request**

```
curl -H "Authorization: Token 3f1e23157c3a1fd740e9dc1c5d748929fe319b95" -H 'Accept: application/json; indent=4' http://127.0.0.1:8000/api/v2.1/org/admin/links/e367afdcd33444c2912a/
```

**Sample response**

```
{
    "success": true
}
```
