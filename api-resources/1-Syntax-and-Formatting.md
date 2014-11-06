# Syntax and Formatting

The Roambi API performs all actions via HTTP using standard HTTP verbs:


| VERB | Description |
|------|-------------|
| GET  | Retrieve an object |
| POST | Create an object |
| PUT | Modify an object |
| DELETE | Delete an object |

Each API call requires basic HTTP parameters and has optional parameters that
can be configured via a JSON body object. The responses for both successes and
errors for each API call are also represented by JSON objects.  

Note that the code samples given in this section use the Bash shell. Variables
are indicated with the format `${VARIABLE_NAME}`.

## URL Scheme

All of the endpoints described in this API documentation assume a common base URL
in the following format:
`${HOSTNAME}:${PORT}/${API_VERSION}`

### Base URL
`https://api.roambi.com/1`

## Input/Output Format

Both request body data and response data are formatted as JSON. Extremely large
numbers will be returned in IEEE754 format (the same way doubles are stored in
  Java). For example: 1.2318237429383e+31.

### Date Format

All timestamps (both those sent in requests and those returned in responses) should
be formatted as ISO 8601.

### Response formats

The Roambi API sends responses as JSON objects in the following general format:

```
HTTP/1.1 200 OK
Date: Mon, 19 Jul 2013 16:18:20 GMT
Last-Modified: Mon, 12 Jul 2013 16:18:20 GMT
Content-Length: 832
Connection: close
Content-Type: application/json
{
  “${resource_name}” : {
  “resource_property_1” : “a string”,
  “resource_property_2” : “another string”,
  “nested_object_property_1” : { … }
  }
}
```

## Rate limiting

The Roambi API server has a rate limiting feature that restricts users to 100
requests per minute per Access Token. Any requests that exceed this limit will
be rejected with an `HTTP 503` error code.

## Error formats

Error responses are sent as a JSON object, and will come in the following
general format:

```
HTTP/1.1 400 Bad Request
Date: Mon, 19 Jul 2013 16:18:20 GMT
Content-Length: 832
Connection: close
Content-Type: application/json
{
  “error” : “error_code”,
  “error_description” : “error description”
}
```

## List of standard errors

The following errors can be received from any API resource, and are related to the
status of the account.

| Error Code | HTTP Status | Description |
|------------|-------------|-------------|
| invalid_account | 400 | Specified account does not exist. |
| disabled_account | 401 | Specified account has been disabled or has expired, or the current user does not have access to this account. |
| access_denied | 402 | User does not have the correct role to use this endpoint. |

## List of API resource errors

The following errors are received from API resources and may be specific to the
current state of those resources.

| Error Code | HTTP Status | Description |
|------------|-------------|-------------|
| expired_token | 401 | Provided access token has expired. |
| invalid_session | 401 | Provided access token has expired. |
| access_denied | 403 | User does not have access to at least one resource related to this request. This may include trying to write to a read-only destination.
| missing_parameter | 400 | A required parameter was not present in the request. |
| invalid_parameter | 400 | A parameter is not in the correct format.
| resource_exists | 400 | A resource already exists with the specified unique identifier. Typically returned during a create or update operation. |
| invalid_file_format | 400 | An uploaded file is not one of the accepted formats. |
| upload_limit_exceeded | 400 | An uploaded file is over the maximum size. |
| invalid_resource | 400 | A resource specified in this request is invalid (e.g. invalid directory_uid). The details object will contain the name of the invalid resource property. |
