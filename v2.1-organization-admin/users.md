# Organization Admin's API

## Update Organization User Info

**PUT** <https://cloud.seafile.com/api/v2.1/org/{org_id}/admin/users/{email}/>

**Request parameters**

* name, update user's name
* contact_email, update user's contact_email
* is_staff, update user's is_staff status
* quota_total, integer equal or greater than 0, unit is MB. 0 means default limit.

**Sample request**

```
curl -X PUT -d "name=new_name&contact_email=new_name@gmail.com&quota_total=23" -H "Authorization: Token 3f1e23157c3a1fd740e9dc1c5d748929fe319b95" -H 'Accept: application/json; indent=4' http://192.168.1.165/api/v2.1/org/1/admin/users/org@org.com/

```

**Sample response**

```
{
    "name": "new_name",
    "is_active": true,
    "quota": 23000000,
    "id": 34,
    "self_usage": 0,
    "contact_email": "new_name@gmail.com",
    "last_login": "2019-07-18T01:52:07+00:00",
    "email": "org@org.com",
    "ctime": "2019-07-16T03:04:20+00:00"
}

```

**Errors**

* 400 Request parameter incorrect.
* 403 Permission denied.
* 404 Organization not found.
* 404 User not found.
* 500 Internal Server Error.


