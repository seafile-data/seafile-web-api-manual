# Departments

Departments are special groups.

## List top level departments

**GET** http://192.168.1.113:8000/api/v2.1/admin/address-book/groups/

**Sample request**

```
curl -H 'Authorization: Token 2bac21cab9eb0c4baac10d1e6fc3cf590f0dcf17' -H 'Accept: application/json; charset=utf-8; indent=4' http://192.168.1.113:8000/api/v2.1/admin/address-book/groups/
```

**Sample response**

```
{
  "data": [
    {
      "name": "test-xxx",
      "created_at": "2018-06-05T10:45:45+08:00",
      "quota": -2,
      "parent_group_id": -1,
      "owner": "system admin",
      "id": 176
    },
    {
      "name": "\u7814\u53d1\u90e8",
      "created_at": "2018-05-24T23:30:07+08:00",
      "quota": -2,
      "parent_group_id": -1,
      "owner": "system admin",
      "id": 172
    },
    {
      "name": "test1",
      "created_at": "2018-05-15T11:57:16+08:00",
      "quota": 1000000000,
      "parent_group_id": -1,
      "owner": "system admin",
      "id": 168
    }
  ]
}
```

## List groups and members in a department

**GET** http://192.168.1.113:8000/api/v2.1/admin/address-book/groups/{group_id}/?return_ancestors=true

**Request parameters**

* return_ancestors (true or false, defaults to false)

**Sample request**

```
curl -H 'Authorization: Token 2bac21cab9eb0c4baac10d1e6fc3cf590f0dcf17' -H 'Accept: application/json; charset=utf-8; indent=4' http://192.168.1.113:8000/api/v2.1/admin/address-book/groups/172/?return_ancestors=true
```

**Sample response**

```
{
  "id": 172
  "name": "\u7814\u53d1\u90e8",
  "created_at": "2018-05-24T23:30:07+08:00",
  "quota": -2,
  "members": [
    {
      "login_id": "",
      "avatar_url": "http://192.168.1.113:8000/image-view\/avatars\/9\/3\/45638f87b4642ce4820dbe65e3438d\/resized\/80\/dfad850ea93d405f6e6cf51a9f1e36bf_GrrNVeZ.png",
      "contact_email": "xxx@gmail.com",
      "name": "xxx",
      "is_admin": true,
      "role": "Admin",
      "group_id": 172,
      "email": "xxx@gmail.com"
    }
  ],
  "parent_group_id": -1,
  "groups": [
    {
      "name": "\u5ba2\u6237\u7aef\u7ec4",
      "created_at": "2018-05-24T23:30:32+08:00",
      "quota": 5000000000,
      "parent_group_id": 172,
      "owner": "system admin",
      "id": 173
    },
    {
      "name": "\u670d\u52a1\u5668\u5f00\u53d1\u7ec4",
      "created_at": "2018-05-25T11:55:17+08:00",
      "quota": -2,
      "parent_group_id": 172,
      "owner": "system admin",
      "id": 174
    },
  ],
  "owner": "system admin",
  "ancestor_groups": [

  ],
}
```

## Add a department

**POST** http://192.168.1.113:8000/api/v2.1/admin/address-book/groups/

**Request parameters**

* `group_name`
* `group_owner`	(defaults to '')
* `parent_group` (Positive Integer, defaults to -1)

**Sample request**

```
curl -v -d "group_name=xxx&group_owner=system admin" -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd' -H 'Accept: application/json; charset=utf-8; indent=4' http://192.168.1.113:8000/api/v2.1/admin/address-book/groups/
```

**Sample response**

```
{
  "name": "xxx",
  "created_at": "2018-06-05T10:45:45+08:00",
  "quota": -2,
  "parent_group_id": -1,
  "owner": "system admin",
  "id": 176
}
```

**Errors**

* 400 `group_name` or `parent_group` invalid

## Delete a department

**DELETE** http://192.168.1.113:8000/api/v2.1/admin/address-book/groups/{group_id}/

**Sample request**

```
curl -X DELETE -v  -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd' -H 'Accept: application/json; charset=utf-8; indent=4' http://192.168.1.113:8000/api/v2.1/admin/address-book/groups/176/
```

**Sample response**

```
{"success":true}
```

## Set Department Quota

Available for Seafile v6.3

**PUT** https://cloud.seafile.com/api/v2.1/admin/groups/{group_id}/

**Request parameters**

* `quota`: integer, `-2` means no quota limit.

**Sample request**

    curl -X PUT -d "quota=100" -H 'Authorization: Token 444d2bbf1fc78ffbeedc4704c9f41e32d926ac94' https://cloud.seafile.com/api/v2.1/admin/groups/1528/

**Sample response**

```
{
    "owner": "1@1.com",
    "created_at": "2016-08-04T17:34:05+08:00",
    "id": 1528,
    "name": "test_group",
    "quota": 100
}
```

**Errors**

* 400 Quota invalid.
* 403 Permission error, only administrator can perform this action
