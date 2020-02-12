# file-scan

## List File Scan Records

**GET** [https://cloud.seafile.com/api/v2.1/admin/file-scan-records/](https\://cloud.seafile.com/api/v2.1/admin/file-scan-records/)

**Request parameters**

* start (default: 0)
* limit (default: 25)

**Sample request：**

```
curl -H "Authorization: Token c644892a0d598f48664370803880d6149946efb1" -H 'Accept: application/json; charset=utf-8; indent=4' "http://127.0.0.1:8000/api/v2.1/admin/file-scan-records/"

```

**Sample response：**

```
{
    "record_list": [
        {
            "detail": {
                "suggestion": "block",
                "label": "abuse"
            },
            "platform": "ali",
            "repo_id": "39c96502-8c6a-4883-a366-3bc9ad64bf93",
            "path": "/test.md",
            "repo_name": "Library"
        },
        {
            "detail": {
                "suggestion": "block",
                "label": "politics"
            },
            "platform": "ali",
            "repo_id": "39c96502-8c6a-4883-a366-3bc9ad64bf93",
            "path": "/哈哈哈哈哈哈哈哈哈哈/呵呵呵呵呵呵呵呵.md",
            "repo_name": "Library"
        }
    ]
}

```

**Success**

Return a list of record object.

**Errors**

* 500 INTERNAL SERVER ERROR


