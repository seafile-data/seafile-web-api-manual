# system-admin-api

## info page

### get system info

**GET** <https://cloud.seafile.com/api/v2.1/admin/sysinfo/>

**Sample request**

```
curl -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' https://cloud.seafile.com/api/v2.1/admin/sysinfo/

```

**Sample response**

```
{
    "current_connected_devices_count": 0,
    "license_to": "demo.seafile.top",
    "license_maxusers": 10000,
    "total_storage": 65399305,
    "total_devices_count": 4,
    "users_count": 59,
    "with_license": true,
    "license_mode": "subscription",
    "active_users_count": 59,
    "license_expiration": "2019-09-14",
    "groups_count": 18,
    "multi_tenancy_enabled": true,
    "total_files_count": 35,
    "repos_count": 24,
    "is_pro": true,
    "org_count": 1
}

```

**Errors**

* 403 Permission denied.
* 500 Internal Server Error.

### upload license

**POST** <https://cloud.seafile.com/api/v2.1/admin/license/>

**Sample request**

```
curl -i -X POST -H "Content-Type: multipart/form-data"  -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' 
-F "license=@seafile-license.txt" https://cloud.seafile.com/api/v2.1/admin/license/

```

**Sample response**

```
{
    license_expiration: "2019-09-14"
    license_maxusers: 10000
    license_mode: "subscription"
    license_to: "demo.seafile.top"
}

```

**Errors**

* 400 Request parameter incorrect.
* 403 Permission denied.
* 500 Internal Server Error.

## web settings

### get web settings info

**GET** <https://cloud.seafile.com/api/v2.1/admin/web-settings/>

**Sample request**

```
curl -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' https://cloud.seafile.com/api/v2.1/admin/web-settings/

```

**Sample response**

```
{
    "DISABLE_SYNC_WITH_ANY_FOLDER": 1,
    "ENABLE_USER_CREATE_ORG_REPO": true,
    "SHARE_LINK_TOKEN_LENGTH": 20,
    "REPO_PASSWORD_MIN_LENGTH": 10,
    "REGISTRATION_SEND_MAIL": 0,
    "SHARE_LINK_PASSWORD_MIN_LENGTH": 8,
    "ENABLE_BRANDING_CSS": false,
    "ENABLE_REPO_HISTORY_SETTING": 0,
    "SERVICE_URL": "http://127.0.0.1:8000",
    "ACTIVATE_AFTER_REGISTRATION": true,
    "ENABLE_ENCRYPTED_LIBRARY": true,
    "CUSTOM_CSS": "bod32w",
    "SITE_NAME": "Seafile",
    "LOGIN_REMEMBER_DAYS": 10,
    "ENABLE_TERMS_AND_CONDITIONS": 0,
    "SITE_TITLE": "Private Seafile123d",
    "USER_STRONG_PASSWORD_REQUIRED": 1,
    "FORCE_PASSWORD_CHANGE": true,
    "ENABLE_SHARE_TO_ALL_GROUPS": false,
    "ENABLE_USER_CLEAN_TRASH": 1,
    "FREEZE_USER_ON_LOGIN_FAILED": 0,
    "ENABLE_TWO_FACTOR_AUTH": 1,
    "USER_PASSWORD_MIN_LENGTH": 6,
    "TEXT_PREVIEW_EXT": "ac, am, bat, c, cc, cmake, cpp, cs, css, diff, el, h, html, htm, java, js, json, less, make, org, php, pl, properties, py, rb, scala, script, sh, sql, txt, text, tex, vi, vim, xhtml, xml, log, csv, groovy, rst, patch, go, yml",
    "ENABLE_SIGNUP": 0,
    "USER_PASSWORD_STRENGTH_LEVEL": 2,
    "FILE_SERVER_ROOT": "http://127.0.0.1:8082",
    "LOGIN_ATTEMPT_LIMIT": 5
}

```

**Errors**

* 403 Permission denied.

### update web settings info

**PUT** <https://cloud.seafile.com/api/v2.1/admin/web-settings/>

**Sample request**

