# Library Sync

## Fetch library Sync info

**GET** <https://cloud.seafile.com/api2/repos/{repo-id}/download-info/>

**Request parameters**

* repo-id

**Sample request**

```
curl -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d9b477fd' -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api2/repos/fd9d4541-0865-4b2d-9523-8070c8d5d59f/download-info/

```

**Sample response**

```
{
    "repo_size": 0,
    "repo_size_formatted": "0 bytes",
    "repo_id": "fd9d4541-0865-4b2d-9523-8070c8d5d59f",
    "magic": "",
    "permission": "rw", # or "r", "cloud-edit", "preview"
    "encrypted": "",
    "repo_desc": "私人资料库",
    "random_key": "",
    "relay_id": "85af473aba8d0967d32e609f66d3cccbaa92f49c",
    "enc_version": 0,
    "mtime_relative": "<time datetime=\"2019-07-15T03:29:35\" is=\"relative-time\" title=\"Mon, 15 Jul 2019 03:29:35 +0000\" >8 days ago</time>",
    "relay_addr": "127.0.0.1",
    "token": "5385e7f3d525669f7f6b0ec502820b26273758ca",
    "repo_version": 1,
    "head_commit_id": "c07704ecb0f91381bfa4f89b544b26e1e52e01eb",
    "relay_port": 10001,
    "mtime": 1563161375,
    "salt": "",
    "email": "foo@foo.com",
    "repo_name": "私人资料库"
}

```


