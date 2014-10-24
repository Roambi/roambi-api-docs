# Resource:  analytics_files
The `analytics_files` resource exposes Analytics publishing via the API.


### Create analytics_file
This endpoint supports two request modes

1.  remote source file (source file stored in Roambi Business)
2.  local source file (source file on the client machine)


### Method
`POST /1/accounts/${ACCOUNT_UID}/files/analytics`


### Parameters:
| Parameter | Required? | Data type | Description |
|-----|-----|-----|-----|
| *template_uid* | Yes | string | ID of the RBI template. |
| *title* | Yes | string | Title of the published file. |
| *source_file_uid* | No | string | ID of the data source file. Can be provided instead of *source_file*; see notes below |
| *source_file* | No | File | Can be provided instead of *source_file_uid*; see notes below. |
| *folder_uid* | Yes | string | ID of the folder where the published RBI will be located. Alternately specify email of a user for his personal folder. |
| *overwrite* | No | boolean | Specify "true" to overwrite an existing Roambi Analytics file in the same directory. |

Notes:
\* IF publishing with a remote source file, then all parameters must be submitted as a JSON body.
\* IF publishing with a local source file, then all parameters must be individually specified as part of a multipart/form-upload request.
\* Only account administrator or the personal folder's owner is allowed to publish to that personal folder.

### Returns:

Returns a background publication job.


### Error responses:

| Error Code | Description |
|-----|-----|-----|
| *file_exists* | The "overwrite" property was set to false and a file with the same name already exists in the target folder. |
| *access_denied* | User does not have access to at least one resource related to this request. This may include trying to write to a read-only destination. |
| *invalid_file_format* | The source file is not a valid Roambi Analytics source file. |
| *invalid_resource* | Specified file does not exist. |

### Example requests

#### Remote Source File (File exists in the Roambi Library)
```bash
# curl https://api.roambi.com/1/accounts/`$ACCOUNT_UID`/files/analytics \
-H "Authorization: Bearer `$ACCESS_TOKEN`" \
-d '{"title" : "`$TITLE`", \
  "template_uid" : "`$TEMPLATE_UID`", \
  "source_file_uid" : "`$SOURCE_FILE_UID`", \
  "folder_uid" : "`$FOLDER_UID`", \
  "overwrite" : true}' \
-X POST
```

#### Local Source File
```bash
$> curl https://api.roambi.com/1/accounts/6d86fe02-adc3-4eb7-9caf-889f1adf33c7/files/analytics \
      -H 'Authorization: Bearer 1/k7lSGo_4JDTjR6GM9iQX9eEKcW5m4Wu5rmMkA-TGsBk9obLtmhnRXmkyI2mE2TGVDFzZXpS8eDhDD2dzl8kYaBGEMkNAORi4TRYR7-ibkac=|ArXS6blvpbZAFH3G-PM3Gw==' \
      -F publish_options='{ \
                            "template_uid":"5201526be4b02842ad9a0bfc", \
                            "overwrite":"true", \
                            "folder_uid":"538573e7e4b0f8cae9752567", \
                            "title":"MyNewRbiFromLocalFile" \
                          }' \
      -F source_file=@'CataListSourceData.xls' \
      -X POST
```

### Example response:
```
{
  "job": {
    "uid": "51771b6484...",
    "progress": 0,
    "status": "processing",
    "exception": null,
    "results": null,
    "retry_after": 3,
    "status_url": "/api/1/job/a6593d94-155..."
  }
}
```
