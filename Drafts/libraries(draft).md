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
  * `org`, get public libraires.

NOTE: If no `type` parameter contained in the url, this api will return all libraries user can access.

**Sample request for get all libraries I can accessed**

```
curl -H 'Authorization: Token 24fd3c026886e3121b2ca630805ed425c272cb96' -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api2/repos/

```

**Sample response for get all libraries I can accessed**

```
[
    {
        "storage_id": "old_version_id",
        "root": "",
        "modifier_email": "1@1.com",
        "name": "lib-of-1",
        "permission": "rw",
        "size_formatted": "0 bytes",
        "storage_name": "旧版本",
        "virtual": false,
        "mtime_relative": "<time datetime=\"2018-07-18T11:34:36\" is=\"relative-time\" title=\"Wed, 18 Jul 2018 11:34:36 +0800\" >59 seconds ago</time>",
        "head_commit_id": "a0727e27e73a513c281bd7f3e78bcd65767d095c",
        "encrypted": false,
        "version": 1,
        "mtime": 1531884876,
        "owner": "1@1.com",
        "modifier_contact_email": "1@1.com",
        "type": "repo",
        "id": "1f6a3ed4-a53c-4f02-a688-eac373347127",
        "modifier_name": "1",
        "size": 0
    },
    {
        "owner_nickname": "name of lian",
        "modifier_email": "lian@lian.com",
        "name": "lib-of-lian",
        "share_type": "personal",
        "permission": "rw",
        "size_formatted": "5.3 GB",
        "root": "",
        "mtime_relative": "<time datetime=\"2018-07-18T11:32:06\" is=\"relative-time\" title=\"Wed, 18 Jul 2018 11:32:06 +0800\" >3 minutes ago</time>",
        "is_admin": false,
        "head_commit_id": "7ea21638dae358f3b75f5236f083f846c91ef2e3",
        "encrypted": false,
        "version": 1,
        "mtime": 1531884726,
        "owner": "lian@lian.com",
        "modifier_contact_email": "lian-contact@email.com",
        "type": "srepo",
        "id": "d4f596ed-09ea-4ac6-8d59-12acbd089097",
        "modifier_name": "name of lian",
        "size": 5655202974
    },
    {
        "share_from_name": "name of lian",
        "modifier_email": "lian@lian.com",
        "name": "seacloud.cc.124",
        "share_from": "lian@lian.com",
        "permission": "rw",
        "share_from_contact_email": "lian-contact@email.com",
        "encrypted": false,
        "root": "",
        "groupid": 70,
        "version": 1,
        "head_commit_id": "d96bc7919934facec5f11d4dbe5215284e7a438a",
        "mtime": 1531812196,
        "owner": "group-of-lian",
        "modifier_contact_email": "lian-contact@email.com",
        "group_name": "group-of-lian",
        "type": "grepo",
        "id": "f26331a8-8acd-4c3d-9c73-352c595c36c8",
        "modifier_name": "name of lian",
        "size": 475709269
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
        "storage_id": "old_version_id",
        "root": "",
        "modifier_email": "1@1.com",
        "name": "lib-of-1",
        "permission": "rw",
        "size_formatted": "0 bytes",
        "storage_name": "旧版本",
        "virtual": false,
        "mtime_relative": "<time datetime=\"2018-07-18T11:34:36\" is=\"relative-time\" title=\"Wed, 18 Jul 2018 11:34:36 +0800\" >59 seconds ago</time>",
        "head_commit_id": "a0727e27e73a513c281bd7f3e78bcd65767d095c",
        "encrypted": false,
        "version": 1,
        "mtime": 1531884876,
        "owner": "1@1.com",
        "modifier_contact_email": "1@1.com",
        "type": "repo",
        "id": "1f6a3ed4-a53c-4f02-a688-eac373347127",
        "modifier_name": "1",
        "size": 0
    },
]

```

### Create Library

**POST** <https://cloud.seafile.com/api2/repos/>

**Request parameters**

* name
* desc (defaults to "new repo")
* passwd (needed by encrypt library)

**Sample request**

```
curl -v -d "name=foo&desc=new library" -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd' -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api2/repos/

```

**Sample response**

```
{
"encrypted": "",
"enc_version": 0,
"repo_id": "f15811fd-5c19-412c-b143-2ac83f352290",
"magic": "",
"relay_id": "c5e41170db250ea497075e2911104faf0105b7fb",
"repo_version": 1,
"relay_addr": "cloud.seafile.com",
"token": "c1f3defe9ba408cd7964427ec276843e9d10c23b",
"relay_port": "10001",
"random_key": "",
"email": "user@mail.com",
"repo_name": "foo"
}

```

**Success**

   Response code 200 and newly created library information are returned.

**Errors**

* 400 Library name missing.
* 520 Operation failed.

### <a id="delete-library"></a>Delete Library

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

### Get Library Info

**GET** <https://cloud.seafile.com/api2/repos/{repo-id}/>

**Request parameters**

* repo-id

**Sample request**

```
curl -G -H 'Authorization: Token 24fd3c026886e3121b2ca630805ed425c272cb96' -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api2/repos/632ab8a8-ecf9-4435-93bf-f495d5bfe975/

```

**Sample response**

```
{
"encrypted": false,
"password_need": null,
"mtime": null,
"owner": "self",
"id": "632ab8a8-ecf9-4435-93bf-f495d5bfe975",
"size": 1356155,
"name": "org",
"root": "b5227040de360dd22c5717f9563628fe5510cbce",
"desc": "org file",
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
* show_days, default 0.
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
* keep_days, default 0.

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


