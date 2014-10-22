# Jobs

A job is a process that the Roambi Business server kicks off when Roambi Business
converts an RBI template and a data source into a new RBI view.

The Jobs object has the following parameters:

| Parameter | Data type | Description |
|-----|-----|-----|
| *uid* | string | ID of the running job. |
| *progress* | string | Progress of the job. |
| *status* | string | Current status of the job. |
| *exception* | numeric | If the job is interrupted or fails, gives the exception code for the job. |
| *retry_after* | numeric | Number of seconds that the job will wait to retry if it initially fails. |
| *status_url* | string | Link to check job status. |

Example:


```
{
"job": {
    "uid": "3b6f7815-eaa5-4b...",
    "progress": 0,
    "status": "processing",
    "exception": null,
    "results": null,
    "retry_after": 3,
    "status_url": "/1/jobs/3b6f7815-eaa5-4b..."
  }
}
```

## Submit Job
This method submits a job to the Roambi Business server that starts the Analytics
file publication process. The publication of Analytics files require both a data
source file residing in a portal and an existing template.

### Method:
```
POST /accounts/`$ACCOUNT_UID`/files/analytics
```

### Parameters:
| Parameter | Required? | Data type | Description |
|-----|-----|-----|
| *template_uid* | Yes | string | ID of the RBI template. |
| *title* | Yes | string | Title of the published file. |
| *source_file_uid* | Yes | string | ID of the data source file. |
| *folder_uid* | Yes | string | ID of the folder where the published RBI will be located. |
| *overwrite* | No | boolean | Specify "true" to overwrite an existing Roambi Analytics file in the same directory. |

### Returns:

Returns a background publication job.

### Error responses:

| Error Code | Description |
|-----|-----|-----|
| *file_exists* | The "overwrite" property was set to false and a file with the same name already exists in the target folder. |
| *access_denied* | User does not have access to at least one resource related to this request. This may include trying to write to a read-only destination. |
| *invalid_file_format* | The source file is not a valid Roambi Analytics source file. |
| *invalid_resource* | Specified file does not exist. |

### Example request:


```
# curl https://api.roambi.com/1/accounts/`$ACCOUNT_UID`/files/analytics \
-H "Authorization: Bearer `$ACCESS_TOKEN`" \
-d '{"title" : "`$TITLE`", \
  "template_uid" : "`$TEMPLATE_UID`", \
  "source_file_uid" : "`$SOURCE_FILE_UID`", \
  "folder_uid" : "`$FOLDER_UID`", \
  "overwrite" : true}' \
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




## Check Job Status

Retrieve the status of a job. After creating a job, you can check the status of that job an unlimited number of times.

### Method:


```

GET /jobs/`$JOB_UID`


```
### Parameters:

None.

### Returns:

Returns a Job object that reflects the current status of a job.

### Error responses:

See [API Error Codes](1-Syntax-and-Formatting.md)

### Example request:


```
# curl https://api.roambi.com/1/jobs/`$JOB_UID`\
  -H "Authorization: Bearer `$ACCESS_TOKEN`" \
  -X GET
```
### Example response:


```
{
"job": {
    "uid": "3b6f7815-eaa5-4b...",
    "progress": 1,
    "status": "complete",
    "exception": null,
    "retry_after": 3,
    "status_url": "/1/jobs/3b6f7815-eaa5-4b..."
  }
}
```
