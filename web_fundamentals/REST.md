# RESTful API

A RESTful API is an application programming interface (API) that follows the REST architectural style for building web APIs. It allows for the creation, retrieval, updating, and deletion of resources through a uniform interface, using HTTP methods to indicate the desired action.

## RESTful API Components

RESTful API Components

1. Client: The client is the user of the API and can be a web browser, mobile app, or any other application that sends requests to the server.

2. Server: The server is the provider of the API and is responsible for processing the requests from the client and returning a response.

3. Resources: Resources are the data or functionality provided by the API and are accessed through a unique identifier, called a URL.

4. HTTP Methods: HTTP methods are used to indicate the desired action on a resource, such as GET, POST, PUT, DELETE, and PATCH.

5. URL: The URL is a unique identifier for a resource and includes the domain name, the API endpoint, and any additional parameters or filters.

## HTTP Methods

The most common HTTP methods used in RESTful APIs are:

### GET

The GET method is used to retrieve a resource from the server. It is a safe and idempotent method, which means that it does not modify the resource and can be repeated without any side effects.

Example:

```
GET /users
```

This request retrieves a list of users from the server.

```
GET /users/123
```

This request retrieves the details of the user with the ID 123 from the server.

### POST

The POST method is used to create a new resource on the server. It is not safe or idempotent, as it can modify the server's state and create multiple resources if repeated.

Example:

```
POST /users
{
  "name": "John",
  "email": "john@example.com"
}
```


This request creates a new user with the name "John" and email "john@example.com" on the server.

### PUT

The PUT method is used to update an existing resource on the server. It is not safe but is idempotent, which means that it can be repeated without any side effects, as long as the resource being updated is the same.

Example:

```
PUT /users/123
{
    "name": "John Smith",
  "email": "john@example.com"
}
```

This request updates the user with the ID 123 with the new name "John Smith" and email "john@example.com" on the server.

### DELETE

The DELETE method is used to delete a resource from the server. It is not safe or idempotent, as it can modify the server's state and delete multiple resources if repeated.

Example:

```
DELETE /users/123
```

This request deletes the user with the ID 123 from the server.

### PATCH

The PATCH method is used to partially update a resource on the server. It is not safe but is idempotent, which means that it can be repeated without any side effects, as long as the resource being updated is the same.

Example:

```
PATCH /users/123
{
    "name": "John Smith"
}
```

This request updates the name of the user with the ID 123 to "John Smith" on the server, leaving the other fields unchanged.

## HTTP Status Codes

HTTP status codes are used to indicate the status of a request made to a server. They are three-digit codes that provide information about the request and the response.

### 1xx: Informational

1xx status codes are used to indicate that the request has been received and is being processed.

- 100 Continue: The server has received the request and is waiting for the rest of the request body to be sent.

- 101 Switching Protocols: The server is switching protocols in response to the request.

### 2xx: Success

2xx status codes are used to indicate that the request was successful and the response contains the requested data.

- 200 OK: The request was successful and the response contains the requested data.

- 201 Created: The request was successful and a new resource was created as a result.

- 202 Accepted: The request was accepted but has not yet been processed.

### 3xx: Redirection

3xx status codes are used to indicate that the client needs to take additional action to complete the request.

- 301 Moved Permanently: The requested resource has been permanently moved to a new URL.

- 302 Found: The requested resource has been temporarily moved to a new URL.

- 303 See Other: The client should use a different URL to access the resource.

### 4xx: Client Error

4xx status codes are used to indicate that the client made an error in the request.

- 400 Bad Request: The request was invalid or could not be understood by the server.

- 401 Unauthorized: The client is not authorized to access the requested resource.

- 404 Not Found: The requested resource was not found on the server.

### 5xx: Server Error

5xx status codes are used to indicate that the server encountered an error while processing the request.

- 500 Internal Server Error: An unexpected condition was encountered by the server and no specific message was given.

- 502 Bad Gateway: The server received an invalid response from an upstream server.

- 503 Service Unavailable: The server is currently unable to handle the request due to maintenance or overload.

## Conclusion

RESTful APIs are a popular choice for building web APIs due to their simplicity and flexibility. By following the REST principles and using the appropriate HTTP methods, it is possible to create a scalable and maintainable system for interacting with resources over the web.