```
curl  -X PUT -d "USER_PASSWORD_STRENGTH_LEVEL=2&USER_STRONG_PASSWORD_REQUIRED=1" -H "Content-Type: multipart/form-data"  -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' https://cloud.seafile.com/api/v2.1/admin/web-settings/

```

**Sample response**

```
{
    "DISABLE_SYNC_WITH_ANY_FOLDER": 1,
    "ENABLE_USER_CREATE_ORG_REPO": true,
    "SHARE_LINK_TOKEN_LENGTH": 20,
    "REPO_PASSWORD_MIN_LENGTH": 10,
    "REGISTRATION_SEND_MAIL": 0,
    "SHARE_LINK_PASSWORD_MIN_LENGTH": 8,
    "ENABLE_BRANDING_CSS": 0,
    "ENABLE_REPO_HISTORY_SETTING": 0,
    "SERVICE_URL": "http://127.0.0.1:8000",
    "ACTIVATE_AFTER_REGISTRATION": 1,
    "ENABLE_ENCRYPTED_LIBRARY": true,
    "CUSTOM_CSS": "bod",
    "SITE_NAME": "Seafile",
    "LOGIN_REMEMBER_DAYS": 10,
    "ENABLE_TERMS_AND_CONDITIONS": 0,
    "SITE_TITLE": "Private Seafile123d",
    "USER_STRONG_PASSWORD_REQUIRED": 1,
    "FORCE_PASSWORD_CHANGE": true,
    "ENABLE_SHARE_TO_ALL_GROUPS": 1,
    "ENABLE_USER_CLEAN_TRASH": 1,
    "FREEZE_USER_ON_LOGIN_FAILED": 0,
    "ENABLE_TWO_FACTOR_AUTH": 1,
    "USER_PASSWORD_MIN_LENGTH": 2,
    "TEXT_PREVIEW_EXT": "ac, am, bat, c, cc, cmake, cpp, cs, css, diff, el, h, html, htm, java, js, json, less, make, org, php, pl, properties, py, rb, scala, script, sh, sql, txt, text, tex, vi, vim, xhtml, xml, log, csv, groovy, rst, patch, go, yml",
    "ENABLE_SIGNUP": 0,
    "USER_PASSWORD_STRENGTH_LEVEL": 2,
    "FILE_SERVER_ROOT": "http://127.0.0.1:8082",
    "LOGIN_ATTEMPT_LIMIT": 5
}

```

**Errors**

* 400 Request parameter incorrect.
* 403 Permission denied.
* 500 Internal Server Error.

### update logo

**POST** <https://cloud.seafile.com/api/v2.1/admin/logo/>

**Sample request**

```
curl -i -X POST -H "Content-Type: multipart/form-data"  -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' 
-F "logo=@logo_pic.png" https://cloud.seafile.com/api/v2.1/admin/logo/

```

**Sample response**

```
{"logo_path":"https://cloud.seafile.com/media/custom/mylogo.png"}

```

**Errors**

* 400 Request parameter incorrect.
* 403 Permission denied.
* 500 Internal Server Error.

### update favicon

**POST** <https://cloud.seafile.com/api/v2.1/admin/favicon/>

**Sample request**

```
curl -i -X POST -H "Content-Type: multipart/form-data"  -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' 
-F "favicon=@favicon_pic.png" https://cloud.seafile.com/api/v2.1/admin/favicon/

```

**Sample response**

```
{"favicon_path":"https://cloud.seafile.com/media/custom/favicon.ico"}

```

**Errors**

* 400 Request parameter incorrect.
* 403 Permission denied.
* 500 Internal Server Error.

### update login background image

**POST** <https://cloud.seafile.com/api/v2.1/admin/login-background-image/>

**Sample request**

```
curl -i -X POST -H "Content-Type: multipart/form-data"  -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' 
-F "login_bg_image=@login_bg_image_pic.png" https://cloud.seafile.com/api/v2.1/admin/login-background-image/

```

**Sample response**

```
{"login_bg_image_path":"https://cloud.seafile.com/media/custom/login-bg.jpg"}

```

