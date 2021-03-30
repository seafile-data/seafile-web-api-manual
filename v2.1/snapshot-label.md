# Snapshot Label

## Get Snapshot Label

**GET** https://cloud.seafile.com/api/v2.1/revision-tags/tag-names/

**Sample request**

Sample for get snapshot label

```
curl -H 'Authorization: Token 88aaa1e6fe35d0444868b4c67f8ca1766cf82f55' -H 'Accept: application/json; indent=4' http://cloud.seafile.com/api/v2.1/revision-tags/tag-names/
```

**Sample response**

```
[
    "q1",
    "qwe",
    "qwe",
    "qwe_-.12",
    "qwe_-1.",
    "r",
    "r",
    "v3",
    "\u4e2d\u6587",
    "\u82f1\u6587"
]
```

## Create Snapshot Label

**POST** https://cloud.seafile.com/api/v2.1/revision-tags/tagged-items/

**Request parameters**
* repo_id
* commit_id, optional
* tag_names

**Sample request**

Sample for create snapshot label.

```
curl -d "repo_id=7377c95d-b303-4914-a555-306651cc4cbf&commit_id=4c03938da11e83d6c1d3e8ff469e92f46a80eeaf&tag_names=v2.1,v2.2" -H 'Authorization: Token 88aaa1e6fe35d0444868b4c67f8ca1766cf82f55' -H 'Accept: application/json; indent=4' http://cloud.seafile.com/api/v2.1/revision-tags/tagged-items/
```

**Sample response**

```
{
    "revisionTags": [
        {
            "tag": "v2.1",
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
        },
        {
            "tag": "v2.2",
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
}
```

**Errors**

* 400 repo_id/commit_id/tag_names invalid.
* 403 Permission denied(need rw permission).

## Update Snapshot Label

**PUT** https://cloud.seafile.com/api/v2.1/revision-tags/tagged-items/

**Request parameters**
* repo_id
* commit_id(default is head commit if commit_id is empty)
* tag_names

**Sample request**

Sample for update snapshot label.

```
curl -X PUT -d "repo_id=7377c95d-b303-4914-a555-306651cc4cbf&commit_id=4c03938da11e83d6c1d3e8ff469e92f46a80eeaf&tag_names=v3" -H 'Authorization: Token 88aaa1e6fe35d0444868b4c67f8ca1766cf82f55' -H 'Accept: application/json; indent=4' http://cloud.seafile.com/api/v2.1/revision-tags/tagged-items/
```

**Sample response**

```
{
    "revisionTags": [
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
}
```

**Errors**

* 400 repo_id/commit_id/tag_names invalid.
* 403 Permission denied(need rw permission).

## Delete Snapshot Label
**Delete** https://cloud.seafile.com/api/v2.1/revision-tags/tagged-items/

**Request parameters**
* repo_id
* tag_name

**Sample request**

Sample for update snapshot label.

```
curl -X DELETE -H 'Authorization: Token 88aaa1e6fe35d0444868b4c67f8ca1766cf82f55' -H 'Accept: application/json; indent=4' -sS 'http://cloud.seafile.com/api/v2.1/revision-tags/tagged-items/?repo_id=7377c95d-b303-4914-a555-306651cc4cbf&tag_names=v3'
```

**Sample response**

```
{}
```

**Errors**

* 400 repo_id/tag_names invalid.
* 403 Permission denied(need rw permission).

