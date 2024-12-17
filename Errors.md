---
stoplight-id: 4x3c8w97zi4nn
tags: [Errors]
---

# Errors

Effective error handling is essential for ensuring a smooth developer experience and building robust applications. This section provides an overview of the errors you may encounter when interacting with the IXO Spatial Web API, and best practices for handling them appropriately.

## Error Categories
The IXO Spatial Web API returns errors that fall into several main categories:

### 1. **Client Errors (4xx)**
Client errors occur when a request cannot be processed due to an issue from the client's side. These errors are typically related to issues like invalid input, authentication problems, or resource access restrictions. Common client error codes include:

- **400 Bad Request**: The request is malformed or contains invalid parameters.
- **401 Unauthorized**: Authentication is required or failed, usually due to a missing or invalid access token.
- **403 Forbidden**: The client does not have permission to access the requested resource.
- **404 Not Found**: The requested resource could not be found.
- **429 Too Many Requests**: The client has hit a rate limit, and should try again later.

### 2. **Server Errors (5xx)**
Server errors occur when there is an issue on the server side that prevents the request from being fulfilled. These errors are less frequent but are generally related to internal server malfunctions or temporary unavailability. Examples include:

- **500 Internal Server Error**: The server encountered an unexpected condition that prevented it from fulfilling the request.
- **502 Bad Gateway**: The server, while acting as a gateway or proxy, received an invalid response from the upstream server.
- **503 Service Unavailable**: The server is currently unable to handle the request, often due to maintenance or overload.

## Error Response Structure
When an error occurs, the IXO Spatial Web API provides an informative response in JSON format. The response includes relevant details to help developers troubleshoot the issue efficiently.

### Example Error Response
```json
{
  "error": {
    "code": 400,
    "message": "Invalid request parameters",
    "details": [
      {
        "field": "entityId",
        "error": "Missing required parameter"
      }
    ]
  }
}
```

- **code**: The HTTP status code representing the error type.
- **message**: A human-readable message describing the error.
- **details**: Additional details about the error, such as the specific field causing the issue.

## Best Practices for Handling Errors
To ensure your application can gracefully handle errors and provide the best user experience, consider following these best practices:

### 1. **Use HTTP Status Codes Effectively**
Rely on the HTTP status codes returned by the API to understand the nature of the issue. For example, always check for `401 Unauthorized` errors to determine whether re-authentication is needed.

### 2. **Implement Retry Logic for 5xx Errors**
Server-side errors are often temporary, and retrying the request after a delay may resolve the issue. Implement exponential backoff to avoid overwhelming the server during periods of high load.

### 3. **Validate Input Parameters**
To minimize `400 Bad Request` errors, validate all input parameters before sending requests. This helps to catch malformed requests early and avoid unnecessary interactions with the server.

### 4. **Respect Rate Limits**
Pay attention to `429 Too Many Requests` errors and implement rate-limiting strategies to comply with the API's usage restrictions. If a rate limit is reached, it is best to back off and retry after the suggested period.

### 5. **Log and Monitor Errors**
Log all error responses and monitor them to identify patterns or frequent issues. This can help improve error handling and prevent similar errors in future.

### 6. **Show User-Friendly Messages**
For client-facing applications, avoid displaying raw error messages to users. Instead, translate errors into user-friendly messages, such as "Please check your login details" for a `401 Unauthorized` error.

## Common Errors and Solutions
### **400 Bad Request**
- **Issue**: Invalid or malformed request.
- **Solution**: Double-check the request syntax and parameters before sending it to the API.

### **401 Unauthorized**
- **Issue**: Missing or invalid authentication.
- **Solution**: Ensure the access token is correct and hasn't expired. Re-authenticate if necessary.

### **403 Forbidden**
- **Issue**: Insufficient permissions to access a resource.
- **Solution**: Verify that the user has the correct roles or permissions to access the endpoint.

### **500 Internal Server Error**
- **Issue**: Server encountered an unexpected condition.
- **Solution**: Retry after some time, or contact support if the issue persists.