**Errors**

* 400 Request parameter incorrect.
* 403 Permission denied.
* 500 Internal Server Error.

## users

### list all users' info

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

### get a user's info

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

### update user info

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

### add user

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

### delete user

**DELETE** <https://cloud.seafile.com/api/v2.1/admin/users/{email}/>

**Sample request**

```
curl -X DELETE -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/admin/users/foo@foo.com/"

```

**Sample response**

```
{success: true}

```

### reset user password

**PUT** <https://cloud.seafile.com/api/v2.1/admin/users/{email}/reset-password/>

**Sample request**

```
curl -X PUT -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/admin/users/foo@foo.com/reset-password/"

```

**Sample response**

```
{"new_password":"mZWp6A3vQc"}

```

### update users quota in batch

**POST** <https://cloud.seafile.com/api/v2.1/admin/users/batch/>

**request parameters**

* operation， must be 'set-quota'
* email, can be mutiple
* quota_total, unit is MB.

**Sample request**

```
curl -X POST "operation=set-quota&email=test@seafiletest.com&email=admin@seafiletest.com&quota_total=2222" -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/admin/users/batch/"

```

**Sample response**

```
{
	"failed":[],
    "success":[
    	{
        	"quota_total":2222000000,
            "email":"test@seafiletest.com"
        },{
        	"quota_total":2222000000,
            "email":"admin@seafiletest.com"
        }
     ]
}

```

### delete users in batch

**POST** <https://cloud.seafile.com/api/v2.1/admin/users/batch/>

**request parameters**

* operation， must be 'delete-user'
* email, can be mutiple

**Sample request**

```
curl -X POST "operation=delete-user&email=c1@c1.com&email=c3@c3.com" -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/admin/users/batch/"

```

**Sample response**

```
{
	"failed":[],
    "success":[
    	{"email":"c1@c1.com"},
        {"email":"c3@c3.com"}
    ]
}

```

### add users in batch

**POST** <https://cloud.seafile.com/useradmin/batchadduser/>

**Sample request**

```
curl -X POST -F "file=new_users.xlsx" -H "Content-Type: multipart/form-data"  -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4'  https://cloud.seafile.com/useradmin/batchadduser/

```

### List all admin users' info

**GET** <https://cloud.seafile.com/api/v2.1/admin/admin-users/>

**Sample request**

```
curl -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/admin/admin-users/"

```

**Sample response**

```
{
    "available_admin_roles": [
        "daily_admin",
        "default_admin",
        "audit_admin",
        "system_admin"
    ],
    "admin_users": [
        {
            "login_id": "",
            "quota_usage": 43624863,
            "last_login": "2019-08-21T10:14:48.879",
            "name": "851958789",
            "create_time": "2019-06-26T03:42:45+00:00",
            "is_active": true,
            "is_staff": true,
            "contact_email": "",
            "reference_id": "",
            "department": "",
            "quota_total": 121212000000,
            "role": "default",
            "admin_role": "default_admin",
            "email": "851958789@qq.com"
        },
        {
            "login_id": "",
            "quota_usage": 0,
            "last_login": "",
            "name": "a6",
            "create_time": "2019-07-16T10:16:57+00:00",
            "is_active": true,
            "is_staff": true,
            "contact_email": "",
            "reference_id": "",
            "department": "",
            "quota_total": -2,
            "role": "default",
            "admin_role": "default_admin",
            "email": "a6@a6.com"
        }
    ]
}

```

### update admin role

**PUT** <https://cloud.seafile.com/api/v2.1/admin/admin-role/>

**Sample request**

```
curl -X PUT -d "email=as@as.com&role=system_admin" -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/admin/admin-role/"

```

**Sample response**

```
{
    "role": "system_admin",
    "email": "as@as.com"
}

```

### add admin in batch

**POST** <https://cloud.seafile.com/api/v2.1/admin/admin-users/batch/>

**request parameters**

* emails, s string contains emails separated by ','

**Sample request**

