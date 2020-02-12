# Organizations

The APIs are only available in pro edition.

## Get Organizations

**GET** <http://192.168.1.113:8000/api/v2.1/admin/organizations/>

**Request parameters**

* page (default 1)
* per_page (default 25)

**Sample request**

```
curl -H 'Authorization: Token 5eba8c2f983404e33b140b13a1d050b9a4440e03' -H 'Accept: application/json; charset=utf-8; indent=4 "http://192.168.1.113:8000/api/v2.1/admin/organizations/"

```

**Sample response**

```
{
    "organizations": [
        {
            "org_id": 1,
            "org_name": "lian-org",
            "ctime": "2019-11-14T17:31:50+08:00",
            "org_url_prefix": "org_28v29mmxdohfh6ttx8dk",
            "role": "default",
            "creator_email": "org@org.com",
            "creator_name": "org",
            "creator_contact_email": "org@org.com",
            "quota": 1232000000,
            "quota_usage": 0
        },
        {
            "org_id": 2,
            "org_name": "LIAN-org-2",
            "ctime": "2019-11-15T11:01:25+08:00",
            "org_url_prefix": "org_17fqbp64v9mtjo4xunf6",
            "role": "default",
            "creator_email": "org@org2.com",
            "creator_name": "org",
            "creator_contact_email": "org@org2.com",
            "quota": -2,
            "quota_usage": 0
        }
    ],
    "total_count": 2
}

```

**Errors**

* 403 Feature is not enabled.

## Search Organization

**GET** <http://127.0.0.1:8000/api/v2.1/admin/search-organization/>

**Request parameters**

* query

**Sample request**

```
curl -H 'Authorization: Token 5eba8c2f983404e33b140b13a1d050b9a4440e03' -H 'Accept: application/json; charset=utf-8; indent=4 "http://127.0.0.1:8000/api/v2.1/admin/search-organization/?query=lian"

```

**Sample response**

```
{
    "organization_list": [
        {
            "org_id": 1,
            "org_name": "lian-org",
            "ctime": "2019-11-14T17:31:50+08:00",
            "org_url_prefix": "org_28v29mmxdohfh6ttx8dk",
            "role": "default",
            "creator_email": "org@org.com",
            "creator_name": "org",
            "creator_contact_email": "org@org.com",
            "quota": 1232000000,
            "quota_usage": 0
        },
        {
            "org_id": 2,
            "org_name": "LIAN-org-2",
            "ctime": "2019-11-15T11:01:25+08:00",
            "org_url_prefix": "org_17fqbp64v9mtjo4xunf6",
            "role": "default",
            "creator_email": "org@org2.com",
            "creator_name": "org",
            "creator_contact_email": "org@org2.com",
            "quota": -2,
            "quota_usage": 0
        }
    ]
}

```

**Errors**

* 403 Feature is not enabled.

## Add Organization

**POST** <https://cloud.seafile.com/api2/organization/>

**Request parameters**

* username
* password
* org_name
* prefix
* quota
* member_limit

**Sample request**

```
curl -v -X POST -d "username=example@example.com&password=example&org_name=example&prefix=example&quota=100&member_limit=10" -H "Authorization: Token ccdff90e4d1efe76b2b3d91c06b027a5cff189d4" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api2/organization/

```

**Sample response**

```
{
    "org_name": "example",
    "ctime": "2019-05-23T08:30:03+00:00",
    "creator_name": "example",
    "creator_email": "example@example.com",
    "org_id": 2,
    "creator_contact_email": "example@example.com",
    "org_url_prefix": "example"
}

```

**Errors**

* 400 Missing argument
* 400 Email is not valid
* 400 Quota is not valid
* 400 URL prefix can only be letters(a-z), numbers, and the underscore character
* 400 A user with this email already exists
* 400 An organization with this prefix already exists
* 403 Feature is not enabled.

## Get Organization Info

**GET** <http://192.168.1.113:8000/api/v2.1/admin/organizations/{org_id}/>

**Request parameters**

* org_id

**Sample request**

```
curl -H 'Authorization: Token 2bac21cab9eb0c4baac10d1e6fc3cf590f0dcf17' -H 'Accept: application/json; charset=utf-8; indent=4' "http://192.168.1.113:8000/api/v2.1/admin/organizations/3/"

```

**Sample response**

```
{
    "org_name": "org",
    "quota_usage": 1059777,
    "ctime": "2018-08-09T12:48:56+08:00",
    "creator_name": "org-admin-user",
    "max_user_number": 1232,
    "creator_email": "org@org.com",
    "org_id": 3,
    "quota": -2,
    "creator_contact_email": "org@org.com",
    "org_url_prefix": "org_l0l4xd"
}

```

**Errors**

* 400 org_id invalid.
* 403 Feature is not enabled.
* 404 Organization not found.

## Update Organization Info

**PUT** <http://192.168.1.113:8000/api/v2.1/admin/organizations/{org_id}/>

**Request parameters**

* org_id
* org_name
* max_user_number
* quota

**Sample request**

```
curl -X PUT -d "org_name=new_org_name&max_user_number=321&quota=4565" -H 'Authorization: Token 2bac21cab9eb0c4baac10d1e6fc3cf590f0dcf17' -H 'Accept: application/json; charset=utf-8; indent=4' "http://192.168.1.113:8000/api/v2.1/admin/organizations/3/"

```

**Sample response**

