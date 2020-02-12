# Department Libraries

## Add Deparment Library

**POST** <http://192.168.1.113:8000/api/v2.1/admin/groups/{group_id}/group-owned-libraries/>

**Request parameters**

* `group_id`
* `repo_name`
* `password`
* `permission`, default `rw`.

**Sample request**

```
curl -d "repo_name=group-owned-repo-4&permission=r" -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd' "http://192.168.1.113:8000/api/v2.1/amdin/groups/53/group-owned-libraries/"

```

**sample response**

```
{
    "repo_id": "9bc59af9-265e-4110-a0e2-619450a5cb35",
    "permission": "r",
    "encrypted": false,
    "owner_email": "53@seafile_group",
    "mtime": "2018-04-23T17:25:37+08:00",
    "repo_name": "group-owned-repo-4",
    "size": 0
}

```

**Errors**

* 400 repo_name/permission invalid.
* 403 NOT allow to create encrypted library..
* 403 Permission denied.
* 403 No group quota.
* 404 Group not found.

## Delete Deparment Library

**DELETE** <http://192.168.1.113:8000/api/v2.1/admin/groups/{group_id}/group-owned-libraries/{repo_id}/>

**Request parameters**

* `group_id`
* `repo_id`

**Sample request**

```
curl -X DELETE -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd' "http://192.168.1.113:8000/api/v2.1/admin/groups/53/group-owned-libraries/9bc59af9-265e-4110-a0e2-619450a5cb35/"

```

**sample response**

```
{"success":true}

```

**Errors**

* 403 Permission denied.
* 404 Group/Library not found.
* 500 Internal Server Error

## Modify Department Library Sub-Folder Permission

**PUT** <http://192.168.1.113:8000/api/v2.1/admin/groups/{group_id}/group-owned-libraries/{repo_id}/>

**Request parameters**

* `group_id`
* `repo_id`
* `path`, path of sub folder.
* `permission`: `r` or `rw`.

**Sample request**

```
curl -X PUT -d "path=/tmp/&permission=r" -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd' "http://192.168.1.113:8000/api/v2.1/admin/groups/53/group-owned-libraries/9bc59af9-265e-4110-a0e2-619450a5cb35/"

```

**sample response**

```
{"success":true}
```

**Errors**

* 400 path/permission invalid.
* 403 Permission denied.
* 404 Group/Library/Folder not found.



