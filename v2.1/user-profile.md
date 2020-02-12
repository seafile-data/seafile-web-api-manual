# user-profile

## Get User Profile

**GET** https://cloud.seafile.com/api/v2.1/user/

**Sample request**

    curl -H "Authorization: Token f2210dacd9c6ccb8133606d94ff8e6199b477fd" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api/v2.1/user/

**Sample response**

    {
        "login_id": "006",
        "name": "Jon Snow",
        "telephone": "110",
        "list_in_address_book": false,
        "contact_email": "othermailofjon@gmail.com",
        "email": "jonsnow@gmail.com"
    }

## Update User Profile

If you want to use this api, you must set `ENABLE_UPDATE_USER_INFO` to `True` in `../conf/seahub_settings.py`, for more info please see [this manual](https://manual.seafile.com/config/seahub_settings_py.html#other-options).

If you want to change contact email, you must set `ENABLE_USER_SET_CONTACT_EMAIL` to `True` in `../conf/seahub_settings.py`.

**PUT** https://cloud.seafile.com/api/v2.1/user/

**Request parameters**

- name (user's nickname, if no value passed, this field will not be changed)
- telephone (if no value passed, this field will not be changed)
- contact_email (if no value passed, or pass your old contact email, this field will not be changed)
- list_in_address_book (`true` or `false`, whether list your account in global address book, if no value passed, this field will not be changed)

**Sample request**

    curl -X PUT -d 'name=Lanister&telephone=120'  -H "Authorization: Token d8c517a01d9ba43a532801fbb3cd07d03b03ea17" -H 'Accept: application/json; indent=4' https://cloud.seafile.com/api/v2.1/user/

**Sample response**

    {
        "login_id": "006",
        "name": "Lanister",
        "telephone": "120",
        "list_in_address_book": false,
        "contact_email": "othermailofjon@gmail.com",
        "email": "jonsnow@gmail.com"
    }

**Errors**

* 400 name/telephone/contact_email/list_in_address_book invalid.
* 403 NOT allow to update user profile.
* 403 NOT allow to set contact email.
* 500 Internal Server Error
