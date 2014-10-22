# Resource:  analytics_files
The `analytics_files` resource exposes Analytics publishing via the API.

## Resource Definition

## Endpoints

### Create analytics_file
This endpoint supports two request modes

1.  remote source file (source file stored in Roambi Business)
2.  local source file (source file on the client machine)

#### Endpoint
`POST /1/accounts/${ACCOUNT_UID}/files/analytics`

#### Parameters
Requests to this endpoint must provide a json body that contains the following
properties:

* overwrite_existing (required, boolean)
* title (required, String)
* template_uid (required, uuid)
* source_file_uid (optional, uuid)
* source_file (optional, multipart form upload)

IF publishing with a remote source file, then all parameters must be submitted
as a JSON body.

IF publishing with a local source file, then all parameters must be individually
specified as part of a multipart/form-upload request.

Sample JSON body (remote source file):
```json
{
  "overwrite_existing" : "true",
  "title" : "My New Roambi",
  "template_uid" : "0045407b-19f5-4b90-9148-d418209c7e90",
  "source_file_uid" : "53f29a50036495f25ccf6782"
}
```
### Request samples
Using curl (remote source file):

```bash
curl https://api.roambi.com/1/accounts/74f331e2-f78b-4948-bca2-a230ee351f1d/files/analytics \
  -H "Authorization: Bearer $ACCESS_TOKEN" \
  -X POST
  -d '{ \
      "title": "My New Roambi", \
      "overwrite_existing": true, \
      "template_uid" : "0045407b-19f5-4b90-9148-d418209c7e90", \
      "source_file_uid" : "53f29a50036495f25ccf6782"
     }'
```
