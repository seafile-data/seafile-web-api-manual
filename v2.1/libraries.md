# Libraries

## Default Library

### Get Default Library

**GET** <https://cloud.seafile.com/api2/default-repo/>

**Sample request**

```
curl -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd' "https://cloud.seafile.com/api2/default-repo/"

```

**Sample response**

```
{
    "repo_id": "691b3e24-d05e-43cd-a9f2-6f32bd6b800e",
    "exists": true
}

```

### Create Default Library

**POST** <https://cloud.seafile.com/api2/default-repo/>

**Sample request**

```
curl -X POST -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd' "https://cloud.seafile.com/api2/default-repo/"

```

**Sample response**

```
{
    "repo_id": "691b3e24-d05e-43cd-a9f2-6f32bd6b800e",
    "exists": true
}

```

## Libraries

### List Libraries

**GET** <https://cloud.seafile.com/api2/repos/?type={type}>

**Request parameters**

* type
  * `mine`, get my owned libraries.
  * `shared`, get libraries shared to me.
  * `group`, get group libraries.
  * `org`, get shared-with-all libraires.

NOTE: If no `type` parameter contained in the url, this api will return all libraries user can access.

**Sample request for get all libraries I can accessed**

```
curl -H 'Authorization: Token 24fd3c026886e3121b2ca630805ed425c272cb96' -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api2/repos/

```

**Sample response for get all libraries I can accessed**

type field in response could be: 

* 'repo': libraries owned by myself.
* 'srepo': libraries shared to me.
* 'grepo': group libraries or shared-with-all libraries.


```
[
    {
        "owner_contact_email": "foo@foo.com",
        "owner_name": "foo",
        "owner": "foo@foo.com",
        "modifier_email": "foo@foo.com",
        "modifier_contact_email": "foo@foo.com",
        "modifier_name": "foo",
        "name": "私人资料库",
		"id": "fd9d4541-0865-4b2d-9523-8070c8d5d59f",
        "permission": "rw",
        "virtual": false,
        "mtime": 1564118923,
        "mtime_relative": "<time datetime=\"2019-07-26T05:28:43\" is=\"relative-time\" title=\"Fri, 26 Jul 2019 05:28:43 +0000\" >10 days ago</time>",
        "encrypted": false,
        "version": 1,
        "head_commit_id": "5c941c846d5b98452045f43eec0750aa75d99ec9",
		"root": "",
        "type": "repo",
        "salt": "",
        "size_formatted": "0 bytes",
        "size": 0
    },
    {
	    "owner_contact_email": "851958789@qq.com",
        "owner_nickname": "851958789",
        "owner_name": "851958789",
        "owner": "851958789@qq.com",
        "modifier_contact_email": "0",
        "modifier_email": "0",
        "modifier_name": "0",
        "name": "admin",
        "id": "ccc60923-8cdf-4cc8-8f71-df86aba3a085",
        "permission": "rw",
        "encrypted": false,
        "group_name": "",
        "mtime": 1562663599,
        "mtime_relative": "<time datetime=\"2019-07-09T09:13:19\" is=\"relative-time\" title=\"Tue, 9 Jul 2019 09:13:19 +0000\" >2019-07-09</time>",
        "share_type": "personal",
        "version": 1,
        "is_admin": true,
        "head_commit_id": "db41f3b32a3d6003d87c7e0f835e89fa21e439d4",
        "root": ""
        "type": "srepo",
        "salt": "",
        "size_formatted": "81.3 KB",
        "size": 83260,
    },
    {
        "owner_contact_email": "foo@foo.com",
        "owner_name": "foo",
        "owner": "foo@foo.com",
        "modifier_email": "foo@foo.com",
        "modifier_contact_email": "foo@foo.com",
		"modifier_name": "foo",
        "name": "repo_src",
		"id": "b9d5e4ad-964f-4510-b328-cd9b44089f91",
        "permission": "rw",
        "virtual": false,
		"mtime": 1563781300,
        "mtime_relative": "<time datetime=\"2019-07-22T07:41:40\" is=\"relative-time\" title=\"Mon, 22 Jul 2019 07:41:40 +0000\" >2019-07-22</time>",
        "encrypted": false,
        "version": 1,
        "head_commit_id": "93ce6ee4db3ebf9289b88d054aa9d507133eebe1",
        "root": "",
        "type": "repo",
        "salt": "",
        "size_formatted": "0 bytes",
        "size": 0
    }
]

```

**Sample request for get my owned libraries**

