# File History

## Get File History

**GET** <http://192.168.1.113:8000/api/v2.1/repos/{repo_id>)/file/history/?path={path}

**Request parameters**

* `repo-id`
* `path`, file path.
* `commit_id`, commit id used for get more file history. If not passed, Seafile will use library's head commit id as its default value and return the latest history.

**Sample request**

```
curl -H 'Authorization: Token e71c00e93af863ba9bcddb61a46bb4de11d713fc' -H 'Accept: application/json; charset=utf-8; indent=4' 'http://192.168.1.113:8000/api/v2.1/repos/7460f7ac-a0ff-4585-8906-bb5a57d2e118/file/history/?path=/o/3.md'

```

**Sample response**

```
{
    "next_start_commit": "ad4ac3e7744ef157ee2b600a3519fd7fdeef77ae",
    "data": [
        {
            "commit_id": "8fd46f0474f4af6628a74cfa16b760b43d229d61",
            "rev_file_id": "e36ff0171f3b87d374517614cdeab5a51ad48ded",
            "ctime": "2017-12-08T15:54:49+08:00",
            "creator_name": "lian",
            "creator_email": "lian@lian.com",
            "rev_renamed_old_path": null,
            "creator_avatar_url": "/media/avatars/0/1/a72299021077701e7c522c46fdaa87/resized/32/7d92599ea5fd5872f572d0e4d34cd7b6.png",
            "path": "/o/3.md",
            "creator_contact_email": "lian@lian.com",
            "size": 3,
            "description": "Modified \"3.md\""
        },
        {
            "commit_id": "a5c3b9855f8a5237e182823130e03bd49d4e8f23",
            "rev_file_id": "bf84ebd3b1043688dcc7b76a94eb64dadb8209a7",
            "ctime": "2017-12-08T15:54:42+08:00",
            "creator_name": "lian",
            "creator_email": "lian@lian.com",
            "rev_renamed_old_path": "/o/2.md",
            "creator_avatar_url": "/media/avatars/0/1/a72299021077701e7c522c46fdaa87/resized/32/7d92599ea5fd5872f572d0e4d34cd7b6.png",
            "path": "/o/3.md",
            "creator_contact_email": "lian@lian.com",
            "size": 1,
            "description": "Renamed \"2.md\""
        }
    ]
}

```

* If value of `next_start_commit` is NOT `false`, it means that there are more file history, if you want to continue to get more file history, resend the request with `commit_id` parameter, and assign the value of `next_start_commit` in response to request's `commit_id` parameter.
* If value of `rev_renamed_old_path` field in the last item of `data` in response is NOT `null`, it means that the last item is a file renamed/moved commit, if you want to get more file history before file was renamed/moved,  resend the request, and assign the value of `rev_renamed_old_path` in response to request's `path` parameter.

Sample request for get more file history, pay attention to the `path` and `commit_id` parameter.

```
curl -H 'Authorization: Token e71c00e93af863ba9bcddb61a46bb4de11d713fc' -H 'Accept: application/json; charset=utf-8; indent=4' 'http://192.168.1.113:8000/api/v2.1/repos/7460f7ac-a0ff-4585-8906-bb5a57d2e118/file/history/?path=/o/2.md&commit_id=ad4ac3e7744ef157ee2b600a3519fd7fdeef77ae'

```

Sample response.

```
{
    "next_start_commit": false,
    "data": [
        {
            "commit_id": "dcb12cf7c325bd4026ad9ebfe880d8f4efe76da8",
            "rev_file_id": "24adf1d58565836f8d487cdbc6398fffc6777f80",
            "ctime": "2017-12-06T11:54:53+08:00",
            "creator_name": "lian",
            "creator_email": "lian@lian.com",
            "rev_renamed_old_path": null,
            "creator_avatar_url": "/media/avatars/0/1/a72299021077701e7c522c46fdaa87/resized/32/7d92599ea5fd5872f572d0e4d34cd7b6.png",
            "path": "/o/1.md",
            "creator_contact_email": "lian@lian.com",
            "size": 1,
            "description": "Modified \"1.md\""
        },
        {
            "commit_id": "e2976492c767d5b989597a9a3b82169bd9e6f15e",
            "rev_file_id": "0000000000000000000000000000000000000000",
            "ctime": "2017-12-06T11:54:47+08:00",
            "creator_name": "lian",
            "creator_email": "lian@lian.com",
            "rev_renamed_old_path": null,
            "creator_avatar_url": "/media/avatars/0/1/a72299021077701e7c522c46fdaa87/resized/32/7d92599ea5fd5872f572d0e4d34cd7b6.png",
            "path": "/o/1.md",
            "creator_contact_email": "lian@lian.com",
            "size": 0,
            "description": "Added \"1.md\""
        }
    ]
}

```

Value of `next_start_commit` is `false` means all file histories have been returned.


**Errors**

* 400 path invalid.
* 403 Permission denied.
* 404 Library/File not found.
* 500 Internal Server Error

## Restore File From History

**POST** <https://cloud.seafile.com/api/v2.1/repos/7460f7ac-a0ff-4585-8906-bb5a57d2e118/file/?p=/1.md>

**Request parameters**

* repo_id
* p
* operation
* commit_id

**Sample request**

```
curl -d "operation=revert&commit_id=7ed3ccdc7559d1afddb95bc050230e3d54bbffef" -H "Authorization: Token 0eb24ce5db35a31f70171eca2f760f03f59fa09a" -H 'Accept: application/json; indent=4' "https://cloud.seafile.com/api/v2.1/repos/7460f7ac-a0ff-4585-8906-bb5a57d2e118/file/?p=/1.md"

```

**Sample response**

```
{
    "success": true
}

```

**Errors**

* 400 commit_id invalid.
* 403 Permission denied.
* 403 File is locked
* 500 Internal Server Error
* 500 Check file lock error

## Download File From a Revision

**GET** <https://cloud.seafile.com/api2/repos/{repo-id}/file/revision/?p=/foo.c&commit_id=a1ec20709675f4dc8db825cdbca296be245d189b>

**Request parameters**

* repo-id
* p
* commit_id

**Sample request**

```
curl -H 'Authorization: Token f2210dacd3606d94ff8e61d99b477fd' -H 'Accept: application/json; charset=utf-8; indent=4' https://cloud.seafile.com/api2/repos/dae8cecc-2359-4d33-aa42-01b7846c4b32/file/revision/?p=/foo.c\&commit_id=a1ec20709675f4dc8db825cdbca296be245d189b

```

**Sample response**

```
"https://cloud.seafile.com:8082/files/adee6094/foo.c"

```

**Errors**

* 400 Path is missing
* 404 Revision not found


