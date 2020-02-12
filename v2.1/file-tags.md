# file-tags

File tags are selected from the tag set of a library. To add a new tag to a file, you should first add the tag name and color to the library.

## List All Tags of a Library

**GET** <https://cloud.seafile.com/api/v2.1/repos/{repo_id}/repo-tags/>

**request parameters**

* repo_id

**Sample request**

```
curl -H "Authorization: Token 05b05e30ee979e333ff33a437988820494fb0afd"  "https://cloud.seafile.com/api/v2.1/repos/cf7ab8ca-ae38-4662-99c8-7fcafd7037de/repo-tags/"

```

**Sample response**

```
{
    "repo_tags": [
        {
            "tag_color": "#FFD43B",
            "tag_name": "new",
            "repo_id": "cf7ab8ca-ae38-4662-99c8-7fcafd7037de",
            "repo_tag_id": 1,
            "files_count": 1
        },
        {
            "tag_color": "#FFA8A8",
            "tag_name": "deprecated",
            "repo_id": "cf7ab8ca-ae38-4662-99c8-7fcafd7037de",
            "repo_tag_id": 2,
            "files_count": 1
        }
    ]
}

```

## Add a Tag to a Library

**POST** <https://cloud.seafile.com/api/v2.1/repos/{repo_id}/repo-tags/>

**request parameters**

* repo_id
* name, tag name
* color, tag color

**Sample request**

```
curl -X POST -d "name=todo&color=#63E6BE" -H "Authorization: Token 05b05e30ee979e333ff33a437988820494fb0afd"  "https://cloud.seafile.com/api/v2.1/repos/cf7ab8ca-ae38-4662-99c8-7fcafd7037de/file-tags/"

```

**Sample response**

```
{
	"repo_tag":
    {
    	"tag_color":"#63E6BE",
    	"tag_name":"todo",
    	"repo_id":"cf7ab8ca-ae38-4662-99c8-7fcafd7037de",
    	"repo_tag_id":4
    }
}

```

## Update a Tag of a Library

**PUT** <https://cloud.seafile.com/api/v2.1/repos/{repo_id}/repo-tags/{repo_tag_id}>

**request parameters**

* repo_id
* repo_tag_id
* name, tag name
* color, tag color

**Sample request**

```
curl -X PUT -d "name=new&color=#FFD43B" -H "Authorization: Token 05b05e30ee979e333ff33a437988820494fb0afd"  "https://cloud.seafile.com/api/v2.1/repos/cf7ab8ca-ae38-4662-99c8-7fcafd7037de/file-tags/1/"

```

**Sample response**

```
{
    "repo_tag": {
        "tag_color": "#FFD43B",
        "tag_name": "new",
        "repo_id": "cf7ab8ca-ae38-4662-99c8-7fcafd7037de",
        "repo_tag_id": 1
    }
}

```

## Delete a Tag of a Library

**DELETE** <https://cloud.seafile.com/api/v2.1/repos/{repo_id}/repo-tags/{repo_tag_id}>

**request parameters**

* repo_id
* repo_tag_id

**Sample request**

```
curl -X DELETE -d "name=todo&color=#63E6BE" -H "Authorization: Token 05b05e30ee979e333ff33a437988820494fb0afd"  "https://cloud.seafile.com/api/v2.1/repos/cf7ab8ca-ae38-4662-99c8-7fcafd7037de/file-tags/1/"

```

**Sample response**

```
{
    "success": "true"
}

```

## List All Tags of a File

**GET** <https://cloud.seafile.com/api/v2.1/repos/{repo_id}/file-tags/>

**request parameters**

* repo_id
* file_path

**Sample request**

```
curl -H "Authorization: Token 05b05e30ee979e333ff33a437988820494fb0afd"  "https://cloud.seafile.com/api/v2.1/repos/cf7ab8ca-ae38-4662-99c8-7fcafd7037de/file-tags/?file_path=%2Fmy_file"

```

**Sample response**

```
{
    "file_tags": [
        {
            "tag_color": "#FFD43B",
            "tag_name": "new",
            "repo_tag_id": 1,
            "file_tag_id": 1
        },
        {
            "tag_color": "#FFA8A8",
            "tag_name": "deprecated",
            "repo_tag_id": 2,
            "file_tag_id": 4
        }
    ]
}

```

## Add a Tag for a File

**POST** <https://cloud.seafile.com/api/v2.1/repos/{repo_id}/file-tags/>

**request parameters**

* repo_id
* file_path
* repo_tag_id

**Sample request**

```
curl -X POST -d "file_path=/my_file&repo_tag_id=2" -H "Authorization: Token 05b05e30ee979e333ff33a437988820494fb0afd"  "https://cloud.seafile.com/api/v2.1/repos/cf7ab8ca-ae38-4662-99c8-7fcafd7037de/file-tags/"

```

**Sample response**

```
{
	"file_tag":
	{
        "repo_tag_id":2,
        "file_tag_id":4
    }
}

```

## Delete a Tag from a File

**POST** <https://cloud.seafile.com/api/v2.1/repos/{repo_id}/file-tags/{file_tag_id}/>

**request parameters**

* repo_id
* file_tag_id

**Sample request**

```
curl -X DELETE -H "Authorization: Token 05b05e30ee979e333ff33a437988820494fb0afd"  "https://cloud.seafile.com/api/v2.1/repos/cf7ab8ca-ae38-4662-99c8-7fcafd7037de/file-tags/4/"

```

**Sample response**

```
{
    "success":"true"
}

```

## List Tagged Files By Tag ID

**GET** <https://cloud.seafile.com/api/v2.1/repos/{repo_id}/tagged-files/{repo_tag_id}/>

**request parameters**

* repo_id
* repo_tag_id

**Sample request**

```
curl -H "Authorization: Token 05b05e30ee979e333ff33a437988820494fb0afd"  "https://cloud.seafile.com/api/v2.1/repos/cf7ab8ca-ae38-4662-99c8-7fcafd7037de/tagged-files/2/"

```

**Sample response**

```
{
    "tagged_files": [
        {
            "modifier_email": "foo@foo.com",
            "file_tag_id": 2,
            "filename": "newfile",
            "parent_path": "/",
            "last_modified": "2019-10-10T10:08:47+00:00",
            "mtime": 1570702127,
            "modifier_contact_email": "foo@foo.com",
            "modifier_name": "foo",
            "size": 0
        }
    ]
}

```


