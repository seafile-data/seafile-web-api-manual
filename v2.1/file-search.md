# File Search

## Search Files in Libraries

**GET** <https://cloud.seafile.com/api2/search/>

**Request parameters**

* `q`, keyword for searching.
* `page`, optional, a number greater than or equal to **1**.
* `per_page`, optional.
* `search_repo`, `all`, `mine`, `shared`, `group`, `public` or a _repo_id_, (`all` for searching in all libraries, etc.), optional. For searching in shared libraries, you can also pass `shared_from` or `not_shared_from` parameter beside `shared` to filter shared libraries.
* `search_path`, path of specifiy library.(This option works only when search_repo is a single repo_id.)
* `search_ftypes`, `all` or `custom`, (`all` for searching all file types, `custom` for only searching the specific file types you defined in `ftype` and `input_fexts`).
* `ftype`, must be in (`Text`, `Document`, `Image`, `Video`, `Audio`, `PDF`, `Markdown`).

> TEXT: ('ac', 'am', 'bat', 'c', 'cc', 'cmake', 'cpp', 'cs', 'css', 'diff', 'el', 'h', 'html', 'htm', 'java', 'js', 'json', 'less', 'make', 'org', 'php', 'pl', 'properties', 'py', 'rb', 'scala', 'script', 'sh', 'sql', 'txt', 'text', 'tex', 'vi', 'vim', 'xhtml', 'xml', 'log', 'csv', 'groovy', 'rst', 'patch', 'go'),
>
> DOCUMENT: ('doc', 'docx', 'ppt', 'pptx', 'odt', 'fodt', 'odp', 'fodp'),
>
> IMAGE: ('gif', 'jpeg', 'jpg', 'png', 'ico', 'bmp', 'tif', 'tiff', 'eps'),
>
> VIDEO: ('mp4', 'ogv', 'webm', 'mov'),
>
> AUDIO: ('mp3', 'oga', 'ogg'),
>
> PDF: ('pdf',),
>
> MARKDOWN: ('markdown', 'md'),

* `input_fexts`, file extensions manually specific.
* `with_permission`, `true` or `false`. Whether return permission info of the file or not, default is `false`.
* `time_from`, filter the result that the updated time greater than or equal to  this value. default unit is `second`.
* `time_to`, filter the result that the updated time less than or equal to  this value. default unit is `second`.
* `size_from`: filter the result that the size greater than or equal to  this value. default unit is `byte`.
* `size_to`: filter the result that the size less than or equal to this value. default unit is `byte`.

**Sample request**

```
curl -H 'Authorization: Token 076de58233c09f19e7a5179abff14ad55987350e' -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api2/search/?q=seafile&search_repo=all&search_ftypes=custom&ftype=Document&input_fexts=md,png&per_page=3&page=3&with_permission=true"

```

**Sample response**

```
{
    "has_more": true,
    "total": 336,
    "results": [
        {
            "repo_id": "040a8aad-5646-4c68-ba8a-73f90c60089f",
            "name": "seafile \u8fd0\u7ef4.docx",
            "repo_encrypted": False,
            "permission": "r",
            "oid": "ecba7db3d6b818873bf94cb1f2161f6a0fc22494",
            "last_modified": 1482910730,
            "content_highlight": "... .<b>seafile</b>.com...",
            "fullpath": "/\u4e1c\u98ce\u65e5\u4ea7/Archived/seafile \u8fd0\u7ef4.docx",
            "repo_name": "\u4ee3\u7ef4\u5ba2\u6237",
            "is_dir": false,
            "repo_type": 'mine',
            "size": 494490
        },
        {
            "repo_id": "233191c7-8e33-4fd2-b0a3-e480363d8e0d",
            "name": "seafile-tutorial.doc",
            "repo_encrypted": False,
            "permission": "rw",
            "oid": "1066014004ad479dd7f3cc0a12462c3f1fd2edeb",
            "last_modified": 1389771193,
            "content_highlight": "...A Brief Tour of <b>Seafile</b> <b>Seafile</b> is a file m...",
            "fullpath": "/\u4ea7\u54c1\u4f7f\u7528\u6587\u6863/seafile-tutorial.doc",
            "repo_name": "seafile-dev",
            "is_dir": false,
            "repo_type": 'mine',
            "size": 414208
        },
        {
            "repo_id": "233191c7-8e33-4fd2-b0a3-e480363d8e0d",
            "name": "seafile_vm.md",
            "repo_encrypted": False,
            "permission": "rw",
            "oid": "66c8dbe139333ead26b4878340da486fffdc5330",
            "last_modified": 1439277140,
            "content_highlight": "...<b>Seafile</b> server VM...",
            "fullpath": "/\u90e8\u7f72\u548c\u8fd0\u7ef4/seafile_vm.md",
            "repo_name": "seafile-dev",
            "is_dir": false,
            "repo_type": 'shared',
            "size": 3255
        }
    ]
}

```

