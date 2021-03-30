# Server Info

## Get Server Information

**GET** <https://cloud.seafile.com/api2/server-info>

_Note_:

* No authentication required.
* Added in seafile community edition server `4.0.5` or pro edition server `4.0.3`

**Sample request**

```
curl https://cloud.seafile.com/api2/server-info/

```

**Sample response**

Sample response from a seafile community edition server:

```
{
    "version": "4.0.6",
    "encrypted_library_version": 2，
    "features": [
    "seafile-basic",
    ]
}

```

Sample response from a seafile pro edition server:

```
{
    "version": "4.0.6",
    "encrypted_library_version": 2，
    "features": [
    "seafile-basic",
    "seafile-pro",
    "office-preview",
    "file-search"
    ]
}

```


