## Read Folder Properties
Adds a new "read" or "write" permissions to a folder. When adding a user / group, no changes will occur if that user / group already has permissions set for the folder.

This method supports the following actions on a folder:
* Adding read permission for a user.
* Adding read permissions for a group.

### Method:
```
**POST** /accounts/`$ACCOUNT_UID`/folders/`$FOLDER_UID`/permissions
```

### Parameters:
None.

### Returns:
Returns summary details for the folder as a confirmation.

### Error responses:
| Error Message | Description |
|-----|-----|-----|
| *resource_not_found* | Specified file or use does not exist or is not visible to the current user. |
| *access_denied* | User does not have access to at least one resource related to this request. This may include trying to write to a read-only destination. |
| *invalid_resource* | Specified file does not exist. |

### Example request:
```
# curl https://api.roambi.com/1/accounts/`$ACCOUNT_UID`/folders/`$FOLDER_UID`/permissions \
 -H "Authorization: Bearer `$ACCESS_TOKEN`" \
 -d '{ \
"groups": {"`$GROUP_UID1`": "read", "`$GROUP_UID2`": "read", ...}, \
"users": {"`$USER_UID1`": "read", "`$USER_UID2`": "read", ...} \
}' \
-X POST
```

### Example response:
```
{
"folder": {
"permissions": {
"everyone": false,
"users": [
{
"access": "write",
"uid": "38150cfc-6c3f-4..."
}
],
"groups": [
{
"access": "read",
"uid": "51db3573c2..."
}
]
},
"updated_at": "2013-07-08",
"created_at": "2013-07-08",
"file_type": "FOLDER",
"read_only": false,
"title": "carlos2",
"uid": "51db3434c2e6..."
}
}
```
