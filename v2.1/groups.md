# Groups

## List Groups

**GET** https://cloud.seafile.com/api2/groups/


**Sample request**

    curl -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd' "https://cloud.seafile.com/api2/groups/"

**Sample response**

    {
        "replynum": 0,
        "groups": [
            {
                "ctime": 1398134171327948,
                "creator": "user@example.com",
                "msgnum": 0,
                "mtime": 1398231100,
                "id": 1,
                "name": "lian"
            },
            {
                "ctime": 1398236081042441,
                "creator": "user@example.com",
                "msgnum": 0,
                "mtime": 0,
                "id": 2,
                "name": "123"
            }
        ]
    }

## Add a Group

**POST** https://cloud.seafile.com/api/v2.1/groups/

**Request parameters**

* name (name of new group)

**Sample request**

```
curl -d "name=new_group_name" -H 'Authorization: Token 444d2bbf1fc78ffbeedc4704c9f41e32d926ac94' https://cloud.seafile.com/api/v2.1/groups/
```

**Sample response**

```
{
    "name": "new_group_name",
    "owner": "lian@lian.com",
    "created_at": "2015-12-17T10:29:57+0800",
    "admins": ["lian@lian.com"],
    "avatar_url": "https://cloud.seafile.com/media/avatars/groups/default.png",
    "id": 773
}
```

## Get Info of a Group

**GET** https://cloud.seafile.com/api/v2.1/groups/772/

**Request parameters**

* avatar_size
* with_repos (0 or 1, if return library info of group. default 0 not return)

**Sample request**

```
curl -H 'Authorization: Token 444d2bbf1fc78ffbeedc4704c9f41e32d926ac94' https://cloud.seafile.com/api/v2.1/groups/772/
```

**Sample response**

```
{
    "name": "rename_group_name",
    "owner": "lian@lian.com",
    "created_at": "2015-12-17T10:29:57+0800",
    "admins": ["lian@lian.com"],
    "avatar_url": "https://cloud.seafile.com/media/avatars/groups/default.png",
    "id": 772
}
```

## Rename a Group

**PUT** https://cloud.seafile.com/api/v2.1/groups/772/

**Request parameters**

* name (name of new group)

**Sample request**

```
curl -X PUT -d "name=rename_group_name" -H 'Authorization: Token 444d2bbf1fc78ffbeedc4704c9f41e32d926ac94' https://cloud.seafile.com/api/v2.1/groups/772/
```

**Sample response**

```
{
    "name": "rename_group_name",
    "owner": "lian@lian.com",
    "created_at": "2015-12-17T10:29:57+0800",
    "admins": ["lian@lian.com"],
    "avatar_url": "https://cloud.seafile.com/media/avatars/groups/default.png",
    "id": 772
}
```

## Transfer a Group

**PUT** https://cloud.seafile.com/api/v2.1/groups/772/

**Request parameters**

* owner (new owner of this group, should be an email.)

**Sample request**

```
curl -X PUT -d "owner=new_owner@new_owner.com" -H 'Authorization: Token 444d2bbf1fc78ffbeedc4704c9f41e32d926ac94' https://cloud.seafile.com/api/v2.1/groups/772/
```

**Sample response**

```
{
    "name": "rename_group_name",
    "owner": "new_owner@new_owner.com",
    "created_at": "2015-12-17T10:29:57+0800",
    "admins": ["lian@lian.com", "new_owner@new_owner.com"],
    "avatar_url": "https://cloud.seafile.com/media/avatars/groups/default.png",
    "id": 772
}
```

## Delete a Group

**DELETE** https://cloud.seafile.com/api/v2.1/groups/772/

**Sample request**

```
curl -X DELETE -H 'Authorization: Token 444d2bbf1fc78ffbeedc4704c9f41e32d926ac94' https://cloud.seafile.com/api/v2.1/groups/772/
```

**Sample response**

```
{"success":true}
```

## Quit Group

**DELETE** https://cloud.seafile.com/api/v2.1/groups/770/members/myself@email.com/

**Sample request**

```
curl -X DELETE -H 'Authorization: Token 444d2bbf1fc78ffbeedc4704c9f41e32d926ac94' https://cloud.seafile.com/api/v2.1/groups/770/members/myself@email.com/
```

**Sample response**

```
{"success":true}
```

## List All Group Members

**GET** https://cloud.seafile.com/api/v2.1/groups/770/members/

**Request parameters**

* avatar_size
* is_admin (`true` or `false`, if ONLY return admin members of group. default `false` return all members)

**Sample request**

```
curl -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd' "https://cloud.seafile.com/api/v2.1/groups/770/members/"
```

**Sample response**

