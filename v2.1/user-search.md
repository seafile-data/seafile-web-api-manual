# User Search

## Search User

**GET** https://cloud.seafile.com/api2/search-user/?q=foo

**Request parameters**

* q

**Sample request**

    curl -H "Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api2/search-user/?q=foo

**Sample response**

```
[
    {'avatar_url': 'https://cloud.seafile.com/media/avatars/default.png',
      'contact_email': u'foo@foo.com',
      'email': u'foo@foo.com',
      'name': 'foo'},
    {'avatar_url': 'https://cloud.seafile.com/media/avatars/default.png',
     'contact_email': u'foo-bar@foo-bar.com',
     'email': u'foo-bar@foo-bar.com',
     'name': 'foo-bar'}
]
```

**Errors**

* 400 Argument missing.
* 403 Guest user can not use global address book.
