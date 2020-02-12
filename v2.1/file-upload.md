# File Upload

## Upload File

### Get Upload Link

**GET** <https://cloud.seafile.com/api2/repos/{repo-id}/upload-link/?p=/upload-dir>

**Request parameters**

* repo-id
* p (use '/' as default)

**Sample request**

```
curl -H "Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd" https://cloud.seafile.com/api2/repos/99b758e6-91ab-4265-b705-925367374cf0/upload-link/

```

**Sample response**

```
"http://cloud.seafile.com:8082/upload-api/73c5d117-3bcf-48a0-aa2a-3f48d5274ae3"

```

**Errors**

```
403 Permission denied.
500 Run out of quota

```

### Upload File

After getting the upload link, POST to this link for uploading files.

**POST** <http://cloud.seafile.com:8082/upload-api/73c5d117-3bcf-48a0-aa2a-3f48d5274ae3>

**Request parameters**

The parameters and file contents should be encoded in [Multipart/form-data format](https://tools.ietf.org/html/rfc7578) . Most http client libraries support it.

* file: this field contains the contents to be uploaded.
* parent_dir : path in your Seafile repo that you want to upload local file to.
* relative_path: sub-folder of "parent_dir", if this sub-folder does not exist, Seafile will create it recursively. When you upload a folder, you should set this parameter to the uploaded folder's name.
* ret-json: returns a json array including file info if set to `1`. If this parameter is not set, the file ids will be returned in a tab-separated string. New apps should set ret-json to 1.
* need_idx_progress: Set to `true`  to ask the server to index file content asynchronously after upload is finished. So that the client doesn't have to wait until the file indexing is completed, which can take some time. The request returns a `task_id` to check file indexing progress.
* replace: whether to overwrite file when it already exists. 1 for replace, 0 for not replace. If existing file is not replaced, the uploaded file will be renamed to the form "filename (1).txt".

**Sample request without **`ret-json`** parameter**

upload file to `/path-in-seafile-repo/`, if a file named 'test.txt' already exists in `/path-in-seafile-repo/`, replace it with the new file:

```
curl -H "Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd" -F file=@local-folder/test.txt -F parent_dir=/path-in-seafile-repo/ -F replace=1 http://cloud.seafile.com:8082/upload-api/73c5d117-3bcf-48a0-aa2a-3f48d5274ae3

curl -H "Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd" -F file=@local-folder/test.txt -F parent_dir=/path-in-seafile-repo/ http://cloud.seafile.com:8082/upload-api/73c5d117-3bcf-48a0-aa2a-3f48d5274ae3

```

**Sample response without **`ret-json`** parameter**

```
adc83b19e793491b1c6ea0fd8b46cd9f32e592fc

```

**Sample request with **`relative_path`** and **`ret-json`\*\* \*\*

upload file to `/path-in-seafile-repo/sub_path_1/sub_path_2/`, Seafile will create `sub_path_1/sub_path_2/` recursively if it does not exist:

```
curl -H "Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd" -F file=@local-folder/test.txt -F file=@1.jpg -F parent_dir=/path-in-seafile-repo/ -F relative_path=sub_path_1/sub_path_2/ http://cloud.seafile.com:8082/upload-api/73c5d117-3bcf-48a0-aa2a-3f48d5274ae3?ret-json=1

```

**Sample response with **`relative_path`** and **`ret-json`\*\* \*\*

```
[
    {
        "name": "test.txt",
        "id": "4ccd37916552e2943314027931edd0b45240be7c",
        "size": 2987
    },
    {
        "name": "1.jpg",
        "id": "12e07dd00c124fa7ea3b645ff9fe183f73eab2a1",
        "size": 1699246
    }
]

```

**Sample request with **`need_idx_progress=true`\*\* \*\*

upload file to `/path-in-seafile-repo/`:

```
curl -H "Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd" -F file=@local-folder/test.txt -F parent_dir=/path-in-seafile-repo/ http://cloud.seafile.com:8082/upload-api/73c5d117-3bcf-48a0-aa2a-3f48d5274ae3?need_idx_progress=true

```

**Sample response with **`?need_idx_progress=true`

```
d319a3f4-40da-4d58-9d3f-07864061f633

```

Then use the `task_id` above to get the progress of file indexing.

**Sample request get progress of file indexing**

```
http://192.168.1.113:8082/idx_progress?task_id=d319a3f4-40da-4d58-9d3f-07864061f633

```

The request returns a JSON string, containing following information:

* indexed: number of bytes indexed
* total: total size of the file
* status: 0 for finished, -1 for error, 1 for indexing
* ret_json: the same JSON formatted file IDs as when `ret-json=1` is set. It's only set when status is 0 (indexing finished).

**Sample response**

```
{
    "indexed": 1244,
    "total": 1244,
    "status": 0,
    "ret_json": "[{\"name\": \"seafile-license (1).txt\", \"id\": \"cb8d8eaa4e540d30550a26e399b1207ef798bc67\", \"size\": 1244}]"
}

```

**Note**

* For python client uploading, see <https://github.com/haiwen/webapi-examples/blob/master/python/upload-file.py>, or it can be done much more easily with elegant [python requests library](http://docs.python-requests.org/en/latest/), see <https://github.com/haiwen/webapi-examples/blob/master/python/upload-file2.py>

**Errors**

```
400 Bad request
403 Permission denied
440 Invalid filename
442 File size is too large
443 Out of quota
500 Internal server error

```

## Resumable Upload File

Refer to <https://manual.seafile.com/deploy_pro/web_resumable_upload.html> to learn more about web resumable upload.

### Check If Enable Resumable Upload

**GET** <http://192.168.1.113:8000/api/v2.1/repos/{repo_id}/file-uploaded-bytes/?parent_dir={parent_dir}&file_name={file_name}>

**Request parameters**

* repo_id
* parent_dir
* file_name

**Sample request**

```
curl -v -H 'Authorization: Token e71c00e93af863ba9bcddb61a46bb4de11d713fc' -H 'Accept: application/json; charset=utf-8; indent=4' "http://192.168.1.113:8000/api/v2.1/repos/09b7d3c0-5f0d-49be-9318-7ca136f386cd/file-uploaded-bytes/?parent_dir=/&file_name=test.md"

```

**Sample response**

```
*   Trying 192.168.1.113...
* Connected to 192.168.1.113 (192.168.1.113) port 8000 (#0)
> GET /api/v2.1/repos/09b7d3c0-5f0d-49be-9318-7ca136f386cd/file-uploaded-bytes/?parent_dir=/&file_name=test.md HTTP/1.1
> Host: 192.168.1.113:8000
> User-Agent: curl/7.50.1
> Authorization: Token e71c00e93af863ba9bcddb61a46bb4de11d713fc
> Accept: application/json; charset=utf-8; indent=4
>
* HTTP 1.0, assume close after body
< HTTP/1.0 200 OK
< Date: Fri, 01 Jun 2018 08:59:27 GMT
< Server: WSGIServer/0.1 Python/2.7.12+
< Content-Length: 26
< Content-Language: en
< Accept-Ranges: bytes
< Vary: Accept, Accept-Language, Cookie
< Allow: GET, HEAD, OPTIONS
< Content-Type: application/json; charset=utf-8; indent=4
<
{
    "uploadedBytes": 0
* Closing connection 0
}

```

If the response has this header `Accept-Ranges: bytes`, means that Seafile server supports resumable upload file.

**Errors**

* 400 parent_dir/file_name invalid.
* 404 Library/Folder not found.
* 500 Internal server error

### Get Upload Link

Same as getting upload link for uploading files.

### Get Bytes Already Uploaded

Before starting a resumable upload, you should first get how much of the file has been uploaded before, and use it as the offset to start uploading.

**GET** <http://192.168.1.113:8000/api/v2.1/repos/{repo_id}/file-uploaded-bytes/?parent_dir={parent_dir}&file_name={file_name}>

**Request parameters**

* repo_id
* parent_dir
* file_name

**Sample request**

```
curl -v -H 'Authorization: Token e71c00e93af863ba9bcddb61a46bb4de11d713fc' -H 'Accept: application/json; charset=utf-8; indent=4' "http://192.168.1.113:8000/api/v2.1/repos/09b7d3c0-5f0d-49be-9318-7ca136f386cd/file-uploaded-bytes/?parent_dir=/path-in-seafile-repo/&file_name=test.md"

```

**Sample response**

File has not been uploaded before.

```
{
    "uploadedBytes": 0
}

```

File has already been uploaded 149946368 bytes. If you want to continue uploading this file, upload it begin with 149946368 bytes.

```
{
    "uploadedBytes": 149946368
}

```

**Errors**

* 400 parent_dir/file_name invalid.
* 404 Library/Folder not found.
* 500 Internal server error

### Upload File in Chunks

Usually a large file is uploaded in many "chunks" with resumable upload. The chunk size can be chosen by the client app. The chunks are then uploaded one by one. After the last chunk is uploaded, the server will index the entire file and save it.

After getting the upload link and `uploadedBytes`, POST to this link for uploading the chunks.

**POST** <http://cloud.seafile.com:8082/upload-api/73c5d117-3bcf-48a0-aa2a-3f48d5274ae3>

**Request parameters**

The request parameters are the same as uploading a file. But two extra headers must be added in the request.

* Content-Range: specifies the range of bytes that are being uploaded. Refer to <https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Range> for more details.
* `Content-Disposition: attachment; filename=\"filename.txt\"` . When using resumable upload, the name of the file is no longer retrieved from the "file" field of the form. It's instead retrieved from a header.

Note: unlike uploading an entire file, resumable upload can only support uploading a single file in each request.

**Sample request**

upload file to `/path-in-seafile-repo/`, if a file named 'test.txt' already exists in `/path-in-seafile-repo/`, replace it with the new file:

```
curl -H "Content-Range: bytes 149946368-150994943/1587609600" -H "Content-Disposition: attachment; filename=\"test.md\"" -F file=@test.md -F parent_dir=/path-in-seafile-repo/ -F replace=1 http://cloud.seafile.com:8082/upload-api/73c5d117-3bcf-48a0-aa2a-3f48d5274ae3

```

* `149946368-150994943` means is now uploading 149946368-150994943 bytes.
* `1587609600` is file's total bytes.

**Sample response**

If this is not the last chunk, the server returns 200 with 

```
{
    "success": true
}

```

If this is the last chunk, the server returns the same response as uploading an entire file.

**Errors**

```
400 Bad request
403 Permission denied
440 Invalid filename
442 File size is too large
443 Out of quota
500 Internal server error

```

## Update file

### Get Update Link

**GET** <https://cloud.seafile.com/api2/repos/{repo-id}/update-link/?p=/update-dir>

**Request parameters**

* repo-id
* p (use '/' as default)

**Sample request**

```
curl -H "Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd" https://cloud.seafile.com/api2/repos/99b758e6-91ab-4265-b705-925367374cf0/update-link/

```

**Sample response**

```
"http://cloud.seafile.com:8082/update-api/e69e5ee7-9329-4f42-bf1b-12879bd72c28"

```

**Errors**

```
403 Permission denied.
500 Run out of quota

```

### Update File

After getting the update link, POST to this link for updating files.

**POST** <http://cloud.seafile.com:8082/update-api/e69e5ee7-9329-4f42-bf1b-12879bd72c28>

**Request parameters**

* file: this field contains the contents to be uploaded.
* target_file: The absolute path inside the library of the file being updated.

**Sample request**

```
curl -H "Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd" -F file=@test.txt -F target_file=/test.txt http://cloud.seafile.com:8082/update-api/e69e5ee7-9329-4f42-bf1b-12879bd72c28

```

**Returns**

The id of the updated file

**Sample response**

```
"adc83b19e793491b1c6ea0fd8b46cd9f32e592fc"

```

**Errors**

```
400 Bad request
403 Permission denied
440 Invalid filename
441 File does not exist
442 File size is too large
443 Out of quota
500 Internal server error

```

## Uploading Large File in Blocks

This is only for use in Seafile desktop and mobile clients.

### Step 1, POST the block list to Seahub

**POST** <https://cloud.seafile.com/api2/repos/{repo-id}/upload-blks-link/?p=/parent-folder-path>

**Request parameters**

* `repo-id`.
* `p`, parent folder path, default is `/`.
* `blklist`: string of block ids, seperated by `,`, for example:

**Sample request**

```
curl -H "Authorization: Token 2bac21cab9eb0c4baac10d1e6fc3cf590f0dcf17" -d 'blklist=1faee57feb464aa1f61165722c93a5075d1993ff,0cfc000bbde26a7b9d4754103501af76a7a' http://192.168.1.113:8000/api2/repos/d4f596ed-09ea-4ac6-8d59-12acbd089097/upload-blks-link/?p=/

```

**Sample response**

The response is in json format containing the following fields:

* rawblksurl: the url to upload raw blocks to file server
* commiturl: the url to commit file in file server
* blklist: the block id list of the missing blocks


```
{
    "blklist": [
        "1faee57feb464aa1f61165722c93a5075d1993ff",
        "0cfc000bbde26a7b9d4754103501af76a7a"],
    "commiturl": "http://192.168.1.113:8082/upload-blks-api/8bd0ae30-e543-4e03-84ce-03a3cc79e14a?commitonly=true&ret-json=true",
    "rawblksurl": "http://192.168.1.113:8082/upload-raw-blks-api/8bd0ae30-e543-4e03-84ce-03a3cc79e14a"
}

```

**Errors**

* 403 Permission denied.
* 404 Folder not found.
* 404 Library not found.
* 443 Out of quota.
* 500 Internal Server Error

### Step 2, upload missing blocks to rawblksurl

```
POST http://server-address:8082/upload-raw-blks-api/<token>

```

**Request parameters**

* filename: file block id.

The content of the request is in multipart form-data format.

```
------WebKitFormBoundaryWWPdItXjNGBDlSuZ
Content-Disposition: form-data; name="file"; filename=<block id>
Content-Type: text/xml


------WebKitFormBoundaryWWPdItXjNGBDlSuZ--

```

Each block is sent in a file field. You should set `filename` attribute to the id of each block.

**Sample request**

```
curl -F file=@1.txt -F filename=1faee57feb464aa1f61165722c93a5075d1993ff https://dev.seafile.com/seafhttp/upload-raw-blks-api/389479a2-01fb-4073-8cd3-8f5115e78fc9

```

**Success**

   Response code 200 if everything is ok

**Errors**

* 400 Invalid URL | Access denied | Duplicate progress id | Invalid Seafile-Content-Range
* 440 Invalid filename
* 441 File already exists
* 442 File size is too large
* 443 Out of quota
* 500 Internal error

### Step 3, let the server to commit the file

```
POST commiturl: `http://server-address:8082/upload-blks-api/<token>?commitonly=true&ret-json=true`

```

The content is in multipart form-data format. Fields and corresponding values are:

**Request parameters**

* parent_dir: parent directory path
* file_name: file name
* file_size: file size in bytes
* replace: whether overwrite file with the same name. 1 for replace, 0 for not replace.
* blockids: block id list of the file in JSON list format

**Sample request**

```
curl -d "parent_dir=/&file_name=1.md&file_size=1234&replace=0&blockids=["1faee57feb464aa1f61165722c93a5075d1993ff","0cfc000bbde26a7b9d4754103501af76a7a36f89"]" -H 'Accept: application/json; charset=utf-8; indent=4' https://dev.seafile.com/seafhttp/upload-blks-api/389479a2-01fb-4073-8cd3-8f5115e78fc9?commitonly=true&ret-json=true

```

**Sample response**

If you set 'ret-json' into url arguments, new_file_id will be returned

```
{
    "id": "4ccd37916552e2943314027931edd0b45240be7c"
}

```

**Errors**

* 400 Invalid URL | Access denied | Duplicate progress id | Invalid Seafile-Content-Range
* 440 Invalid filename
* 441 File already exists
* 442 File size is too large
* 443 Out of quota
* 446 Block missing
* 403 Permission denied
* 500 Internal error

### Get Update Blocks Link

**GET** <https://cloud.seafile.com/api2/repos/{repo-id}/update-blks-link/>

**Request parameters**

* repo-id

**Sample request**

```
curl -H "Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd" https://cloud.seafile.com/api2/repos/99b758e6-91ab-4265-b705-925367374cf0/update-blks-link/

```

**Sample response**

```
"https://cloud.seafile.com/seafhttp/update-blks-api/402c6d48-fe52-4592-97dd-85f462f03d66"

```

**Errors**

* 403 Can not access repo
* 520 above quota


