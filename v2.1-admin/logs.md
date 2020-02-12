# Logs

The APIs is only supported in pro edition.

## Get Login Log

**GET** <https://cloud.seafile.com/api/v2.1/admin/logs/login/?start=2016-03-20&end=2016-03-31>

**Sample request**

```
curl -H "Authorization: Token f651b0fb62978961b68e1bf8d740647d2fc4be8" -H 'Accept: application/json; indent=4' "https://demo.seafile.top/api/v2.1/admin/logs/login/?start=2019-07-30&end=2019-07-31"

```

**Sample response**

```
[
    {
        'email': u'lian@lian.com',
        'login_ip': u'192.168.1.124',
        'name': u'lian',
        'login_time': '2016-03-31T14:42:23+08:00'
    },
    {
        'email': u'org@org.com',
        'login_ip': u'192.168.1.124',
        'name': u'org',
        'login_time': '2016-03-31T14:39:08+08:00'
    }
]

```

**Errors**

* 400 start or end date invalid.
* 403 Feature disabled.

## Get File Access Log

**GET** <https://cloud.seafile.com/api/v2.1/admin/logs/file-audit/?start=2016-03-20&end=2016-03-31>

**Sample request**

```
curl -H "Authorization: Token f651b0fb62978961b68e1bf8d740647d2fc4be8" -H 'Accept: application/json; indent=4' "https://demo.seafile.top/api/v2.1/admin/logs/file-audit/?start=2019-07-30&end=2019-07-31"

```

**Sample response**

```
[
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
    {
        "ip": "58.20.58.17",
        "repo_owner_email": "demo@seafile.com",
        "user_contact_email": "demo@seafile.com",
        "repo_id": "7d911e46-e81e-4cd3-a1a7-6f86d0d0678b",
        "repo_owner_name": "seafile()",
        "repo_owner_contact_email": "demo@seafile.com",
        "time": "2019-07-31T15:55:10+08:00",
        "etype": "file-download-api",
        "user_name": "seafile()",
        "file_path": "/\u5c31.md",
        "user_email": "demo@seafile.com",
        "repo_name": "\u53ef\u80fd\u5462"
    }
]

```

**Errors**

* 400 start or end date invalid.
* 403 Feature disabled.

## Get File Update Logs

**GET** <https://cloud.seafile.com/api/v2.1/admin/logs/file-update/?start=2016-03-20&end=2016-03-31>

**Sample request**

```
curl -H "Authorization: Token f651b0fb62978961b68e1bf8d740647d2fc4be8" -H 'Accept: application/json; indent=4' "https://demo.seafile.top/api/v2.1/admin/logs/file-update/?start=2019-07-30&end=2019-07-31"

```

**Sample response**

```
[
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
    {
        "commit_id": "59576aba2ee33a99f73f209f7e87bbd51143a263",
        "repo_owner_email": "demo@seafile.com",
        "user_contact_email": "demo@seafile.com",
        "repo_id": "7d911e46-e81e-4cd3-a1a7-6f86d0d0678b",
        "repo_owner_name": "seafile()",
        "file_operation": "Added \"C400002fePdX0zcfpQ (1).m4a\".",
        "repo_owner_contact_email": "demo@seafile.com",
        "time": "2019-07-31T14:58:31+08:00",
        "user_name": "seafile()",
        "user_email": "demo@seafile.com",
        "repo_name": "\u53ef\u80fd\u5462"
    }
]

```

**Errors**

* 400 start or end date invalid.
* 403 Feature disabled.

## Get Permission Audit Logs

**GET** <https://cloud.seafile.com/api/v2.1/admin/logs/perm-audit/?start=2016-03-20&end=2016-03-31>

**Sample request**

```
curl -H "Authorization: Token f651b0fb62978961b68e1bf8d740647d2fc4be8" -H 'Accept: application/json; indent=4' "https://demo.seafile.top/api/v2.1/admin/logs/perm-audit/?start=2019-07-30&end=2019-07-31"

```

**Sample response**

```
[
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
    {
        'etype': u'add-repo-perm',
        'file_path': u'/folder',
        'from_email': u'org3@org3.com',
        'from_name': u'org3',
        'permission': u'rw',
        'repo_id': u'a84544e5-0b84-459d-b1e6-0399dabc76a0',
        'repo_name': '',
        'time': '2016-03-31T06:21:53+08:00',
        'to': u'777'
    }
]

```

**Errors**

* 400 start or end date invalid.
* 403 Feature disabled.


