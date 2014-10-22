## API Reference: Read File Property
Obtain detailed file properties.

### Method:


**GET** /accounts/`$ACCOUNT_UID`/files/`$FILE_UID`/info

### Example request:


```
# curl https://api.roambi.com/1/accounts/`$ACCOUNT_UID`/files/`$FILE_UID`/info \
  -H "Authorization: Bearer `$ACCESS_TOKEN`" \
  -X GET
```
### Example response:


```
{
"uid": "5176db7884aea7...",
    "title": "My File",
    "created_at": "2013-04-23",
    "updated_at": "2013-04-24"
}
```
## API Reference: Update File Property
Updates a file in the specified Portal and folder. This method supports updating properties of a file (i.e. move file to a different folder or change file title), but does not support updating the file data itself.

### Method:

**POST** /accounts/`$ACCOUNT_UID`/files/`$FILE_UID`/info

### Parameters:

| Parameter | Data type | Description |
|-----|-----|-----|
| *title* | string | New title for the file. |
| *folder_uid* | string | ID of the new folder for the file in the Roambi Library. |

### Returns:

Returns summary details of the file as an confirmation for update completion.

### Error responses:

| Error Code | Description |
|-----|-----|-----|
| *resource_exists* | The "overwrite" property was set to false and a file with the same name already exists in the target folder. |
| *access_denied* | User does not have access to at least one resource related to this request. This may include trying to write to a read-only destination. |
| *invalid_resource* | Specified file or directory does not exist. |

### Example request:


```
# curl https://api.roambi.com/1/accounts/`$ACCOUNT_UID`/files/`$FILE_UID`/info \
  -H "Authorization: Bearer `$ACCESS_TOKEN`" \
  -d '{"title":`$NEW_TITLE`,' \
  -d '"folder_uid":`$NEW_FOLDER_UID`}'
  -X POST

```
### Example response:


```
{
"file": {
    "uid": "5176db7884aea7...",
    "title": "My New Title",
    "read_only": "false",
    "file_size": 13706,
    "file_type": EXCEL,
    "created_at": "2013-04-23",
    "updated_at": "2013-04-24"
  }
}
```
