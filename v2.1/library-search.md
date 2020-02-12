# Library Search

## Search Library By Name

**GET** https://cloud.seafile.com/api2/repos/

**Request parameters**

* type (optional)
* nameContains (optional)

**Sample request**

    Search the all library

    curl -H 'Authorization: Token 24fd3c026886e3121b2ca630805ed425c272cb96' -sS 'https://cloud.seafile.com/api2/repos/?nameContains=T'

**Sample response**

    [
        {
            "root": "",
            "modifier_email": null,
            "name": "TEST",
            "permission": "rw",
            "size_formatted": "424.6 MB",
            "virtual": false,
            "mtime_relative": "<time datetime=\"2017-07-04T08:30:33\" is=\"relative-time\" title=\"Tue, 4 Jul 2017 08:30:33 +0000\" >2017-07-04</time>",
            "head_commit_id": "05418e616a5325b3f0ccfaf7d4c54c803b8168de",
            "encrypted": false,
            "version": 1,
            "mtime": 1499157033,
            "owner": "admin@admin.com",
            "modifier_contact_email": "",
            "type": "repo",
            "id": "a9025464-2c72-4b9c-9cdd-6de62e56f696",
            "modifier_name": "",
            "size": 445243555
        }
    ]

**Sample request**

    Search the specified library

    curl -H 'Authorization: Token 24fd3c026886e3121b2ca630805ed425c272cb96' -sS 'https://cloud.seafile.com/api2/repos/?type=mime&nameContains=T'

**Sample response**

    []


**Errors**

None