```
[
    {
        "login_id": "",
        "name": "nickname-of-lian",
        "avatar_url": "https://cloud.seafile.com/media/avatars/default.png",
        "is_admin": true,
        "contact_email": "lian_contact@email.com",
        "email": "lian@lian.com"
    },
    {
        "login_id": "",
        "name": "1",
        "avatar_url": "https://cloud.seafile.com/media/avatars/default.png",
        "is_admin": false,
        "contact_email": "1@1.com",
        "email": "1@1.com"
    }
]
```

## Add a Group Member

**POST** https://cloud.seafile.com/api/v2.1/groups/770/members/

**Request parameters**

* email

**Sample request**

```
curl -d "email=new-member@email.com" -H 'Authorization: Token 444d2bbf1fc78ffbeedc4704c9f41e32d926ac94' https://cloud.seafile.com/api/v2.1/groups/770/members/
```

**Sample response**

```
{
    "login_id": "",
    "name": "new-member",
    "avatar_url": "https://cloud.seafile.com/media/avatars/default.png",
    "is_admin": false,
    "contact_email": "new-member@email.com",
    "email": "new-member@email.com"
}
```

## Bulk Add Group Members

**POST** https://cloud.seafile.com/api/v2.1/groups/770/members/bulk/

**Request parameters**

* emails

**Sample request**

```
curl -d "emails=new-member-1@email.com,new-member-2@email.com,new-member-3@email.com" -H 'Authorization: Token 444d2bbf1fc78ffbeedc4704c9f41e32d926ac94' https://cloud.seafile.com/api/v2.1/groups/770/members/bulk/
```

**Sample response**

```
{
    "failed":[
        {
            "error_msg": "Invalid email",
            "email": "new-member-3@email.com"
        },
        {
            "error_msg": "Is already group member",
            "email": "new-member-4@email.com"
        }
    "success":[
        {
            "login_id": "",
            "name": "new-member-1",
            "avatar_url": "https://cloud.seafile.com/media/avatars/default.png",
            "is_admin": false,
            "contact_email": "new-member-1@email.com",
            "email": "new-member-1@email.com"
        },
        {
            "login_id": "",
            "name": "new-member-2",
            "avatar_url": "https://cloud.seafile.com/media/avatars/default.png",
            "is_admin": false,
            "contact_email": "new-member-2@email.com",
            "email": "new-member-2@email.com"
        }
    ]
}
```

## Get Info of a Group Member

**GET** https://cloud.seafile.com/api/v2.1/groups/770/members/group-member@email.com/

**Sample request**

```
curl -H 'Authorization: Token 444d2bbf1fc78ffbeedc4704c9f41e32d926ac94' https://cloud.seafile.com/api/v2.1/groups/770/members/group-member@email.com/
```

**Request parameters**

* avatar_size

**Sample response**

```
{
    "login_id": "",
    "name": "group-member",
    "avatar_url": "https://cloud.seafile.com/media/avatars/default.png",
    "is_admin": false,
    "contact_email": "group-member@email.com",
    "email": "group-member@email.com"
}
```

## Set a Group Admin

**PUT** https://cloud.seafile.com/api/v2.1/groups/770/members/group-member@email.com/

**Request parameters**

* is_admin=true

**Sample request**

```
curl -X PUT -d "is_admin=true" -H 'Authorization: Token 444d2bbf1fc78ffbeedc4704c9f41e32d926ac94' https://cloud.seafile.com/api/v2.1/groups/770/members/group-member@email.com/
```

**Sample response**

```
{
    "login_id": "",
    "name": "group-member",
    "avatar_url": "https://cloud.seafile.com/media/avatars/default.png",
    "is_admin": true,
    "contact_email": "group-member@email.com",
    "email": "group-member@email.com"
}
```

## Unset a Group Admin

**PUT** https://cloud.seafile.com/api/v2.1/groups/770/members/group-member@email.com/

**Request parameters**

* is_admin=false

**Sample request**

```
curl -X PUT -d "is_admin=false" -H 'Authorization: Token 444d2bbf1fc78ffbeedc4704c9f41e32d926ac94' https://cloud.seafile.com/api/v2.1/groups/770/members/group-member@email.com/
```

**Sample response**

```
{
    "login_id": "",
    "name": "group-member",
    "avatar_url": "https://cloud.seafile.com/media/avatars/default.png",
    "is_admin": false,
    "contact_email": "group-member@email.com",
    "email": "group-member@email.com"
}
```

## Delete a Group Member

**DELETE** https://cloud.seafile.com/api/v2.1/groups/770/members/group-member@email.com/

**Sample request**

```
curl -X DELETE -H 'Authorization: Token 444d2bbf1fc78ffbeedc4704c9f41e32d926ac94' https://cloud.seafile.com/api/v2.1/groups/770/members/group-member@email.com/
```

**Sample response**

```
{"success":true}
```
