# Accounts

## List All Users' Info

**GET** <https://cloud.seafile.com/api/v2.1/admin/users/>

**Request parameters**

* page: current page.
* per_page

**Sample request**

```
curl -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/admin/users/?page=1&per_page=2"

```

**Sample response**

```
{
	"available_roles":[
    	"default",
        "can_generate_upload_link_false",
        "guest"
    ],
    "data": [
        {
            "login_id": "",
            "quota_usage": 4509,
            "last_login": "2019-08-12T01:31:49.873",
            "name": "851958789",
            "create_time": "2019-06-26T03:42:45+00:00",
            "is_active": true,
            "is_staff": true,
            "contact_email": "",
            "reference_id": "",
            "department": "",
            "quota_total": -2,
            "role": "default",
            "email": "851958789@qq.com"
        },
        {
            "login_id": "",
            "quota_usage": 319340737,
            "last_login": "2019-08-09T07:00:25.548",
            "name": "123",
            "create_time": "2019-06-26T06:06:59+00:00",
            "is_active": true,
            "is_staff": true,
            "contact_email": "",
            "reference_id": "",
            "department": "",
            "quota_total": -2,
            "role": "can_generate_upload_link_false",
            "email": "123@123.com"
        }
    ],
    "paeg_info": {
        "current_page": 1,
        "has_next_page": true
    }
}

```

## Search User