```
curl -X POST -d "emails=q1@q1.com,q2@q2.com" -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/admin/admin-role/"

```

**Sample response**

```
{
    "new_admin_info": [
        {
            "login_id": "",
            "quota_usage": 0,
            "last_login": "",
            "name": "q1",
            "create_time": "2019-07-19T02:43:16+00:00",
            "is_active": true,
            "is_staff": true,
            "contact_email": "",
            "reference_id": "",
            "department": "",
            "quota_total": -2,
            "role": "default",
            "email": "q1@q1.com"
        },
        {
            "login_id": "",
            "quota_usage": 0,
            "last_login": "",
            "name": "q2",
            "create_time": "2019-07-19T02:43:54+00:00",
            "is_active": true,
            "is_staff": true,
            "contact_email": "",
            "reference_id": "",
            "department": "",
            "quota_total": 222000000,
            "role": "default",
            "email": "q2@q2.com"
        }
    ]
}

```

### List All libraries Info of A User

**GET** <https://cloud.seafile.com/api/v2.1/admin/libraries/>

**Sample request**

```
curl -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/admin/libraries/?owner="foo@foo.com"

```

**Sample response**

```
{
    "owner": "foo@foo.com",
    "repos": [
        {
            "status": "normal",
            "owner_contact_email": "is.li.xiaoyi@qqq.com",
            "owner_name": "2232323",
            "name": "My Library",
            "encrypted": false,
            "owner_email": "851958789@qq.com",
            "last_modify": "2019-08-19T07:22:02+00:00",
            "file_count": 0,
            "owner": "foo@foo.com",
            "size_formatted": "41.6 MB",
            "id": "34e7fb92-e91d-499d-bcde-c30ea8af9828",
            "size": 43624863
        },
        {
            "status": "normal",
            "owner_contact_email": "is.li.xiaoyi@qqq.com",
            "owner_name": "2232323",
            "name": "额",
            "encrypted": false,
            "owner_email": "851958789@qq.com",
            "last_modify": "2019-08-19T07:22:02+00:00",
            "file_count": 0,
            "owner": "foo@foo.com",
            "size_formatted": "0 bytes",
            "id": "ff13807c-36f1-4ae0-b667-68c5a72fed47",
            "size": 0
        }
    ],
    "name": ""
}

```

### List All Libraries Share to a User

**GET** <https://cloud.seafile.com/api/v2.1/admin/users/{email}/repos-share-in//>

**request parameter**

* email

**Sample request**

```
curl -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/admin/users/foo@foo.com/repos-share-in/"

```

**Sample response**

```
[
	{
    	"status":"",
    	"owner_contact_email":"foo@foo.com",
        "owner_name":"foo",
        "name":"fofofofo",
        "encrypted":false,
        "owner_email":"foo@foo.com",
        "last_modify":"2019-08-26T03:40:28+00:00",
        "file_count":0,
        "owner":"foo@foo.com",
        "size_formatted":"0\u00a0bytes",
        "id":"006633b8-cfd1-4d87-b000-a2881eab3633",
        "size":0
    }
]

```

### List All Share Links of a user

**GET** <https://cloud.seafile.com/api/v2.1/admin/users/{email}/share-links/>

**request parameter**

* email

**Sample request**

```
curl -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/admin/users/foo@foo.com/share-links/"

```

**Sample response**

```
[
    {
        "size": 386,
        "repo_id": "34e7fb92-e91d-499d-bcde-c30ea8af9828",
        "ctime": "2019-08-20T02:28:22+00:00",
        "creator_name": "2232323",
        "creator_email": "foo@foo.com",
        "obj_name": "mar.md",
        "token": "a7c8f121b0274a789adf",
        "view_cnt": 0,
        "link": "http://127.0.0.1:8000/f/a7c8f121b0274a789adf/",
        "expire_date": "2019-08-24T02:28:22+00:00",
        "path": "/mar.md",
        "creator_contact_email": "foo@foo.com",
        "is_dir": false,
        "permissions": {
            "can_edit": false,
            "can_download": true
        },
        "is_expired": true,
        "repo_name": "My Library"
    }
]

```

