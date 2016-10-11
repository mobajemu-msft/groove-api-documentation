# Groove RESTful API HTTP Status Codes
The Hypertext Transfer Protocol (HTTP) standard describes a number of status codes that are returned by the server in response to a client request. The Groove API methods return HTTP protocol-compliant status codes to describe the status of the request.

The table provides a list of status codes returned by the Groove API, and their typical meanings.

| **Code** | **Reason phrase**               | **Description**                                                                                        |
|----------|---------------------------------|--------------------------------------------------------------------------------------------------------|
| 200      | OK                              | The request was successful.                                                                            |
| 400      | Bad Request                     | The URL or input parameters are incorrect.                                                             |
| 401      | Unauthorized                    | The request requires user authentication.                                                              |
| 403      | Forbidden                       | The request is not allowed for the user or service.                                                    |
| 404      | Not Found                       | The specified resource could not be found.                                                             |
| 409      | Conflict                        | The request was not completed due to a conflict with the current state of the resource.                |
| 429      | Too Many Requests               | The caller has exceeded the service throttling limit and needs to wait before sending another request. |
| 500      | Internal Server Error           | The server encountered an unexpected condition that prevented it from fulfilling the request.          |
| 502      | Bad Gateway                     | A backend dependency is unavailable or returning errors.                                               |
| 503      | Service Unavailable             | The server is refusing the request due to excessive load.                                              |

| Note                                                                                                                                                                                                                                      |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Some resources and methods provide specific information about the meaning of particular status codes in the context of that resource or method. For more details, refer to the documentation for the resources or methods that you are using. |

## See Also
[Error(JSON)](JSON_Error.md)
