# Devices

## List Devices

**GET** https://cloud.seafile.com/api2/devices/

**Sample request**

    curl -H "Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api2/devices/

**Sample response**

```
[
    {
        "synced_repos": [
            {
                "repo_id": "47945b31-dedb-4b92-a048-32bf825595ce",
                "sync_time": 1458008928,
                "repo_name": "wopi"
            },
            {
                "repo_id": "78c620ee-2989-4427-8eff-7748f4fbebc0",
                "sync_time": 1457943466,
                "repo_name": "lib-of-lian"
            }
        ],
        "last_accessed": "2016-03-15T10:28:48+08:00",
        "device_name": "lian",
        "platform_version": "",
        "platform": "linux",
        "user": "lian@lian.com",
        "key": "99abe1a7cc7d614db0bfa19db81e42ef675abe4f",
        "client_version": "5.0.0",
        "last_login_ip": "192.168.1.16",
        "device_id": "be10980211752515053bf9036a13139375de0cc8"
    },
    {
        "last_accessed": "2016-03-15T13:59:51+08:00",
        "device_name": "PLK-AL10",
        "platform_version": "5.0.2",
        "platform": "android",
        "user": "lian@lian.com",
        "key": "067051c94163ed193f2131d48c61882daa7cb238",
        "client_version": "2.0.3",
        "last_login_ip": "192.168.1.208",
        "device_id": "4a0d62c1f27b3b74"
    }
]
```

**Errors**

* 401 UNAUTHORIZED

## Unlink Device

**DELETE** https://cloud.seafile.com/api2/devices/

**Request parameters**

* platform
* device_id

**Sample request**

    curl -X DELETE -d "platform=linux&device_id=be10980211752515053bf9036a13139375de0cc8" -H "Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api2/devices/

**Sample response**

    {"success": true}

**Errors**

* 400 platform invalid
* 400 device_id invalid

