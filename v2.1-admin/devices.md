# Devices

## Get Desktop Devices

Get first page (50 records per page) of desktop devices.

**GET** https://cloud.seafile.com/api/v2.1/admin/devices/?platform=desktop&page=1&per_page=50

**Sample request**

    curl -H "Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api/v2.1/admin/devices/?platform=desktop&page=1&per_page=50

**Sample response**

```
[
    {'has_next_page': False},
    [
        {
            'last_accessed': '2016-04-11T18:24:29+08:00',
            'last_login_ip': u'192.168.1.210',
            'platform': u'linux',
            'user': u'1@1.com',
            'client_version': u'2.0.4',
            'device_name': u'PLK-AL10',
            'device_id': u'4a0d62c1f27b3b74'
        }
    ]
]
```

**Errors**

* 403 Permission error, only administrator can perform this action

## Get Mobile Devices

Get first page (50 records per page) of mobile devices.

**GET** https://cloud.seafile.com/api/v2.1/admin/devices/?platform=mobile&page=1&per_page=50

**Sample request**

    curl -H "Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api/v2.1/admin/devices/?platform=mobile&page=1&per_page=50

**Sample response**

```
[
    {'has_next_page': False},
    [
        {
            'last_accessed': '2016-04-11T18:24:29+08:00',
            'last_login_ip': u'192.168.1.210',
            'platform': u'ios',
            'user': u'1@1.com',
            'client_version': u'2.0.4',
            'device_name': u'PLK-AL10',
            'device_id': u'4a0d62c1f27b3b74'
        }
    ]
]
```

**Errors**

* 403 Permission error, only administrator can perform this action

## Unlink User Device

**DELETE** https://cloud.seafile.com/api/v2.1/admin/devices/

**Request parameters**

* platform
* device_id
* user

**Sample request**

    curl -X DELETE -d "platform=linux&device_id=be10980211752515053bf9036a13139375de0cc8&user=1@1.com" -H "Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api/v2.1/admin/devices/

**Sample response**

    {"success": true}

**Errors**

* 400 platform invalid
* 400 device_id invalid
* 400 user invalid
* 500 Internal Server Error

## Get Device Errors

This api is only supported in pro edition.

**GET** https://cloud.seafile.com/api/v2.1/admin/device-errors/

**Sample request**

    curl -H "Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api/v2.1/admin/device-errors/

**Sample response**

```
[
    {
        'repo_id': u'47945b31-dedb-4b92-a048-32bf825595ce',
        'device_ip': u'192.168.1.124',
        'error_time': '2016-04-13T17:49:11+08:00',
        'device_name': u'lian-ubuntu-1404-64',
        'email': u'1@1.com',
        'client_version': u'5.0.6',
        'error_msg': u'No permission.',
        'repo_name': u'wopi'
    }
]
```

**Errors**

* 403 Feature disabled.
* 500 Internal Server Error

## Clean Device Errors

This api is only supported in pro edition.

**DELETE** https://cloud.seafile.com/api/v2.1/admin/device-errors/

**Sample request**

    curl -X DELETE -H "Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api/v2.1/admin/device-errors/

**Sample response**

```
{"success":true}
```

**Errors**

* 403 Feature disabled.
* 500 Internal Server Error