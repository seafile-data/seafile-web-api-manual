# info

## Get Organization Info

**GET** <https://cloud.seafile.com/api/v2.1/org/admin/info/>

**Sample request**

```
curl -H "Authorization: Token 3f1e23157c3a1fd740e9dc1c5d748929fe319b95" -H 'Accept: application/json; indent=4' http://127.0.0.1:8000/api/v2.1/org/admin/info/
```

**Sample response**

```
{
    "org_id": 11,
    "org_name": "orgo",
    "storage_quota": -2,
    "storage_usage": 0,
    "member_quota": null,
    "member_usage": 2,
    "active_members": 2
}
```