**GET** [https://cloud.seafile.com/api/v2.1/admin/search-user/](https://cloud.seafile.com/api/v2.1/admin/users/)

**Request parameters**

* query

**Sample request**

```
curl -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/admin/search-user/?query=lian"

```

**Sample response**

```
{
    "user_list": [
        {
            "email": "foo@foo.com",
            "name": "name-of-foo",
            "contact_email": "foo@foo.com",
            "is_staff": true,
            "is_active": true,
            "source": "db",
            "quota_usage": 0,
            "quota_total": -2,
            "create_time": "2019-11-13T17:33:15+08:00",
            "last_login": "",
            "role": "default",
            "institution": "test-institution"
        },
        {
            "email": "leosirius@seafile.ren",
            "name": "leosirius",
            "contact_email": "leosirius@seafile.ren",
            "is_staff": false,
            "is_active": true,
            "source": "ldapimport",
            "quota_usage": 0,
            "quota_total": -2,
            "create_time": "1970-01-01T08:00:00+08:00",
            "last_login": "",
            "role": "default",
            "institution": ""
        }
    ]
}

```

## Get a User's Info

**GET** <https://cloud.seafile.com/api/v2.1/admin/users/{email}/>

**Sample request**

```
curl -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/admin/users/foo@foo.com"

```

**Sample response**

```
{
    "login_id": "2131",
    "quota_usage": 4509,
    "last_login": "2019-08-26T09:24:39.448",
    "name": "8519858789",
    "has_default_device": false,
    "create_time": "2019-06-26T03:42:45+00:00",
    "is_active": true,
    "is_force_2fa": false,
    "is_staff": true,
    "contact_email": "is.li.xiaoyi@qqq.com",
    "reference_id": "bb",
    "department": "",
    "quota_total": 12121212000000,
    "role": "default",
    "email": "foo@foo.com"
}

```

## Update User Info

**PUT** <https://cloud.seafile.com/api/v2.1/admin/users/{email}/>

**Request parameters**

* password
* is_staff, true or false
* is_active, true or false
* role	
* name
* login_id
* contact_email
* reference_id
* department
* quota_total, unit is MB

**Sample request**

```
curl -X PUT -d "quota_total=1" -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/admin/users/foo@foo.com/"

```

**Sampple response**

```
{
    "login_id": "",
    "quota_usage": 22022841,
    "last_login": "2019-08-12T06:46:50.442",
    "name": "foo",
    "create_time": "2019-06-28T06:24:12+00:00",
    "is_active": true,
    "is_staff": true,
    "contact_email": "",
    "reference_id": "",
    "department": "",
    "quota_total": 1000000,
    "role": "can_generate_upload_link_false",
    "email": "foo@foo.com",
    "has_default_device": true,
    "is_force_2fa": true,
}

```

## Add User

**POST** <https://cloud.seafile.com/api/v2.1/admin/users/>

**Request parameters**

* email, required.
* password
* is_staff, true or false
* is_active, true or false
* role
* name
* login_id
* contact_email
* reference_id
* department
* quota_total, unit is MB

**Sample request**

```
curl -X POST -d "email=aaabbb@aaabbb.com&password=aaabbb" -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/admin/users/"

```

**Sample response**

```
{
    "login_id": "",
    "quota_usage": 0,
    "last_login": "",
    "name": "aaabbb",
    "create_time": "2019-08-14T10:09:41+00:00",
    "is_active": false,
    "is_staff": false,
    "contact_email": "",
    "reference_id": "",
    "department": "",
    "quota_total": -2,
    "role": "",
    "email": "aaabbb@aaabbb.com"
}

```

## Delete User

**DELETE** <https://cloud.seafile.com/api/v2.1/admin/users/{email}/>

**Sample request**

```
curl -X DELETE -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/admin/users/foo@foo.com/"

```

**Sample response**

```
{success: true}

```

## Migrate Account

**POST** <https://cloud.seafile.com/api2/accounts/{email}/>

**Request parameters**

* op
* to_user this user must exist

**Sample request**

```
curl -v -d "op=migrate&to_user=user2@mail.com" -H "Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api2/accounts/user@mail.com/

```

**Sample response**

```
...
< HTTP/1.0 200 OK
...

"success"

```

**Success**

```
Response code 200(OK) is returned.

```

**Errors**

* 400 Bad Request, arguments are missing or invalid
* 403 Permission error, only administrator can perform this action

## List Accounts(Deprecated)

**GET** <https://cloud.seafile.com/api2/accounts/>

**Request parameters**

* start (default to 0)
* limit (default to 100)
* scope (default None, accepted values: 'LDAP' or 'DB' or 'LDAPImport')

To retrieve all users, just set both `start` and `limit` to `-1`.

If scope parameter is passed then accounts will be searched inside the specific scope, otherwise it will be used the old approach: first LDAP and, if no account is found, DB.

**Sample request**

```
curl -H "Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api2/accounts/

```

**Sample response**

```
[
{
    "email": "foo@foo.com"
},
{
    "email": "bar@bar.com"
}
]

```

**Errors**

* 403 Permission error, only administrator can perform this action

## Get Account Info(Deprecated)

**GET** <https://cloud.seafile.com/api2/accounts/{email}/>

**Request parameters**

**Sample request**

```
curl -v -H "Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api2/accounts/user@mail.com/

```

**Sample response**

```
{
"is_staff": false,
"is_active": true,
"id": 2,
"create_time": 1356061187741686,
"usage": 651463187,
"total": 107374182400,
"email": "user@mail.com"
}

```

**Errors**

* 403 Permission error, only administrator can perform this action

## Create Account(Deprecated)

**PUT** <https://cloud.seafile.com/api2/accounts/{email}/>

**Request parameters**

* password
* is_staff (defaults to False)
* is_active (defaults to True)

**Sample request**

```
curl -v -X PUT -d "password=123456" -H "Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api2/accounts/newaccount@gmail.com/

```

**Sample response**

```
...
< HTTP/1.0 201 CREATED
< Location: https://cloud.seafile.com/api2/accounts/newaccount@gmail.com/
...

"success"

```

**Success**

```
Response code 201(Created) is returned and the Location header provides shared link.

```

**Errors**

* 403 Permission error, only administrator can perform this action

## Delete Account(Deprecated)

**DELETE** <https://cloud.seafile.com/api2/accounts/{email}/>

**Sample request**

```
curl -v -X DELETE -H "Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api2/accounts/newaccount@gmail.com/

```

**Sample response**

```
"success"

```

**Errors**

* 403 Permission error, only administrator can perform this action


