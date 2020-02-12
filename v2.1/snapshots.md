# Snapshot

## List Items in Directory of a Snapshot

_Note_: Used in Snapshot and Trash.

**GET**: <https://cloud.seafile.com/api/v2.1/repos/{repo_id}/commits/{commit_id}/dir/>

**Request parameters**

* path

**Sample request**

```
curl -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d9b477fd' https://cloud.seafile.com/api/v2.1/repos/dae8cecc-2359-4d33-aa42-01b7846c4b32/commits/23f6c39d7b0640cd226bcfcba0a25a32f5ed5f6a/dir/?path=%2F

```

**Sample response**

```
{
    "dirent_list": [
        {
            "type": "dir",
            "name": "second-folder",
            "parent_dir": "/first-folder/",
            "obj_id": "ba2fbc1bf1e9653e60e9880c75bdb89e5ae182c6"
        },
        {
            "obj_id": "0000000000000000000000000000000000000000",
            "type": "file",
            "name": "second-file.md",
            "parent_dir": "/first-folder/",
            "size": 0
        }
    ]
}

```

**Errors**

* 403 Permission denied.
* 404 Library not found.
* 404 Folder not found.
* 404 Commit not found.

## Revert library to a Snapshot

_Note_: Only library owner can revert.

**POST**: <https://cloud.seafile.com/api/v2.1/repos/{repo_id}/commits/{commit_id}/revert/>

**Sample request**

```
curl -X POST -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d9b477fd' https://cloud.seafile.com/api/v2.1/repos/dae8cecc-2359-4d33-aa42-01b7846c4b32/commits/23f6c39d7b0640cd226bcfcba0a25a32f5ed5f6a/revert/

```

###### Sample response

```
{
    "success": true
}

```

**Errors**

* 403 Permission denied.
* 404 Library not found.
* 404 Commit not found.


