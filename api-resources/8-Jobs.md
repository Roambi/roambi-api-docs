# Jobs

A job is a process that the Roambi Business server kicks off when Roambi Business
converts an RBI template and a data source into a new RBI view.

The Jobs object has the following parameters:

| Parameter | Data type | Description |
|-----|-----|-----|-----|
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

## Check Job Status

Retrieve the status of a job. After creating a job, you can check the status of that job an unlimited number of times.


### Method:
`GET /jobs/${JOB_UID}`

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
