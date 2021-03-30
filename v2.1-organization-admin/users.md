# users

## List Users

**GET** /api/v2.1/org/{org_id}/admin/users/

**Sample request**

```
curl -H "Authorization: Token 3f1e23157c3a1fd740e9dc1c5d748929fe319b95" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api/v2.1/org/12/admin/users/

```

**Sample response**

```
{
    "per_page": 100,
    "user_list": [
        {
            "quota_usage": 0,
            "name": "o2",
            "contact_email": "o2@o2.com",
            "is_active": true,
            "quota": -2,
            "id": 178,
            "self_usage": 0,
            "last_login": "2019-11-04T07:23:35+00:00",
            "quota_total": -2,
            "email": "o2@o2.com",
            "ctime": "2019-11-04T07:11:46+00:00"
        }
    ],
    "page_next": false,
    "page": 1
}

```

## Add User

**POST** /api/v2.1/org/{org_id}/admin/users/

**Sample request**

```
curl -X POST -H "Authorization: Token 3f1e23157c3a1fd740e9dc1c5d748929fe319b95" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api/v2.1/org/12/admin/users/

```

**Sample response**

```
{
    "name": "o2b",
    "is_active": true,
    "quota": -2,
    "id": 180,
    "self_usage": 0,
    "contact_email": "o2b@o2b.com",
    "last_login": null,
    "email": "o2b@o2b.com",
    "ctime": "2019-11-04T07:47:51+00:00"
}

```

## Get User

**GET** /api/v2.1/org/{org_id}/admin/users/{email}/

**Sample request**

```
curl -H "Authorization: Token 3f1e23157c3a1fd740e9dc1c5d748929fe319b95" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api/v2.1/org/12/admin/users/o2a@o2a.com/

```

**Sample response**

```
{
    "quota_usage": 0,
    "name": "o2a",
    "avatar_url": "https://cloud.seafile.com/media/avatars/default.png",
    "quota_total": -2,
    "contact_email": "o2a@o2a.com",
    "email": "o2a@o2a.com"
}

```

## Update User

**PUT** /api/v2.1/org/{org_id}/admin/users/{email}/

**Request Parameters**

choose one attribute to update

* name
* contact_email
* quota_total
* is_staff

**Sample request**

```
curl -X PUT -d "name=o2aa" -H "Authorization: Token 3f1e23157c3a1fd740e9dc1c5d748929fe319b95" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api/v2.1/org/12/admin/users/o2a@o2a.com/

```

**Sample response**

```
{
    "quota_usage": 0,
    "name": "o2a",
    "avatar_url": "https://cloud.seafile.com/media/avatars/default.png",
    "quota_total": -2,
    "contact_email": "o2a@o2a.com",
    "email": "o2a@o2a.com"
}

```

## Delete User

**DELETE** /api/v2.1/org/{org_id}/admin/users/{email}/

**Sample request**

```
curl -X DELETE -H "Authorization: Token 3f1e23157c3a1fd740e9dc1c5d748929fe319b95" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api/v2.1/org/12/admin/users/o2a@o2a.com/

```

**Sample response**

```
{
    "success": true
}

```

## Reset User Password

**PUT** /api/v2.1/org/{org_id}/admin/users/{email}/set-password/

**Sample request**

```
curl -X PUT -H "Authorization: Token 3f1e23157c3a1fd740e9dc1c5d748929fe319b95" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api/v2.1/org/12/admin/users/o2a@o2a.com/set-password/

```

**Sample response**

```
{
    "new_password": "PcqK9nwSR0"
}

```

## List User's Libraries

**GET** /api/v2.1/org/{org_id}/admin/users/{email}/repos/

**Sample request**

```
curl -H "Authorization: Token 3f1e23157c3a1fd740e9dc1c5d748929fe319b95" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api/v2.1/org/12/admin/users/o2@o2.com/repos/

```

**Sample response**

```
{
    "repo_list": [
        {
            "status": "normal",
            "owner_name": "o2",
            "permission": "rw",
            "encrypted": false,
            "owner_email": "o2@o2.com",
            "last_modified": "2019-11-04T07:12:31+00:00",
            "size": 0,
            "owner_contact_email": "o2@o2.com",
            "repo_id": "6fdc40bf-4978-4fb5-92bf-0fadbf831bb2",
            "modifier_email": "o2@o2.com",
            "repo_name": "My Library"
        }
    ]
}

```

## List Libraries Shared to a User

**GET** /api/v2.1/org/{org_id}/admin/users/{email}/beshared-repos/

**Sample request**

```
curl -H "Authorization: Token 3f1e23157c3a1fd740e9dc1c5d748929fe319b95" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api/v2.1/org/12/admin/users/o2b@o2b.com/beshared-repos/

```

**Sample response**

```
{
    "repo_list": [
        {
            "status": "normal",
            "owner_name": "o2",
            "permission": "rw",
            "encrypted": false,
            "owner_email": "o2@o2.com",
            "last_modified": "2019-11-04T08:00:54+00:00",
            "size": 0,
            "owner_contact_email": "o2@o2.com",
            "repo_id": "59668537-a225-49ff-a3e1-8eeca1032e9f",
            "modifier_email": "o2@o2.com",
            "repo_name": "22"
        }
    ]
}

```