```
{
    "org_name": "new_org_name",
    "quota_usage": 1059777,
    "ctime": "2018-08-09T12:48:56+08:00",
    "creator_name": "org-admin-user",
    "max_user_number": 321,
    "creator_email": "org@org.com",
    "org_id": 3,
    "quota": 4565000000,
    "creator_contact_email": "org@org.com",
    "org_url_prefix": "org_l0l4xd"
}

```

**Errors**

* 400 org_id/max_user_number/quota invalid.
* 403 Feature is not enabled.
* 404 Organization not found.

## Delete Organization

**DELETE** <http://192.168.1.113:8000/api/v2.1/admin/organizations/{org_id}/>

**Request parameters**

* org_id

**Sample request**

```
curl -X DELETE  -H 'Authorization: Token 2bac21cab9eb0c4baac10d1e6fc3cf590f0dcf17' -H 'Accept: application/json; charset=utf-8; indent=4' "http://192.168.1.113:8000/api/v2.1/admin/organizations/3/"

```

**Sample response**

```
{
    "success": true
}

```

**Errors**

* 400 org_id invalid.
* 403 Feature is not enabled.
* 404 Organization not found.

## Get Organization Users

This api is only supported in pro edition (since 6.3.10).

**GET** <http://192.168.1.113:8000/api/v2.1/admin/organizations/1/users/>

**Request parameters**

* org_id

**Sample request**

```
curl -H 'Authorization: Token 5eba8c2f983404e33b140b13a1d050b9a4440e03' -H 'Accept: application/json; charset=utf-8; indent=4' "http://192.168.1.113:8000/api/v2.1/admin/organizations/1/users/"

```

**Sample response**

```
{
    "users": [
        {
            "quota_usage": 0,
            "name": "lian-org",
            "org_id": 1,
            "contact_email": "lian@seafile.com",
            "active": true,
            "quota_total": 4565000000,
            "email": "lian@seafile.com"
        },
        {
            "quota_usage": 1059777,
            "name": "org-admin-user",
            "org_id": 1,
            "contact_email": "org@org.com",
            "active": true,
            "quota_total": 4565000000,
            "email": "org@org.com"
        }
    ]
}

```

**Errors**

* 400 org_id invalid.

## Add Organization User

This api is only supported in pro edition (since 6.0.9).

**POST** <https://cloud.seafile.com/api/v2.1/admin/organizations/{org_id}/users/>

**Request parameters**

* org_id
* email
* password

**Sample request**
    curl -d "username=1@org-3.com&password=1&org_name=org-3&prefix=org-3"a=100&member_limit=10" -H "Authorization: Token 3f1e23157c3a1fd740e9dc1c5d748929fe319b95" -H 'Accept: application/json; indent=4' <http://192.168.1.165/api2/organization/>

**Sample response**

```
{
    "quota_usage": 0,
    "name": "6",
    "org_id": 1,
    "contact_email": "6@org.com",
    "active": true,
    "quota_total": -1,
    "email": "6@org.com"
}

```

**Errors**

* 400 org_id invalid.
* 400 email invalid.
* 400 password invalid.
* 400 User already exists.
* 403 The number of users exceeds the limit.
* 403 Failed. You can only invite %d members.
* 404 Organization not found.

## Get Organization User Info

**GET** <https://cloud.seafile.com/api/v2.1/admin/organizations/{org_id}/users/{email}/>

**Request parameters**

* org_id
* email

**Sample request**

```
curl -H "Authorization: Token 3f1e23157c3a1fd740e9dc1c5d748929fe319b95" -H 'Accept: application/json; indent=4' http://192.168.1.165/api/v2.1/admin/organizations/1/users/6@org.com/

```

**Sample response**

```
{
    "quota_usage": 0,
    "name": "6",
    "org_id": 1,
    "contact_email": "6@org.com",
    "active": true,
    "quota_total": -1,
    "email": "6@org.com"
}

```

**Errors**

* 400 org_id invalid.
* 400 User is not member of organization.
* 404 Organization not found.
* 404 User not found.

## Updage Organization User Info

**PUT** <https://cloud.seafile.com/api/v2.1/admin/organizations/{org_id}/users/{email}/>

**Request parameters**

* org_id
* email
* active, `true` or `false`
* name
* contact_email
* quota_total, integer greater than 0, unit is MB.

**Sample request**

```
curl -X PUT -d "active=false&name=name-of-6&contact_email=6-contact@email.com&quota_total=23" -H "Authorization: Token 3f1e23157c3a1fd740e9dc1c5d748929fe319b95" -H 'Accept: application/json; indent=4' http://192.168.1.165/api/v2.1/admin/organizations/1/users/6@org.com/

```

**Sample response**

```
{
    "quota_usage": 0,
    "name": "name-of-6",
    "org_id": 1,
    "contact_email": "6-contact@email.com",
    "active": false,
    "quota_total": 23,
    "email": "6@org.com"
}

```

**Errors**

* 400 org_id invalid.
* 400 active invalid, should be 'true' or 'false'.
* 400 Failed to set quota.
* 404 Organization not found.
* 404 User not found.

## Delete Organization User

**DELETE** <https://cloud.seafile.com/api/v2.1/admin/organizations/{org_id}/users/{email}/>

**Request parameters**

* org_id
* email

**Sample request**

```
curl -X DELETE -H "Authorization: Token 0eb24ce5db35a31f70171eca2f760f03f59fa09a" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api/v2.1/admin/organizations/160/users/6@org.com/

```

**Sample response**

```
{
    "success": true
}

```

**Errors**

* 400 org_id invalid.
* 403 Failed to delete: is an organization creator.
* 404 Organization not found.
* 404 User not found.


