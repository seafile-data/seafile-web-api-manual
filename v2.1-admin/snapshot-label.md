# Snapshot Label

## Get Snapshots by Label

**GET** https://cloud.seafile.com/api/v2.1/admin/revision-tags/tagged-items/

**Request parameters**
* user, optional
* repo_id, optional
* tag_name, optional
* tag_contains, optional

**Sample request**

Sample for get snapshots by label

```
curl -H 'Authorization: Token 88aaa1e6fe35d0444868b4c67f8ca1766cf82f55' -H 'Accept: application/json; indent=4' http://cloud.seafile.com/api/v2.1/admin/revision-tags/tagged-items/?repo_id=7377c95d-b303-4914-a555-306651cc4cbf&tag_contains=v
```

**Sample response**

```
[
    {
        "tag": "v3",
        "tag_creator": "foo@foo.com",
        "revision": {
            "commit_id": "4c03938da11e83d6c1d3e8ff469e92f46a80eeaf",
            "repo_id": "7377c95d-b303-4914-a555-306651cc4cbf",
            "contact_email": "foo@foo.com",
            "name": "foo",
            "time": "2017-09-13T15:20:54+08:00",
            "link": "/repo/history/view/7377c95d-b303-4914-a555-306651cc4cbf/?commit_id=4c03938da11e83d6c1d3e8ff469e92f46a80eeaf",
            "email": "foo@foo.com",
            "description": "Added \"ca (1).js\"."
        }
    }
]
```