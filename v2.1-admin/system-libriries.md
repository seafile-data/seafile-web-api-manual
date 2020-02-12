# system-libriries

## Get System Library Info

**GET** <https://cloud.seafile.com/api/v2.1/admin/system-libraries/>

**Sample request**

```
curl -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' https://cloud.seafile.com/api/v2.1/admin/system-libraries/

```

**Sampple response**

```
{
	"description":"Template for creating 'My Library' for users",
	"name":"My Library Template",
	"id":"5e7212d7-1bdb-4351-bc25-58a274b1419f"
}

```

## Get Upload Library Content Link

**GET** <https://cloud.seafile.com/api/v2.1/admin/system-library/upload-link/?from=web>

**Request parameters**

* path

**Sample request**

```
cur -d "path=/" -H "Authorization: Token f2d84d433a7d6a255e27f325c1050df48e8c26ac" -H 'Accept: application/json; charset=utf-8; indent=4' https://cloud.seafile.com/api/v2.1/admin/system-library/upload-link/?from=web/

```

**Sampple response**

```
{"upload_link":"http://127.0.0.1:8082/upload-aj/45af9909-f276-4fde-a12c-be87a18eac89"}

```