**Sample request**

```
Search for files in a library specified directory.

curl -H 'Authorization: Token 076de58233c09f19e7a5179abff14ad55987350e' -H 'Accept: application/json; charset=utf-8; indent=4' "https://cloud.seafile.com/api2/search/?q=a&search_repo=2628a63b-cfad-41f5-a748-392ec9287686&search_path=/testtest"

```

**Sample response**

```
{
    "has_more": false,
    "total": 2,
    "results": [
        {
            "repo_owner_name": "admin",
            "repo_id": "2628a63b-cfad-41f5-a748-392ec9287686",
            "name": "3a",
            "repo_encrypted": False,
            "repo_owner_contact_email": "admin@admin.com",
            "repo_owner_email": "admin@admin.com",
            "last_modified": 1520836447,
            "content_highlight": "",
            "fullpath": "/testtest/3a",
            "repo_name": "dev",
            "is_dir": false,
            "size": 0
        },
        {
            "repo_owner_name": "admin",
            "repo_id": "2628a63b-cfad-41f5-a748-392ec9287686",
            "name": "1a",
            "repo_encrypted": False,
            "repo_owner_contact_email": "admin@admin.com",
            "repo_owner_email": "admin@admin.com",
            "last_modified": 1520836462,
            "content_highlight": "",
            "fullpath": "/testtest/1a",
            "repo_name": "dev",
            "is_dir": false,
            "size": 0
        }
    ]
}

```

**Sample request**

```
Search for files within the specified time range and size range.

curl -H 'Authorization: Token 076de58233c09f19e7a5179abff14ad55987350e' -G -d 'q=a&time_from=1517801993&
time_to=15254060581&size_from=100&size_to=105' http://cloud.seafile.com/api2/search/

```

**Sample response**

```
{
"has_more": false,
"total": 4,
"results": [
    {
        "repo_owner_name": "admin",
        "repo_type": "mine",
        "repo_id": "c89409c5-b52c-4469-91ba-b222a5d3efff",
        "name": "e0c64527659f42b60cc3b16597ac07a0448a50",
        "repo_owner_contact_email": "admin@admin.com",
        "repo_owner_email": "admin@admin.com",
        "last_modified": 1517802012,
        "content_highlight": "",
        "fullpath": "/note1/.git/objects/06/e0c64527659f42b60cc3b16597ac07a0448a50",
        "repo_name": "Doc",
        "is_dir": false,
        "size": 103
    },
    {
        "repo_owner_name": "admin",
        "repo_type": "mine",
        "repo_id": "c89409c5-b52c-4469-91ba-b222a5d3efff",
        "name": "e0c64527659f42b60cc3b16597ac07a0448a50",
        "repo_owner_contact_email": "admin@admin.com",
        "repo_owner_email": "admin@admin.com",
        "last_modified": 1517802012,
        "content_highlight": "",
        "fullpath": "/untitled folder/note1/.git/objects/06/e0c64527659f42b60cc3b16597ac07a0448a50",
        "repo_name": "Doc",
        "is_dir": false,
        "size": 103
    },
    {
        "repo_owner_name": "admin",
        "repo_type": "mine",
        "repo_id": "c89409c5-b52c-4469-91ba-b222a5d3efff",
        "name": "2a4dce0781e77bd4e8d6a73d5c35bafbccebe7",
        "repo_owner_contact_email": "admin@admin.com",
        "repo_owner_email": "admin@admin.com",
        "last_modified": 1517802010,
        "content_highlight": "",
        "fullpath": "/note1/.git/objects/29/2a4dce0781e77bd4e8d6a73d5c35bafbccebe7",
        "repo_name": "Doc",
        "is_dir": false,
        "size": 103
    },
    {
        "repo_owner_name": "admin",
        "repo_type": "mine",
        "repo_id": "c89409c5-b52c-4469-91ba-b222a5d3efff",
        "name": "2a4dce0781e77bd4e8d6a73d5c35bafbccebe7",
        "repo_owner_contact_email": "admin@admin.com",
        "repo_owner_email": "admin@admin.com",
        "last_modified": 1517802010,
        "content_highlight": "",
        "fullpath": "/untitled folder/note1/.git/objects/29/2a4dce0781e77bd4e8d6a73d5c35bafbccebe7",
        "repo_name": "Doc",
        "is_dir": false,
        "size": 103
    }
]

```

}

**Errors**

* 404 Search not supported.
* 400 Missing argument q.
* 400 Parameter invalid.


