# Office Web APP Integration

## View File Through Office Web APP

**GET** https://cloud.seafile.com/api2/repos/{repo-id}/owa-file/?path=/foo.docx

**Request parameters**

* repo-id
* path
* action, `view` or `edit`, default value is `view`;

**Sample request for view**

    curl  -v  -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd' -H 'Accept: application/json; charset=utf-8; indent=4' 'https://cloud.seafile.com/api2/repos/dae8cecc-2359-4d33-aa42-01b7846c4b32/owa-file/?path=/foo.docx'

**Sample response for view**

```
{
    "access_token": "7decacff-6e55-4856-9734-01aaab26ef45",
    "action_url": "http://off1.off.com/wv/wordviewerframe.aspx?WOPIsrc=http%3A%2F%2F192.168.1.124%3A8000%2Fapi2%2Fwopi%2Ffiles%2F2b0750085925fa85238e5f64cfd13ed6f1076bfd%2F",
    "access_token_ttl": 1456906784000
}
```

**Sample request for edit**

    curl  -v  -H 'Authorization: Token f2210dacd9c6ccb8133606d94ff8e61d99b477fd' -H 'Accept: application/json; charset=utf-8; indent=4' 'https://cloud.seafile.com/api2/repos/dae8cecc-2359-4d33-aa42-01b7846c4b32/owa-file/?path=/foo.docx&action=edit'

**Sample response for edit**

```
{
    "access_token": "bb80a7934b42454189ade73bdfba7f62",
    "action_url": "http://off1.off.com/we/wordeditorframe.aspx?WOPISrc=http%3A%2F%2F192.168.1.227%3A8000%2Fapi2%2Fwopi%2Ffiles%2F1ef1da7af8dc2d02f85f156dba779a31ff1db9f7&ui=zh-CN&rs=zh-CN",
    "access_token_ttl": 1496925674000
}
```

**After get response**

In order to instantiate the Office Online applications, a host must create an HTML page that will host an iframe element within it pointing to a particular WOPI action URL. And then use a form element and POST the `access_token` and `access_token_ttl` values to the Office Online.

For more info, you can see [this official docs](http://wopi.readthedocs.org/en/latest/hostpage.html).

**Errors**

* 400 path invalid.
* 403 permission denied.
* 403 Library encrypted.
* 403 Office Web App feature not enabled.
* 403 Office Web App feature only supported in professional edition.
* 404 File/Library not found.
* 500 Internal Server Error