```
curl -H "Authorization: Token 8cc0e7085a24b6abfee721e758b6aab4a90e7321" -H 'Accept: application/json; indent=4' "https://cloud.seafile.com/api2/repos/?type=mine"

```

**Sample response for get my owned libraries**

```
[
    {
        "owner": "1@1.com",
        "modifier_email": "1@1.com",
        "modifier_contact_email": "1@1.com",
        "modifier_name": "1"
        "storage_id": "old_version_id",
        "root": "",
        "name": "lib-of-1",
        "id": "1f6a3ed4-a53c-4f02-a688-eac373347127",
        "permission": "rw",
        "storage_name": "旧版本",
        "virtual": false,
        "mtime": 1531884876,
        "mtime_relative": "<time datetime=\"2018-07-18T11:34:36\" is=\"relative-time\" title=\"Wed, 18 Jul 2018 11:34:36 +0800\" >59 seconds ago</time>",
        "head_commit_id": "a0727e27e73a513c281bd7f3e78bcd65767d095c",
        "encrypted": false,
        "version": 1,
        "type": "repo",
        "salt": "",
        "size_formatted": "0 bytes",
        "size": 0
    },
]

```

### Create Library

**POST** [https://cloud.seafile.com/api2/repos/](https://cloud.seafile.com/api/v2.1/repos/)

**Request parameters**

* repo_name: name of library
* passwd: needed by encrypted library
* storage_id: when multiple storage backends enabled, use this identifier for storage object.

**Sample request**

```
curl -v -d "repo_name=new_repo" -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd' -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api/v2.1/repos/

```

**Sample response**

```
{
    "repo_size": 0,
    "repo_id": "9d8ae7b1-dbe7-4783-ac5a-6e0aca26bc77",
    "encrypted": false,
    "mtime": 1565339214,
    "email": "foo@foo.com",
    "repo_name": "new_repo"
}

```

**Success**

   Response code 200 and newly created library information are returned.

**Errors**

* 400 Library name missing.
* 520 Operation failed.

### Create Encrypted Library

**POST** <https://cloud.seafile.com/api2/repos/>﻿

**Request parameters**

* `from` : if not passed, Seafile will generate repo sync token and then return it; if set its value to `web` , Seafile will not generate repo sync token.
* `name` : repo's name.
* `repo_id` 
* `magic` 
* `random_key` 
* `enc_version` : `0`  or `1`  or `2`  or `3` . if passed `0`  or `1`  or `2` , Seafile will create v2 encrypted repo; if passed `3` , Seafile will create v3 encrypted repo. Note, if `3`  is passed, client MUST passes `salt`  parameter too.
* `salt` : used for create v3 encrypted repo.

**Sample request**

```
curl -v -d "name=dist&repo_id=7914e90a-c34e-4fe9-9497-4cec4ce708f9&magic=06d3cc794f7a18ad5b20d0cb279ebb347b39b555d22adc3e3e09f3312965b134&random_key=c2db23a18735962eb0ebbf6ae0665979bf22f0232976b913dab8f2851930039285009287154c08c3de11ab53348e63b4&enc_version=2" -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd' -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api2/repos/

```

**Sample response**

```
{'email': u'lian@lian.com',
 'enc_version': 2,
 'encrypted': 1,
 'head_commit_id': u'822e90c1ad6d1c28aa9656f7429f20e05a38e0c6',
 'magic': u'06d3cc794f7a18ad5b20d0cb279ebb347b39b555d22adc3e3e09f3312965b134',
 'mtime': 1558337264,
 'mtime_relative': u'<time datetime="2019-05-20T07:27:44" is="relative-time" title="Mon, 20 May 2019 07:27:44 +0000" >Just now</time>',
 'random_key': u'c2db23a18735962eb0ebbf6ae0665979bf22f0232976b913dab8f2851930039285009287154c08c3de11ab53348e63b4',
 'relay_addr': '127.0.0.1',
 'relay_id': u'ba789883abf9e65d8fb91b85635bb0485b3548e6',
 'relay_port': 10001,
 'repo_desc': u'dist',
 'repo_id': u'7914e90a-c34e-4fe9-9497-4cec4ce708f9',
 'repo_name': u'dist',
 'repo_size': 0,
 'repo_size_formatted': u'0\xa0bytes',
 'repo_version': 1,
 'salt': '',
 'token': u'cc7a4f953c5dd27c8e6021017273513c5c47815f'}

```

**Success**

   Response code 200 and newly created library information are returned.

### Delete Library

**DELETE** <https://cloud.seafile.com/api2/repos/{repo-id}/>

**Sample request**

```
curl -v -X DELETE -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd' -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api2/repos/8f5f2222-72a8-454f-ac40-8397c5a556a8/

```

**Sample response**

"success"

**Errors**

* 400 Library does not exist.
* 403 Only library owner can perform this operation.

### Rename Library

**POST** <https://cloud.seafile.com/api2/repos/{repo-id}/?op=rename>

**Sample request**

```
curl -d "repo_name=new-repo-name"  -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd' -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api2/repos/8f5f2222-72a8-454f-ac40-8397c5a556a8/?op=rename

```

**Sample response**

"success"

**Errors**

* 404 Library not found.
* 403 You do not have permission to rename this library.
* 500 Unable to rename library

### Transfer Library

#### Transfer Library to User

**PUT** <https://cloud.seafile.com/api2/repos/{repo-id}/owner/>

**Request parameters**

* repo-id
* owner

**Sample request**

```
curl -v -X PUT -d "owner=new@owner.com" -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d9b477fd' -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api2/repos/dae8cecc-2359-4d33-aa42-01b7846c4b32/owner/

```

**Sample response**

```
{
    "success": True
}

```

**Errors**

* 440 Email invalid.
* 403 Permission error(only administrator/repo-owner can perform this action).
* 404 Library not found.
* 404 User not found.

#### Transfer Library to Department

**PUT** <https://cloud.seafile.com/api2/repos/{repo-id}/owner/>

**Request parameters**

* repo-id
* owner, the format should be "`department_id`@seafile_group"

**Sample request**

```
curl -v -X PUT -d "owner=1@seafile_group" -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d9b477fd' -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api2/repos/dae8cecc-2359-4d33-aa42-01b7846c4b32/owner/

```

**Sample response**

```
{
    "success": True
}

```

**Errors**

* 440 Email invalid.
* 403 Permission error(only administrator/repo-owner can perform this action).
* 404 Library not found.
* 404 User not found.

### Get Library Info

**GET** <https://cloud.seafile.com/api2/repos/{repo-id}/>

**Request parameters**

* repo-id

**Sample request**

```
curl -G -H 'Authorization: Token 24fd3c026886e3121b2ca630805ed425c272cb96' -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api2/repos/632ab8a8-ecf9-4435-93bf-f495d5bfe975/

```

**Sample response**

For normal library

```
{
    "permission": "rw",
    "encrypted": false,
    "mtime": 1572659621,
    "owner": "self",
    "modifier_contact_email": "foo@foo.com",
    "id": "11894b06-7b48-4ec5-ac11-a0da45d7ee70",
    "modifier_name": "foo",
    "size": 127696753,
    "modifier_email": "foo@foo.com",
    "name": "lib of foo",
    "root": "ebc2aad269e11a2123d3bb17aca6096651dee18c",
    "file_count": 5,
    "type": "repo"
}

```

For encrypted library

```
{
    "magic": "18008830ca813ee9027a914c5b962a2ec6c5e4a14a6c114eda5b302588f6d8bd",
    "permission": "rw",
    "encrypted": true,
    "enc_version": 2,
    "mtime": 1572687916,
    "owner": "self",
    "modifier_contact_email": "foo@foo.com",
    "id": "4afdaa07-c6a8-4948-a956-1df127c92708",
    "modifier_name": "foo",
    "size": 11260342,
    "modifier_email": "foo@foo.com",
    "name": "cas",
    "root": "c44003e5ad3cd957e12f77fd0de7d340dd74877b",
    "salt": "",
    "file_count": 61,
    "random_key": "3d6e40ec287e4e72892fdb98093adb8adfa5638c461258079d76d2867443c97b83a074d70c5fc3ff09d550ca183e1059",
    "type": "repo"
}

```

### Get Library Owner

**GET** <https://cloud.seafile.com/api2/repos/{repo-id}/owner/>

**Request parameters**

* repo-id

**Sample request**

```
curl -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d9b477fd' -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api2/repos/dae8cecc-2359-4d33-aa42-01b7846c4b32/owner/

```

**Sample response**

```
{
"owner": "user@example.com"
}

```

**Errors**

* 403 Permission error(only administrator/repo-owner can perform this action).

## Library History and Trash

### Get Library History

**GET** <https://cloud.seafile.com/api/v2.1/repos/{repo_id}/history/>

**Request parameters**

* repo_id
* page, default 1
* per_page, default 100

**Sample request**

```
curl -H 'Authorization: Token 0eb24ce5db35a31f70171eca2f760f03f59fa09a' -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/repos/7460f7ac-a0ff-4585-8906-bb5a57d2e118/history/"

```

**Sample response**

```
{
    "data": [
        {
            "commit_id": "2b1313e4bbce2b938403c829b114b12b549128a3",
            "time": "2017-04-10T03:24:09+00:00",
            "description": "Recovered deleted directory \"456\"",
            "creator": "lian@lian.com"
        },
        {
            "commit_id": "0be8bba456ece31598557d9f3d5471b5b4d9d7c0",
            "time": "2017-04-10T03:23:49+00:00",
            "description": "Removed directory \"456\"",
            "creator": "lian@lian.com"
        },
        {
            "commit_id": "e6f21a80d60b7f1797434fdab622e562af937f81",
            "time": "2017-04-10T03:23:45+00:00",
            "description": "Deleted \"empty.docx\"",
            "creator": "lian@lian.com"
        },
        {
            "commit_id": "0bddb7401a75a9799209a24fb118e8d49151b6d6",
            "time": "2017-04-10T03:23:41+00:00",
            "description": "Deleted \"QQ_account_manager.png\"",
            "creator": "lian@lian.com"
        }
    ],
    "more": false
}

```

**Errors**

* 403 Permission denied.
* 404 Library not found.
* 500 Internal Server Error

### Get Library History Limit Days

**GET** <https://cloud.seafile.com/api2/repos/{repo-id}/history-limit/>

**Request parameters**

* repo-id

**Sample request**

```
curl -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d9b477fd' -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api2/repos/dae8cecc-2359-4d33-aa42-01b7846c4b32/history-limit/

```

**Sample response**

```
{
"keep_days": -1,
}

```

**Errors**

* 403 Permission denied.
* 404 Library not found.
* 500 Internal Server Error

### Set Library History Limit Days

**PUT** <https://cloud.seafile.com/api2/repos/{repo-id}/history-limit/>

**Request parameters**

* repo-id
* keep_days. -1 for keep full history; 0 for do not keep history; positive number for keep a period of limit days.

**Sample request**

```
curl -v -X PUT -d "keep_days=4" -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd' -H 'Accept: application/json; charset=utf-8; indent=4' https://cloud.seafile.com/api2/repos/dae8cecc-2359-4d33-aa42-01b7846c4b32/history-limit/

```

**Sample response**

```
{
"keep_days": 4,
}

```

**Errors**

* 400 keep_days invalid.
* 403 Permission denied.
* 404 Library not found.
* 500 Internal Server Error
* 520 Failed to set library history limit.

### Get Library Trash

**GET** <https://cloud.seafile.com/api/v2.1/repos/{repo_id}/trash/>

**Request parameters**

* repo_id
* path, default '/'.
* per_page, default 100.
* scan_stat, An opaque status returned by the last call. In the first call, None must be passed. The last entry of the result list contains a 'scan_stat' attribute. In the next call, pass in the returned 'scan_stat'.

**Sample request**

```
curl -H 'Authorization: Token 0eb24ce5db35a31f70171eca2f760f03f59fa09a' -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/repos/7460f7ac-a0ff-4585-8906-bb5a57d2e118/trash/"

```

**Sample response**

```
{
    "scan_stat": "2b1313e4bbce2b938403c829b114b12b549128a3",
    "data": [
        {
            "commit_id": "2364981a2bef50c16281a664df55af209019a88c",
            "scan_stat": null,
            "obj_id": "f86ef37332e89d6a132e27ce857c76e15971b227",
            "deleted_time": "2017-04-10T03:23:41+00:00",
            "obj_name": "QQ_account_manager.png",
            "is_dir": false,
            "parent_dir": "/",
            "size": 77970
        },
        {
            "commit_id": "0bddb7401a75a9799209a24fb118e8d49151b6d6",
            "scan_stat": null,
            "obj_id": "10ae7309338efe92d9ceddb9d6835463d277da34",
            "deleted_time": "2017-04-10T03:23:45+00:00",
            "obj_name": "empty.docx",
            "is_dir": false,
            "parent_dir": "/456/",
            "size": 10682
        }
        ...
    ],
    "more": true
}

```

Get more trash items.

**Sample request**

```
curl -H 'Authorization: Token 0eb24ce5db35a31f70171eca2f760f03f59fa09a' -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api/v2.1/repos/7460f7ac-a0ff-4585-8906-bb5a57d2e118/trash/?scan_stat=2b1313e4bbce2b938403c829b114b12b549128a3"

```

**Sample response**

```
{
    "scan_stat": null,
    "data": [
        {
            "commit_id": "726d2ce009df9176592ab88eca297b5e50c15639",
            "scan_stat": null,
            "obj_id": "cfc5e4299a862b366c98eeb7f5a8a1f689d2916a",
            "deleted_time": "2017-04-10T09:11:02+00:00",
            "obj_name": "empty.xlsx",
            "is_dir": false,
            "parent_dir": "/456/",
            "size": 8176
        },
        {
            "commit_id": "2b1313e4bbce2b938403c829b114b12b549128a3",
            "scan_stat": null,
            "obj_id": "414a75f5c67ca56c480ca2ae9137b7812940c3ce",
            "deleted_time": "2017-04-10T09:11:01+00:00",
            "obj_name": "empty.pptx",
            "is_dir": false,
            "parent_dir": "/456/",
            "size": 40506
        }
    ],
    "more": false
}

```

**Errors**

* 403 Permission denied.
* 404 Library not found.
* 500 Internal Server Error

### Clean Library Trash

**DELETE** <https://cloud.seafile.com/api/v2.1/repos/{repo_id}/trash/>

**Request parameters**

* repo_id

**Sample request**

```
curl -X DELETE -H "Authorization: Token f97d5b77cee9438451b92d29155f61c5abce3c4f" -H 'Accept: application/json; indent=4' "https://cloud.seafile.com/api/v2.1/repos/d4f596ed-09ea-4ac6-8d59-12acbd089097/trash/"

```

**Sample response**

```
{
    "success": true
}

```

then you get library trash again, no data in response.

```
curl -H "Authorization: Token f97d5b77cee9438451b92d29155f61c5abce3c4f" -H 'Accept: application/json; indent=4' "https://cloud.seafile.com/api/v2.1/repos/d4f596ed-09ea-4ac6-8d59-12acbd089097/trash/"

```

```
{
    "scan_stat": null,
    "data": [],
    "more": false
}

```

**Errors**

* 400 path invalid.
* 403 Permission denied.
* 404 Library not found.
* 500 Internal Server Error

## Library Commit

### Get Library Commit Info

**GET** <https://cloud.seafile.com/api/v2.1/repos/{repo_id}/commits/{commit_id}>

**Request parameters**

* `repo_id`
* `commit_id`

**Sample request**

```
curl -H 'Authorization:Token 825d6877dc3474d952b1f5b0654aeaeb90c48281' -H 'Accept: application/json; indent=4' "https://cloud.seafile.com/api/v2.1/repos/8756ca9d-e3ed-44da-b43e-1bfd165b2377/commits/28c15cca4a8dbd5135fbe3ae75c3df7f5f355484/"

```

**Sample response**

```
{
    "commit_info": {
        "description": "Added or modified \"1.md\" and 2 more files.\nDeleted \"default.jpeg\".\nRenamed \"123.umind\" and 1 more files.\nAdded \"789\" and 1 more directories.\nRemoved directory \"456\".\n",
        "creator_name": "lian-name",
        "creator_email": "lian@lian.com",
        "device_name": "lian mac pro work",
        "time": "2020-03-11T10:17:03+08:00",
        "creator_contact_email": "lian@lian.com"
    },
    "commit_diffs": [
        {
            "op_type": "renamed",
            "path": "/123/123.umind",
            "new_path": "/123/123.umind copy"
        },
        {
            "op_type": "renamed",
            "path": "/d0efd88ejw1f6vqsjmjh9j20c846i4i6.jpg",
            "new_path": "/123.jpg"
        },
        {
            "op_type": "modified",
            "path": "/123/1.md",
            "new_path": ""
        },
        {
            "op_type": "deldir",
            "path": "/123/456",
            "new_path": ""
        },
        {
            "op_type": "newdir",
            "path": "/123/789",
            "new_path": ""
        },
        {
            "op_type": "newdir",
            "path": "/abd",
            "new_path": ""
        },
        {
            "op_type": "removed",
            "path": "/default.jpeg",
            "new_path": ""
        },
        {
            "op_type": "new",
            "path": "/departments copy.md",
            "new_path": ""
        },
        {
            "op_type": "modified",
            "path": "/info.md",
            "new_path": ""
        }
    ]
}

```

**Errors**

* 404 Library not found.
* 404 Commit not found.
* 403 Permission denied.

<https://cloud.seafile.com/api2/repos/>


