# libraries

## List Libraries

**GET** /api/v2.1/org/{org_id}/admin/repos/

**Sample request**

```
curl -H "Authorization: Token 3f1e23157c3a1fd740e9dc1c5d748929fe319b95" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api/v2.1/org/12/admin/repos/
```

**Sample response**

```
{
    "page_next": false,
    "page": 1,
    "repo_list": [
        {
            "repo_id": "f707b2ee-241f-4322-95c0-4135b47e6a85",
            "encrypted": false,
            "owner_email": "o2@o2.com",
            "is_department_repo": false,
            "owner_name": "o2",
            "group_id": "",
            "repo_name": "My Library"
        }
    ]
}
```

## Transfer Library

**PUT** /api/v2.1/org/{org_id}/admin/repos/{repo_id}/

**Request Parameters**

- email: transfer to

**Sample request**

```
curl -X PUT -d "email=o2a@o2a.com" -H "Authorization: Token 3f1e23157c3a1fd740e9dc1c5d748929fe319b95" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api/v2.1/org/12/admin/repos/f707b2ee-241f-4322-95c0-4135b47e6a85/
```

**Sample response**

```
{
	"repo_id":"f707b2ee-241f-4322-95c0-4135b47e6a85",
    "encrypted":false,
    "owner_email":"o2a@o2a.com",
    "is_department_repo":false,
    "owner_name":"o2a",
    "group_id":"",
    "repo_name":
    "My Library"
}
```

## Delete Library

**DELETE** /api/v2.1/org/{org_id}/admin/repos/{repo_id}/

**Sample request**

```
curl -X DELETE -H "Authorization: Token 3f1e23157c3a1fd740e9dc1c5d748929fe319b95" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api/v2.1/org/12/admin/repos/f707b2ee-241f-4322-95c0-4135b47e6a85/
```

**Sample response**

```
{
    "success": true
}
```
