# logs

## List File Access Logs

**GET** /api/v2.1/org/admin/logs/file-access/

**Sample request**

```
curl -H "Authorization: Token 3f1e23157c3a1fd740e9dc1c5d748929fe319b95" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api/v2.1/org/admin/logs/file-access/
```

**Sample response**

```
{
    "log_list": [
        {
            "ip": "1.68.7.249",
            "repo_owner_email": "demo@seafile.com",
            "user_contact_email": "demo@seafile.com",
            "repo_id": "7d911e46-e81e-4cd3-a1a7-6f86d0d0678b",
            "repo_owner_name": "seafile()",
            "repo_owner_contact_email": "demo@seafile.com",
            "time": "2019-07-31T14:58:39+08:00",
            "etype": "file-download-web",
            "user_name": "seafile()",
            "file_path": "/C400002fePdX0zcfpQ (1).m4a",
            "user_email": "demo@seafile.com",
            "repo_name": "\u53ef\u80fd\u5462"
        },
    ],
    "page": 1,
    "page_next": false
}
```

## List File Update Logs

**GET** /api/v2.1/org/admin/logs/file-update/

**Sample request**

```
curl -H "Authorization: Token 3f1e23157c3a1fd740e9dc1c5d748929fe319b95" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api/v2.1/org/admin/logs/file-update/
```

**Sample response**

```
{
    "log_list": [
        {
            "commit_id": "212ec59f50a49763b80ae8466776243a27ec77ce",
            "repo_owner_email": "demo@seafile.com",
            "user_contact_email": "demo@seafile.com",
            "repo_id": "7d911e46-e81e-4cd3-a1a7-6f86d0d0678b",
            "repo_owner_name": "seafile()",
            "file_operation": "Added \"\u5c31.md\"",
            "repo_owner_contact_email": "demo@seafile.com",
            "time": "2019-07-31T14:58:13+08:00",
            "user_name": "seafile()",
            "user_email": "demo@seafile.com",
            "repo_name": "\u53ef\u80fd\u5462"
        },
    ],
    "page": 1,
    "page_next": false
}
```

## List Library Permission Logs

**GET** /api/v2.1/org/admin/logs/repo-permission/

**Sample request**

```
curl -H "Authorization: Token 3f1e23157c3a1fd740e9dc1c5d748929fe319b95" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api/v2.1/org/admin/logs/repo-permission/
```

**Sample response**

```
{
    "log_list": [
        {
            'etype': u'add-repo-perm',
            'file_path': u'/folder',
            'from_email': u'org3@org3.com',
            'from_name': u'org3',
            'permission': u'rw',
            'repo_id': u'a84544e5-0b84-459d-b1e6-0399dabc76a0',
            'repo_name': '',
            'time': '2016-03-31T06:21:50+08:00',
            'to': u'org@org.com'
        },
    ],
    "page": 1,
    "page_next": false
}
```