### Delete a Share Link

**DELETE** <https://cloud.seafile.com/api/v2.1/admin/share-links/{token}/>

**Sample request**

```
curl -X DELETE -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/admin/share-links/a7c8f121b0274a789adf/"

```

**Sample response**

```
{"success":true}

```

### List All Upload Links of a user

**GET** <https://cloud.seafile.com/api/v2.1/admin/user/{email}/upload-links/>

**request parameter**

* email

**Sample request**

```
curl -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/admin/users/foo@foo.com/upload-links/"

```

**Sample response**

```
[
    {
        "view_cnt": 0,
        "ctime": "2019-08-27T02:23:05+00:00",
        "creator_name": "2232323",
        "creator_email": "foo@foo.com",
        "creator_contact_email": "foo@foo.com",
        "token": "84f45d6ac36245f695d7",
        "repo_id": "34e7fb92-e91d-499d-bcde-c30ea8af9828",
        "link": "http://127.0.0.1:8000/u/d/84f45d6ac36245f695d7/",
        "obj_name": "里",
        "path": "/里/",
        "repo_name": "My Library"
    }
]

```

### Delete a Upload Link

**DELETE** <https://cloud.seafile.com/api/v2.1/admin/upload-links/{token}/>

**Sample request**

```
curl -X DELETE -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/admin/upload-links/a7c8f121b0274a789adf/"

```

**Sample response**

```
{"success":true}

```

### List All Groups that User Has Joined

**GET** <https://cloud.seafile.com/api/v2.1/admin/users/{email}/groups/>

**request parameter**

* email

**Sample request**

```
curl -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/admin/users/foo@foo.com/groups/"

```

**Sample response**

```
[
    {
        "owner_name": "2232323",
        "name": "3",
        "created_at": "2019-07-09T02:42:43+00:00",
        "quota": -1,
        "parent_group_id": 0,
        "role": "member",
        "owner": "851958789@qq.com",
        "id": 163
    },
    {
        "owner_name": "2232323",
        "name": "312",
        "created_at": "2019-07-08T06:00:02+00:00",
        "quota": -1,
        "parent_group_id": 0,
        "role": "member",
        "owner": "851958789@qq.com",
        "id": 162
    }
]

```

### Delete a Group by ID

**DELETE** <https://cloud.seafile.com/api/v2.1/admin/groups/{group_id}/>

**Sample request**

```
curl -X DELETE -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/admin/groups/?email="foo@foo.com"

```

**Sample response**

```
{"success":true}

```

### Set/Unset Force 2FA for User

**PUT** <https://cloud.seafile.com/api2/two-factor-auth/{email}/>

**Request parameters**

* force_2fa, 1 or 0, represent set or unset force 2FA for user.

**Sample request**

```
curl -X PUT -d "force_2fa=1" -H "Authorization: Token 4c3fa38f9f2fee40485446afdee7a23749cb6911" -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api2/two-factor-auth/foo@foo.com/"

```

**Sample response**

```
{
    "success": true
}

```

**Errors**

* 400 user not found.
* 500 Internal Server Error.

### Delete Verified 2FA Devices

**DELETE** <https://cloud.seafile.com/api2/two-factor-auth/{email}/>

Remove records from devices that have been verified by 2-step verification. These devices will require 2-step verification the next time they log in.

**Sample request**

```
curl -X DELETE -H "Authorization: Token 4c3fa38f9f2fee40485446afdee7a23749cb6911" -H 'Accept: application/json; charset=utf-8; indent=4' https://cloud.seafile.com/api2/two-factor-auth/foo@foo.com/

```

**Sample response**

```
{
    "success": true
}

```

**Errors**

* 400 email can not be empty, or user not found.
* 500 Internal Server Error.

## Organizations

### List All Groups of an Organization

**GET** <https://cloud.seafile.com/api/v2.1/admin/organizations/{org_id}/groups/>

**Sample request**

```
curl -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' https://cloud.seafile.com/api/v2.1/admin/organizations/7/groups/

```

