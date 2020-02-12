# Libraries

## Get all Libraries

Available for Seafile v6.0.0+

**GET** <https://cloud.seafile.com/api/v2.1/admin/libraries/?page=1&per_page=100>

Get first page (100 records per page) of libraries.

**Sample request**

```
curl -H "Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api/v2.1/admin/libraries/?page=1&per_page=100

```

**Sample response**

```
{
    "page_info": {
        "current_page": 1,
        "has_next_page": true
    },
    "repos": [
        {
            "status": "normal",
            "name": null,
            "encrypted": false,
            "file_count": 0,
            "owner": "lian@lian.com",
            "size_formatted": "0 bytes",
            "id": "04df5005-1dfc-4e30-ae55-95ed6559583f",
            "size": 0
        },
        {
            "status": "normal",
            "name": "My Library",
            "encrypted": false,
            "file_count": 161,
            "owner": "lian@lian.com",
            "size_formatted": "25.4 MB",
            "id": "2deffbac-d7be-4ace-b406-efb799083ee9",
            "size": 26617460
        }
        ...
    ]
}

```

**Errors**

* 403 Permission error, only administrator can perform this action

## Search Library by Name

**GET** [http://127.0.0.1:8000/api/v2.1/admin/search-library/](http://127.0.0.1:8000/api/v2.1/admin/search-library/?query=l)

**Request parameters**

* query

**Sample request**

```
curl -H "Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd" -H 'Accept: application/json; indent=4' http://127.0.0.1:8000/api/v2.1/admin/search-library/?query=l

```

**Sample response**

```
{
    "repo_list": [
        {
            "id": "a0877bb0-c4f8-4316-8e52-c4ce416362c3",
            "name": "lib in test department",
            "owner_email": "3@seafile_group",
            "owner_name": "test department",
            "owner_contact_email": "",
            "size": 0,
            "encrypted": false,
            "file_count": 0,
            "status": "normal"
        },
        {
            "id": "b2134604-ea68-41d0-a075-0970e889b848",
            "name": "lib of 7.1 lian",
            "owner_email": "lian@lian.com",
            "owner_name": "name-of-lian",
            "owner_contact_email": "lian@lian.com",
            "size": 15,
            "encrypted": false,
            "file_count": 0,
            "status": "normal"
        }
    ]
}

```

**Errors**

* 400, query invalid.
* 403 Permission error, only administrator can perform this action

## Search Library by Owner

Available for Seafile v6.0.0+

**GET** <https://cloud.seafile.com/api/v2.1/admin/libraries/?owner=lian@lian.com>

**Request parameters**

* owner

**Sample request**

```
curl -H "Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api/v2.1/admin/libraries/?owner=lian@lian.com

```

**Sample response**

```
{
    "owner": "lian@lian.com",
    "repos": [
        {
            "status": "normal",
            "name": "lib-of-lian",
            "encrypted": false,
            "file_count": 0,
            "owner": "lian@lian.com",
            "size_formatted": "16.5 KB",
            "id": "78c620ee-2989-4427-8eff-7748f4fbebc0",
            "size": 16883
        },
        {
            
            "status": "normal",
            "name": "encrypted",
            "encrypted": true,
            "file_count": 0,
            "owner": "lian@lian.com",
            "size_formatted": "18.1 MB",
            "id": "47695bb8-3364-4274-939d-3c5a0df9710c",
            "size": 18997225
        },
        ...
    ],
    "name": ""
}

```

**Errors**

* 403 Permission error, only administrator can perform this action

## Get a Library info

**GET** <https://cloud.seafile.com/api/v2.1/admin/libraries/{repo_id}/>

**Sample request**

```
curl -H'Authorization: Token 444d2bbf1fc78ffbeedc4704c9f41e32d926ac94' https://cloud.seafile.com/api/v2.1/admin/libraries/00d5c2d4-fc3d-465f-8e2a-ed02d9f8b00f/

```

**Sample response**

```
{
    "id": "00d5c2d4-fc3d-465f-8e2a-ed02d9f8b00f",
    "name": "foolib",
    "owner": "1@seafile_group",
    "owner_email": "1@seafile_group",
    "owner_name": "1",
    "owner_contact_email": "1@seafile_group",
    "size": 0,
    "size_formatted": "0 bytes",
    "encrypted": false,
    "file_count": 0,
    "status": "normal",
    "group_name": "dpt1"
}

```

**Errors**

* 403 Permission error, only administrator can perform this action

## Create Library

**POST** <https://cloud.seafile.com/api/v2.1/admin/libraries/>

**Request parameters**

* name
* owner: default is current admin user

**Sample request**

```
curl -i -X POST -d "name=new_lib_name" -H "Content-Type: multipart/form-data"  -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' https://cloud.seafile.com/api/v2.1/admin/libraries/

```

**Sampple response**

```
{
	"status":"normal",
    "owner_contact_email":"851958789@qq.com",
    "owner_name":"851958789",
    "name":"\u7684",
    "encrypted":false,
    "owner_email":"851958789@qq.com",
    "file_count":0,
    "owner":"851958789@qq.com",
    "size_formatted":"0\u00a0bytes",
    "id":"5d30af42-67df-4082-84a7-621370b190f3",
    "size":0
}

```

## Delete a Library

Available for Seafile v6.0.0+

**DELETE** <https://cloud.seafile.com/api/v2.1/admin/libraries/{repo_id}/>

**Sample request**

```
curl -X DELETE -H 'Authorization: Token 444d2bbf1fc78ffbeedc4704c9f41e32d926ac94' https://cloud.seafile.com/api/v2.1/admin/libraries/ee3b2d19-1a06-47f0-bbfa-554cab3bdedc/

```

**Sample response**

```
{"success":true}

```

**Errors**

* 403 Permission error, only administrator can perform this action

## Update a Library Status

**PUT** [https://cloud.seafile.com/api/v2.1/admin/libraries/{repo_id}/](https://cloud.seafile.com/api/v2.1/admin/libraries/%7Brepo_id%7D/)

**Request parameters**

* status:  `normal` or `read-only`

**Sample request**

```
curl -X PUT -d "status=read-only" -H 'Authorization: Token 444d2bbf1fc78ffbeedc4704c9f41e32d926ac94' -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api/v2.1/admin/libraries/ee3b2d19-1a06-47f0-bbfa-554cab3bdedc/

```

**Sample response**

```
{
    "status": "read-only",
    "owner_contact_email": "a@a.com",
    "owner_name": "aaa",
    "name": "documents",
    "encrypted": false,
    "owner_email": "a@a.com",
    "file_count": 1,
    "owner": "a@a.com",
    "size_formatted": "11 bytes",
    "id": "ee3b2d19-1a06-47f0-bbfa-554cab3bdedc",
    "size": 11
}

```

**Errors**

* 400 status invalid.
* 403 Permission error, only administrator can perform this action.
* 404 Library not found.
* 500 Internal Server Error.

## Transfer a Library

Available for Seafile v6.0.0+

**PUT** <https://cloud.seafile.com/api/v2.1/admin/libraries/{repo_id}/>

**Sample request**

```
curl -X PUT -d "owner=a1@a1.com" -H 'Authorization: Token 444d2bbf1fc78ffbeedc4704c9f41e32d926ac94' https://cloud.seafile.com/api/v2.1/admin/libraries/0dd5949a-94e4-4a8a-b727-9cbe3f2dcad0/

```

**Sample response**

```
{
    "id": "0dd5949a-94e4-4a8a-b727-9cbe3f2dcad0",
    "name": "My Library",
    "owner": "a1@a1.com",
    "owner_email": "a1@a1.com",
    "owner_name": "a1",
    "owner_contact_email": "a1@a1.com",
    "size": 180175,
    "size_formatted": "176.0 KB",
    "encrypted": false,
    "file_count": 1,
    "status": "normal"
}

```

**Errors**

* 400 owner invalid.
* 403 Permission error, only administrator can perform this action
* 404 User not found.
* 404 Library not found.
* 500 Internal Server Error

## Update Library Name

**PUT** <https://cloud.seafile.com/api/v2.1/admin/libraries/{repo_id}/>

**Request parameters**

* name

**Sample request**

```
curl -X PUT -d "name=foolib22" -H 'Authorization: Token 444d2bbf1fc78ffbeedc4704c9f41e32d926ac94' https://cloud.seafile.com/api/v2.1/admin/libraries/ee3b2d19-1a06-47f0-bbfa-554cab3bdedc/

```

**Sample response**

```
{    
    "id": "00d5c2d4-fc3d-465f-8e2a-ed02d9f8b00f",
    "name": "foolib22",
    "owner": "1@seafile_group",
    "owner_email": "1@seafile_group",
    "owner_name": "1",
    "owner_contact_email": "1@seafile_group",
    "size": 0,
    "size_formatted": "0 bytes",
    "encrypted": false,
    "file_count": 0,
    "status": "normal",
    "group_name": "dpt1"
}

```

## Get All Deleted Libraries

**GET** <http://192.168.1.113:8000/api/v2.1/admin/trash-libraries/>

* `page`, default 1.
* `per_page`, default 100.

**Sample request**

```
curl -H 'Authorization: Token 2bac21cab9eb0c4baac10d1e6fc3cf590f0dcf17' -H 'Accept: application/json; charset=utf-8; indent=4' "http://192.168.1.113:8000/api/v2.1/admin/trash-libraries/"

```

**Sample response**

```
{
    "page_info": {
        "current_page": 1,
        "has_next_page": false
    },
    "repos": [
        {
            "owner": "1@1.com",
            "owner_name": "1",
            "delete_time": "2018-06-04T17:24:55+08:00",
            "name": "a-stor-2",
            "id": "ed46b580-8df7-4a2b-bb45-c3d179cfc668"
        },
        {
            "owner": "1@1.com",
            "owner_name": "1",
            "delete_time": "2018-06-04T17:24:54+08:00",
            "name": "a-st",
            "id": "560d9b7b-fd24-4ce3-9e4a-20a953bee1b9"
        },
        {
            "owner": "lian@lian.com",
            "owner_name": "1",
            "delete_time": "2018-06-04T17:21:35+08:00",
            "name": "dst",
            "id": "09b7d3c0-5f0d-49be-9318-7ca136f386cd"
        },
        {
            "owner": "lian@lian.com",
            "owner_name": "1",
            "delete_time": "2018-06-04T17:21:32+08:00",
            "name": "k",
            "id": "fbf4b69c-5a46-41a3-a9a3-58c1274ec536"
        },
        {
            "owner": "lian@lian.com",
            "owner_name": "1",
            "delete_time": "2018-06-04T17:21:29+08:00",
            "name": "src",
            "id": "d4aac5b9-28d4-4372-a4b3-d6de171402df"
        }
    ]
}

```

**Errors**

* 403 Permission error, only administrator can perform this action
* 500 Internal Server Error

## Get Deleted Libraries by Owner

**GET** <http://192.168.1.113:8000/api/v2.1/admin/trash-libraries/?owner={owner}>

* `owner`, library owner's email.

**Sample request**

```
curl -H 'Authorization: Token 2bac21cab9eb0c4baac10d1e6fc3cf590f0dcf17' -H 'Accept: application/json; charset=utf-8; indent=4' "http://192.168.1.113:8000/api/v2.1/admin/trash-libraries/?owner=1@1.com"

```

**Sample response**

```
{
    "repos": [
        {
            "owner": "1@1.com",
            "owner_name": "1",
            "delete_time": "2018-06-04T17:24:55+08:00",
            "name": "a-stor-2",
            "id": "ed46b580-8df7-4a2b-bb45-c3d179cfc668"
        },
        {
            "owner": "1@1.com",
            "owner_name": "1",
            "delete_time": "2018-06-04T17:24:54+08:00",
            "name": "a-st",
            "id": "560d9b7b-fd24-4ce3-9e4a-20a953bee1b9"
        }
    ],
    "search_owner": "1@1.com"
}

```

**Errors**

* 403 Permission error, only administrator can perform this action
* 500 Internal Server Error

## Clean Deleted Library

**DELETE** <http://192.168.1.113:8000/api/v2.1/admin/trash-libraries/{repo_id}/>

* `repo_id`, deleted library's id.

**Sample request**

```
curl -X DELETE -H 'Authorization: Token 2bac21cab9eb0c4baac10d1e6fc3cf590f0dcf17' -H 'Accept: application/json; charset=utf-8; indent=4' "http://192.168.1.113:8000/api/v2.1/admin/trash-libraries/560d9b7b-fd24-4ce3-9e4a-20a953bee1b9/"

```

**Sample response**

```
{
    "success": true
}

```

**Errors**

* 403 Permission error, only administrator can perform this action
* 500 Internal Server Error

## Restore Deleted Library

**PUT** <http://192.168.1.113:8000/api/v2.1/admin/trash-libraries/d4aac5b9-28d4-4372-a4b3-d6de171402df/>

* `repo_id`, deleted library's id.

**Sample request**

```
curl -X PUT -H 'Authorization: Token 2bac21cab9eb0c4baac10d1e6fc3cf590f0dcf17' -H 'Accept: application/json; charset=utf-8; indent=4' "http://192.168.1.113:8000/api/v2.1/admin/trash-libraries/d4aac5b9-28d4-4372-a4b3-d6de171402df/"

```

**Sample response**

```
{
    "success": true
}

```

**Errors**

* 403 Permission error, only administrator can perform this action
* 404 Library does not exist in trash.
* 500 Internal Server Error

## Clean All Deleted Libraries

**DELETE** <http://192.168.1.113:8000/api/v2.1/admin/trash-libraries/>

**Sample request**

```
curl -X DELETE -H 'Authorization: Token 2bac21cab9eb0c4baac10d1e6fc3cf590f0dcf17' -H 'Accept: application/json; charset=utf-8; indent=4' "http://192.168.1.113:8000/api/v2.1/admin/trash-libraries/"

```

**Sample response**

```
{
    "success": true
}

```

**Errors**

* 403 Permission error, only administrator can perform this action
* 500 Internal Server Error

## Get Library History Setting

**GET** <https://cloud.seafile.com/api/v2.1/admin/libraries/{repo_id}/history-limit/>

**Sample request**

```
cur -d  -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' https://cloud.seafile.com/api/v2.1/admin/libraries/2f04c909-c957-4c1c-af85-a89d7b520ecb/history-limit/

```

**Sampple response**

```
{"keep_days":-1}

```

## Update Library History Setting

**PUT** <https://cloud.seafile.com/api/v2.1/admin/libraries/{repo_id}/history-limit/>

**Request parameters**

* keep_days: a integer, -1 means no limit. 0 means don't keep history.

**Sample request**

```
cur  -X PUT -d "keep_days=30" -H "Content-Type: multipart/form-data"  -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4'https://cloud.seafile.com/api/v2.1/admin/libraries/2f04c909-c957-4c1c-af85-a89d7b520ecb/history-limit/

```

**Sampple response**

```
{"keep_days":30}

```

## List Library Contents

**GET** <https://cloud.seafile.com/api/v2.1/admin/libraries/{repo_id}/dirents/>

**Request parameters**

* parent_dir

**Sample request**

```
curl -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' https://cloud.seafile.com/api/v2.1/admin/libraries/5e7212d7-1bdb-4351-bc25-58a274b1419f/dirents/?parent_dir=%2F

```

**Sample response**

```
{
	"repo_id":"5e7212d7-1bdb-4351-bc25-58a274b1419f",
    "dirent_list":[
    	{
            "file_size":"",
           "last_update":"2019-08-08T03:39:10+00:00",
           "is_file":false,
           "obj_name":"111"
        },
        {
           "file_size":"",
           "last_update":"2019-08-08T06:18:38+00:00",
           "is_file":false,
           "obj_name":"e"
        }
    ],
    "is_system_library":true,
    "repo_name":"My Library Template"
}

```

## Delete Library Content

**DELETE** <https://cloud.seafile.com/api/v2.1/admin/libraries/{repo_id}/dirent/>

**Request parameters**

* path

**Sample request**

```
cur -X DELETE "path=/111/222/333/e2.docx" -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' https://cloud.seafile.com/api/v2.1/admin/libraries/5e7212d7-1bdb-4351-bc25-58a274b1419f/dirent/

```

**Sampple response**

```
{success: true}

```

## Get Library Content Download Link

**GET** <https://cloud.seafile.com/api/v2.1/admin/libraries/{repo_id}/dirent/>

**Request parameters**

* path
* dl, must be 1

**Sample request**

```
cur -d "path=/111/222/333/e2.docx&dl=1" -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' https://cloud.seafile.com/api/v2.1/admin/libraries/5e7212d7-1bdb-4351-bc25-58a274b1419f/dirent/

```

**Sampple response**

```
{"download_url":"http://127.0.0.1:8082/files/9ac1f8f8-dabe-4b33-85d4-f662494b7275/e2.docx"}

```

## Get Library Content Item

**GET** <https://cloud.seafile.com/api/v2.1/admin/libraries/{repo_id}/dirent/>

**Request parameters**

* path

**Sample request**

```
curl -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' https://cloud.seafile.com/api/v2.1/admin/libraries/5e7212d7-1bdb-4351-bc25-58a274b1419f/dirent/?path=/111/222/333/e2.docx

```

**Sampple response**

```
{
	"file_size":"22.9\u00a0KB",
    "last_update":"2019-08-14T03:15:08+00:00",
    "is_file":true,"obj_name":"6DB125C6C105385F0F81F919F48116FF.jpg"
}

```

## Create Library Folder

**POST** <https://cloud.seafile.com/api/v2.1/admin/libraries/{repo_id}/dirents/>

**Request parameters**

* parent_dir
* obj_name, new folder's name

**Sample request**

```
curl -d "obj_name=my_new_folder"  -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' https://cloud.seafile.com/api/v2.1/admin/libraries/5e7212d7-1bdb-4351-bc25-58a274b1419f/dirents/?parent_dir=%2F

```

**Sample response**

```
{
	"file_size":"",
    "last_update":"2019-08-14T03:46:47+00:00",
    "is_file":false,
    "obj_name":"my_new_folder"
}

```


