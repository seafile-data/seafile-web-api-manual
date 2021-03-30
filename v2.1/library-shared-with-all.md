# Shared with All Libraries

## Create Shared with All Library

**POST** https://cloud.seafile.com/api2/repos/public/

**Request parameters**

* name
* permission, `r` or `rw`, default `r`.
* passwd (optional).

**Sample request**, create an encrypted public repo with `rw` permission

    curl -X POST -d "name=test-public-repo&permission=rw&passwd=password" -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d9b477fd' -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api2/repos/public/

**Sample response**

```
{
    "owner_nickname": "lian",
    "permission": "rw",
    "encrypted": true,
    "mtime_relative": "<time datetime=\"2016-05-31T12:01:49\" is=\"relative-time\" title=\"Tue, 31 May 2016 12:01:49 +0800\" >1 second ago</time>",
    "mtime": 1464667309,
    "owner": "lian@lian.com",
    "id": "6553fd8b-bf3e-41ad-a481-90c8523d3b4a",
    "size": 0,
    "name": "test-public-repo",
    "desc": "",
    "size_formatted": "0 bytes"
}
```

**Errors**

* 400 Library name is required.
* 400 Invalid permission
* 403 You do not have permission to create library.
* 403 NOT allow to create encrypted library.

## Set Exist Lib as Shared with All Library

**PUT** https://cloud.seafile.com/api2/shared-repos/{repo-id}/?share_type=public

**Request parameters**

* repo_id
* share_type, must be `public`
* permission, `r` or `rw`.

**Sample request**, create an encrypted public repo with `rw` permission

    curl -X PUT -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d9b477fd' -H 'Accept: application/json; indent=4' 'https://cloud.seafile.com/api2/shared-repos/2deffbac-d7be-4ace-b406-efb799083ee9/?share_type=public&permission=rw'

**Sample response**

```
success
```

**Errors**

* 400 Permission need to be rw or r.
* 403 You do not have permission to share library.
* 500 Failed to share library to public.

## Remove Shared with All Library

**DELETE** https://cloud.seafile.com/api2/shared-repos/{repo-id}/?share_type=public

**Request parameters**

* repo-id
* share_type

**Sample request**

    curl -X DELETE -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d9b477fd' -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api2/shared-repos/dae8cecc-2359-4d33-aa42-01b7846c4b32/?share_type=public

**Success**

    "success"

**Errors**

* 400 Share type is required.
* 400 Share type can only be personal or group or public.
* 403 You do not have permission to unshare library.

