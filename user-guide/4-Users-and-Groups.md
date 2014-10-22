## API Reference: Users
The Roambi Business API provides a way to manage users within the context of a specific
organization. Users resources will not violate the restrictions around user management
via the web UI. For example, if users can be invited to join an organization, but
cannot be directly added to the organization without consent, the API will follow
these restrictions accordingly.

The Users object has the following properties:

| Properties | Data type | Description |
|-----|-----|-----|
| *uid* | string | ID of the user. |
| *first_name* | string | First name of the user. |
| *last_name* | string | Last name of the user. |
| *email_address* | string | Email address registered for the user. |
| *role* | string | Role of the user. Valid roles are Administrator, Publisher, and Viewer. |
| *created_at* | timestamp | Timestamp for the date that the user was created. |
| *updated_at* | timestamp | Timestamp for the last time that the user info was updated. |

Example:


```
{
"users": [{
    "uid": "e4ca641e-b9...",
    "first_name": "Pete",
    "last_name": "Campbell",
    "email_address": "pete@scdp.com",
    "created_at": "2013-04-18",
    "updated_at": "2013-04-18"
  }]
}
```


## API Reference: Listing users
Retrieve lists of users associated with a specific Roambi Business organization.

Listing users requires the current user to be assigned the Admin role for the organization.

### Method:

**GET** /accounts/`$ACCOUNT_UID`/users

### Parameters:

| Parameter | Required? | Data type | Description |
|-----|-----|-----|
| *status* | No | string | Current status of the user. |

Valid `status` values can be "member" or "invited".

### Returns:

Returns a paged response of a list of users.

### Error responses:

See <a href="https://support.roambi.com/entries/23851988-API-error-codes" target="_blank">API error codes</a>.

### Example request:


```
# curl https://api.roambi.com/1/accounts/`$ACCOUNT_UID`/users \
  -H "Authorization: Bearer `$ACCESS_TOKEN`" \
  -X GET
```
### Example response:


```
{
"users": [{
    "uid": "e4ca641e-b9...",
    "first_name": "Pete",
    "last_name": "Campbell",
    "email_address": "pete@scdp.com",
    "created_at": "2013-04-18",
    "updated_at": "2013-04-18"
  },
  {
    "uid": "695ff138-fa2...",
    "first_name": "Megan",
    "last_name": "Draper",
    "email_address": "megan@scdp.com",
    "created_at": "2013-04-18",
    "updated_at": "2013-04-18"
  },
  {
    "uid": "c784ff63-9a3...",
    "first_name": "Roger",
    "last_name": "Sterling",
    "email_address": "roger@scdp.com",
    "created_at": "2013-04-18",
    "updated_at": "2013-04-18"
  },
  {
    "uid": "72a6d0d2-879...",
    "first_name": "Harry",
    "last_name": "Crane",
    "email_address": "harry@scdp.com",
    "created_at": "2013-04-18",
    "updated_at": "2013-04-18"
  }],
"list_data": {
  "offset":0,
  "limit":50,
  "record_count":4,
  "result_count":4
  }
}
```



## API Reference: Groups
The Roambi Business API provides a way to manage groups within the context of a specific organization. Groups resources will not violate the restrictions around group management via the web UI.

The Group object has the following properties:

| Properties | Data type | Description |
|-----|-----|-----|
| *uid* | string | ID of the group. |
| *name* | string | Name of the group. |
| *created_at* | timestamp | Timestamp for the date that the group was created. |
| *updated_at* | timestamp | Timestamp for the last time that the group info was updated. |

Example:


```
{
"groups": [{
    "uid": "51771b6484...",
    "name": "Sales",
    "created_at": "2013-04-18",
    "updated_at": "2013-04-18"
  }]
}
```


## API Reference: Listing groups
Retrieve lists of groups associated with a specific Roambi Business organization.

Listing groups requires the current user to be assigned the Admin role for the organization.

### Method:

**GET** /accounts/`$ACCOUNT_UID`/groups

### Parameters:

None.

### Returns:

Returns a paged response of a list of users.

### Error responses:

See <a href="https://support.roambi.com/entries/23851988-API-error-codes">API error codes</a>.

### Example request:


```
# curl https://api.roambi.com/1/accounts/`$ACCOUNT_UID`/groups \
  -H "Authorization: Bearer `$ACCESS_TOKEN`" \
  -X GET
```
### Example response:


```
{
"groups": [{
    "uid": "51771b6484...",
    "name": "Sales",
    "created_at": "2013-04-18",
    "updated_at": "2013-04-18"
  },
  {
"uid": "51771b7184a...",
    "name": "Finance",
    "created_at": "2013-04-18",
    "updated_at": "2013-04-18"
  }]
}
```
