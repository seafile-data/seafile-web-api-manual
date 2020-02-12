# Default Libraries

## Get User Default Library

Available for Seafile v6.0.9+

**GET** https://cloud.seafile.com/api/v2.1/admin/default-library/{user_email}

**Sample request**

    curl -H 'Authorization: Token 024692f8411a656baa2cc2d5ed4cd46177b3b3d0' "https://cloud.seafile.com/api/v2.1/admin/default-library/?user_email=foo@foo.com"

**Sample response**

```
{
    "repo_id":"9e58655f-d2a2-4df9-baa2-5ca50698ad98",
    "exists":true,
    "user_email":"lian@lian.com"
}
```

**Errors**

* 400 user_email invalid.
* 404 User not found.
* 403 Permission error, only administrator can perform this action.
* 500 Internal Server Error


## Create User Default Library

Available for Seafile v6.0.9+

**POST** https://cloud.seafile.com/api/v2.1/admin/default-library/

**Sample request**

    curl -d "user_email=foo@foo.com" -H 'Authorization: Token 024692f8411a656baa2cc2d5ed4cd46177b3b3d0' "https://cloud.seafile.com/api/v2.1/admin/default-library/"

**Sample response**

```
{
    "repo_id":"9e58655f-d2a2-4df9-baa2-5ca50698ad98",
    "exists":true,
    "user_email":"lian@lian.com"
}
```

**Errors**

* 400 user_email invalid.
* 403 Permission error, only administrator can perform this action.
* 403 Permission error, user can not create library.
* 404 User not found.
* 500 Internal Server Error
