# Groups

## Get all groups

**GET** <https://cloud.seafile.com/api/v2.1/admin/groups/?page=1&per_page=100>

Get first page (100 records per page) of groups.

**Sample request**

```
curl -H "Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api/v2.1/admin/groups/?page=1&per_page=100

```

**Sample response**

```
{
    "page_info": {
        "current_page": 1,
        "has_next_page": true
    },
    "groups": [
        {
            "owner": "test@test.com",
            "created_at": "2016-08-01T16:58:14+08:00",
            "id": 1476,
            "name": "test_group"
        },
        {
            "owner": "1@1.com",
            "created_at": "2016-08-02T16:48:14+08:00",
            "id": 1486,
            "name": "group"
        }
        ...
    ]
}

```

**Errors**

* 403 Permission error, only administrator can perform this action

## Search group

**GET** <http://127.0.0.1:8000/api/v2.1/admin/search-group/>

**Request parameters**

* query

**Sample request**

```
curl -H "Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd" -H 'Accept: application/json; indent=4' http://127.0.0.1:8000/api/v2.1/admin/search-group/?query=g

```

**Sample response**

```
{
    "group_list": [
        {
            "id": 1,
            "name": "group of foo",
            "owner": "foo@foo.com",
            "owner_name": "name-of-foo",
            "created_at": "2019-11-15T17:21:18+08:00",
            "quota": -1,
            "parent_group_id": 0
        },
        {
            "id": 2,
            "name": "group 2 of foo",
            "owner": "foo@foo.com",
            "owner_name": "name-of-foo",
            "created_at": "2019-11-15T17:21:27+08:00",
            "quota": -1,
            "parent_group_id": 0
        }
    ]
}

```

**Errors**

* 400, query invalid.
* 403 Permission error, only administrator can perform this action

## Create a new group

**POST** <https://cloud.seafile.com/api/v2.1/admin/groups/>

**Request parameters**

* group_name
* group_owner, email of group owner. If left blank, owner will be admin.

**Sample request**

```
curl -X PUT -d "group_name=123&owner=q1@q1.com" -H "Authorization: Token 4c3fa38f9f2fee40485446afdee7a23749cb6911" -H 'Accept: application/json; charset=utf-8; indent=4' https://cloud.seafile.com/api/v2.1/admin/groups/

```

**Sample response**

```
{
	"owner_name":"q1",
    "name":"321222",
    "created_at":"2019-08-30T05:45:52+00:00",
    "quota":-1,
    "parent_group_id":0,
    "owner":"q1@q1.com",
    "id":414
}

```

## Delete a Group

**DELETE** <https://cloud.seafile.com/api/v2.1/admin/groups/{group_id}/>

**Sample request**

```
curl -X DELETE -H 'Authorization: Token 444d2bbf1fc78ffbeedc4704c9f41e32d926ac94' https://cloud.seafile.com/api/v2.1/admin/groups/1486/

```

**Sample response**

```
{"success":true}

```

**Errors**

* 403 Permission error, only administrator can perform this action

## Transfer a Group

**PUT** <https://cloud.seafile.com/api/v2.1/admin/groups/{group_id}/>

**Sample request**

```
curl -X PUT -d "new_owner=1@1.com" -H 'Authorization: Token 444d2bbf1fc78ffbeedc4704c9f41e32d926ac94' https://cloud.seafile.com/api/v2.1/admin/groups/1528/

```

**Sample response**

```
{
    "owner": "1@1.com",
    "created_at": "2016-08-04T17:34:05+08:00",
    "id": 1528,
    "name": "test_group"
}

```

**Errors**

* 403 Permission error, only administrator can perform this action
* 404 User not found.

## List Group Members

**GET** <https://cloud.seafile.com/api/v2.1/admin/groups/{group_id}/members/>

Get all members of a group.

**Sample request**

```
curl -H "Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api/v2.1/admin/groups/64/members/

```

**Sample response**

```
[
    {
        "login_id":"",
        "avatar_url":"https://cloud.seafile.com/media/avatars/0/1/a72299021077701e7c522c46fdaa87/resized/80/6ad30837f69ea7ef234dc272fb15e9e9.png",
        "contact_email":"lian@lian.com",
        "name":"name of lian",
        "is_admin":true,
        "role":"Owner",
        "group_id":65,
        "email":"lian@lian.com"
    },
    {
        "login_id":"",
        "avatar_url":"https://cloud.seafile.com/media/avatars/default.png",
        "contact_email":"1@1.com",
        "name":"123",
        "is_admin":false,
        "role":"Member",
        "group_id":65,
        "email":"1@1.com"
    }
]

```

**Errors**

* 403 Permission error, only administrator can perform this action
* 404 Group not found.

