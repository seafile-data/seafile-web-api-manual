# groups

## List Groups

**GET** <https://cloud.seafile.com/api/v2.1/org/{org_id}/admin/groups/>

**Sample request**

```
curl -H "Authorization: Token 3f1e23157c3a1fd740e9dc1c5d748929fe319b95" -H 'Accept: application/json; indent=4' http://127.0.0.1:8000/api/v2.1/org/12/admin/groups/

```

**Sample response**

```
{
    "page_next": false,
    "per_page": 25,
    "page": 1,
    "groups": [
        {
            "ctime": "2019-11-04T08:03:55+00:00",
            "creator_name": "o2",
            "creator_email": "o2@o2.com",
            "group_name": "g1",
            "creator_contact_email": "o2@o2.com",
            "id": 157
        }
    ]
}

```

## Get Group

**GET** <https://cloud.seafile.com/api/v2.1/org/{org_id}/admin/groups/{group_id}/>

**Sample request**

```
curl -H "Authorization: Token 3f1e23157c3a1fd740e9dc1c5d748929fe319b95" -H 'Accept: application/json; indent=4' http://127.0.0.1:8000/api/v2.1/org/12/admin/groups/157/

```

**Sample response**

```
{
    "ctime": "2019-11-04T08:03:55+00:00",
    "creator_name": "o2",
    "creator_email": "o2@o2.com",
    "group_name": "g1",
    "creator_contact_email": "o2@o2.com",
    "id": 157
}

```

## Delete Group

**DELETE** <https://cloud.seafile.com/api/v2.1/org/{org_id}/admin/groups/{group_id}/>

**Sample request**

```
curl -X DELETE -H "Authorization: Token 3f1e23157c3a1fd740e9dc1c5d748929fe319b95" -H 'Accept: application/json; indent=4' http://127.0.0.1:8000/api/v2.1/org/12/admin/groups/158/

```

**Sample response**

```
{
    "success": true
}

```

## List Group Libraries

**GET** <https://cloud.seafile.com/api/v2.1/org/{org_id}/admin/groups/{group_id}/libraries/>

**Sample request**

```
curl -H "Authorization: Token 3f1e23157c3a1fd740e9dc1c5d748929fe319b95" -H 'Accept: application/json; indent=4' http://127.0.0.1:8000/api/v2.1/org/12/admin/groups/157/libraries/

```

**Sample response**

```
{
    "libraries": [
        {
            "repo_id": "57421faf-a8ab-47f5-b5d7-00686f5cd8f2",
            "name": "grepo",
            "permission": "rw",
            "encrypted": false,
            "shared_by_name": "o2",
            "group_id": 157,
            "shared_by": "o2@o2.com",
            "size": 0
        }
    ],
    "group_id": 157,
    "group_name": "g1"
}

```

## Delete Group Library

**DELETE** <https://cloud.seafile.com/api/v2.1/org/{org_id}/admin/groups/{group_id}/libraries/{repo_id}/>

**Sample request**

```
curl -H "Authorization: Token 3f1e23157c3a1fd740e9dc1c5d748929fe319b95" -H 'Accept: application/json; indent=4' http://127.0.0.1:8000/api/v2.1/org/12/admin/groups/157/libraries/57421faf-a8ab-47f5-b5d7-00686f5cd8f2/

```

**Sample response**

```
{
    "success": true
}

```

## List Group Members

**GET** <https://cloud.seafile.com/api/v2.1/org/{org_id}/admin/groups/{group_id}/members/>

Get all members of a group.

**Sample request**

```
curl -H "Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api/v2.1/org/12/admin/groups/64/members/

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

**POST** <https://cloud.seafile.com/api/v2.1/org/{org_id}/admin/groups/{group_id}/members/>

**Sample request**

```
curl -d "email=1@1.com&email=2@1.com" -H 'Authorization: Token 0eb24ce5db35a31f70171eca2f760f03f59fa09a' https://cloud.seafile.com/api/v2.1/org/12/admin/groups/65/members/

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

## Delete Group Member

**DELETE** <https://cloud.seafile.com/api/v2.1/org/{org_id}/admin/groups/{group_id}/members/{email}/>

**Sample request**

```
curl -X DELETE -H 'Authorization: Token 444d2bbf1fc78ffbeedc4704c9f41e32d926ac94' https://cloud.seafile.com/api/v2.1/12/admin/groups/64/members/foo@foo.com/

```

**Sample response**

```
{"success":true}

```

## Update Group Member Role

**PUT** <https://cloud.seafile.com/api/v2.1/org/s{org_id}/admin/groups/{group_id}/members/{email}>

**Sample request**

```
curl -X PUT -d "is_admin=true" -H 'Authorization: Token 0eb24ce5db35a31f70171eca2f760f03f59fa09a' https://cloud.seafile.com/api/v2.1/12/admin/groups/65/members/3@1.com/

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


