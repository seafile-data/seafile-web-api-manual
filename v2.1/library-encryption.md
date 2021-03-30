# Library Encryption

## Decrypt Library

**POST** https://cloud.seafile.com/api2/repos/{repo-id}/

**Request parameters**

* password

**Sample request**

    curl -v -d "password=123" -H 'Authorization: Token e6a33d61954f219a96b60f635cf02717964e4385' -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api2/repos/0c2465a5-4753-4660-8a22-65abec9ec8d0/

**Sample response**

"success"

**Errors**

* 400 Incorrect password
* 409 Repo is not encrypted