## Add Group Member

Available for Seafile v6.0.8+

**POST** <https://cloud.seafile.com/api/v2.1/admin/groups/{group_id}/members/>

**Sample request**

```
curl -d "email=1@1.com&email=2@1.com" -H 'Authorization: Token 0eb24ce5db35a31f70171eca2f760f03f59fa09a' https://cloud.seafile.com/api/v2.1/admin/groups/65/members/

```

**Sample response**

```
{
    "failed":[
        {
            "email":"2@1.com","error_msg":"User 2@1.com is already a group member."
        }
    ],
    "success":[
        {
            "login_id":"",
            "avatar_url":"https://cloud.seafile.com/media/avatars/default.png",
            "contact_email":"8@1.com",
            "name":"name of 8",
            "is_admin":0,
            "role":"Member",
            "group_id":65,
            "email":"8@1.com"
        }
    ]
}

```

**Errors**

* 400 email invalid.
* 404 Group not found.

## Delete Group Member

Available for Seafile v6.0.0+

**DELETE** <https://cloud.seafile.com/api/v2.1/admin/groups/{group_id}/members/{email}/>

**Sample request**

```
curl -X DELETE -H 'Authorization: Token 444d2bbf1fc78ffbeedc4704c9f41e32d926ac94' https://cloud.seafile.com/api/v2.1/admin/groups/64/members/foo@foo.com/

```

**Sample response**

```
{"success":true}

```

**Errors**

* 403 Permission error, only administrator can perform this action
* 403 foo@foo.com is group owner, can not be removed.
* 404 Group not found.
* 500 Internal Server Error

## Update Group Member Role

Available for Seafile v6.0.8+

### Set a group member as admin

**PUT** <https://cloud.seafile.com/api/v2.1/admin/groups/{group_id}/members/{email}>

**Sample request**

```
curl -X PUT -d "is_admin=true" -H 'Authorization: Token 0eb24ce5db35a31f70171eca2f760f03f59fa09a' https://cloud.seafile.com/api/v2.1/admin/groups/65/members/3@1.com/

```

**Sample response**

```
{
    "login_id":"",
    "avatar_url":"https://cloud.seafile.com/media/avatars/default.png",
    "contact_email":"3@1.com",
    "name":"update name of 3",
    "is_admin":1,
    "role":"Admin",
    "group_id":65,
    "email":"3@1.com"
}

```

**Errors**

* 400 email invalid.
* 400 is_admin invalid.
* 404 Group/User not found.

### Unset a group member as admin

**PUT** <https://cloud.seafile.com/api/v2.1/admin/groups/{group_id}/members/{email}>

**Sample request**

```
curl -X PUT -d "is_admin=false" -H 'Authorization: Token 0eb24ce5db35a31f70171eca2f760f03f59fa09a' https://cloud.seafile.com/api/v2.1/admin/groups/65/members/3@1.com/

```

**Sample response**

```
{
    "login_id":"",
    "avatar_url":"https://cloud.seafile.com/media/avatars/default.png",
    "contact_email":"3@1.com",
    "name":"update name of 3",
    "is_admin":0,
    "role":"Member",
    "group_id":65,
    "email":"3@1.com"
}

```

**Errors**

* 400 email invalid.
* 400 is_admin invalid.
* 404 Group/User not found.
* 500 Internal Server Error

## List libraries Shared to a Group

Available for Seafile v6.0.0+

**GET** <https://cloud.seafile.com/api/v2.1/admin/groups/{group_id}/libraries/>

Get all libraries of a group.

**Sample request**

```
curl -H "Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api/v2.1/admin/groups/64/libraries/

```

**Sample response**

```
[
    {
        "repo_id":"7460f7ac-a0ff-4585-8906-bb5a57d2e118",
        "name":"My Library",
        "permission":"rw",
        "group_id":65,
        "shared_by":"lian@lian.com",
        "size":97662
    }
]

```

**Errors**

* 403 Permission error, only administrator can perform this action
* 404 Group not found.

## Remove a Library from Group

Available for Seafile v6.0.0+

**DELETE** <https://cloud.seafile.com/api/v2.1/admin/groups/{group_id}/libraries/{repo_id}/>

**Sample request**

```
curl -X DELETE -H 'Authorization: Token 444d2bbf1fc78ffbeedc4704c9f41e32d926ac94' https://cloud.seafile.com/api/v2.1/admin/groups/64/libraries/7460f7ac-a0ff-4585-8906-bb5a57d2e118/

```

**Sample response**

```
{"success":true}

```

**Errors**

* 403 Permission error, only administrator can perform this action
* 404 Library/Group not found.
* 500 Internal Server Error