**Sampple response**

```
{
    "groups": [
        {
            "created_at": "2019-09-02T03:17:38+00:00",
            "group_id": 419,
            "creator_name": "org222@org222.com",
            "group_name": "org222gourps"
        }
    ]
}

```

### List All Libraries of an Organization

**GET** <https://cloud.seafile.com/api/v2.1/admin/organizations/{org_id}/libraries/>

**Sample request**

```
curl -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' https://cloud.seafile.com/api/v2.1/admin/organizations/7/libraries/

```

**Sampple response**

```
{
    "repos": [
        {
            "repo_id": "06c6cede-75e7-4d73-835c-81e0ad4771e2",
            "owner_email": "bbb@org222.com",
            "repo_name": "My Library"
        },
        {
            "repo_id": "642fdc91-b437-44b1-80b2-5f8ad9aa3c21",
            "owner_email": "aaa@org222.com",
            "repo_name": "My Library"
        }
    ]
}

```

## Notifications

### List All System Notifications

**GET** <https://cloud.seafile.com/api/v2.1/admin/sys-notifications/>

**Sample request**

```
curl -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' https://cloud.seafile.com/api/v2.1/admin/sys-notifications/

```

**Sampple response**

```
{
    "notifications": [
        {
            "id": 4,
            "msg": "22222",
            "is_current": false
        },
        {
            "id": 3,
            "msg": "fefeff",
            "is_current": true
        },
        {
            "id": 1,
            "msg": "test",
            "is_current": false
        }
    ]
}

```

### Add a System Notification

**POST** <https://cloud.seafile.com/api/v2.1/admin/sys-notifications/>

**Request parameters**

* msg

**Sample request**

```
curl -X POST -d "msg='warning!'" -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' https://cloud.seafile.com/api/v2.1/admin/sys-notifications/

```

**Sampple response**

```
{
    "notification": {
        "id": 5,
        "msg": "warning!",
        "is_current": false
    }
}

```

### Set a System Notification to current

**PUT** <https://cloud.seafile.com/api/v2.1/admin/sys-notifications/{nid}/>

**Sample request**

```
curl -X POST -d "msg='warning!'" -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' https://cloud.seafile.com/api/v2.1/admin/sys-notifications/5/

```

**Sampple response**

```
{
    "success": true
}

```

### Delete a System notification

**DELETE** <https://cloud.seafile.com/api/v2.1/admin/sys-notifications/{nid}/>

**Sample request**

```
curl -X POST -d "msg='warning!'" -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' https://cloud.seafile.com/api/v2.1/admin/sys-notifications/5/

```

**Sampple response**

```
{
    "success": true
}

```

## Statistics

### List User Monthly Traffic

**GET** <https://cloud.seafile.com/api/v2.1/admin/statistics/system-user-traffic/>

**Request parameters**

* month, string
* page, current page.
* per_page

**Sample request**

```
curl -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/admin/statistics/system-user-traffic/?month=201910&per_page=1&page=1"

```

**Sample response**

```
{
    "user_monthly_traffic_list": [
        {
            "email": "a1@a1.com",
            "name": "a1",
            "sync_file_upload": 0,
            "sync_file_download": 0,
            "web_file_upload": 19888016,
            "web_file_download": 0,
            "link_file_upload": 0,
            "link_file_download": 0
        }
    ],
    "has_next_page": true
}

```

### List Org Monthly Traffic

**GET** <https://cloud.seafile.com/api/v2.1/admin/statistics/system-org-traffic/>

**Request parameters**

* month, string
* page, current page.
* per_page

**Sample request**

```
curl -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/admin/statistics/system-org-traffic/?month=201910&per_page=1&page=1"

```

**Sample response**

```
{
    "org_monthly_traffic_list": [
        {
            "org_id": 1,
            "org_name": "",
            "sync_file_upload": 0,
            "sync_file_download": 0,
            "web_file_upload": 19888016,
            "web_file_download": 0,
            "link_file_upload": 1400,
            "link_file_download": 0
        }
    ],
    "has_next_page": false
}

```


