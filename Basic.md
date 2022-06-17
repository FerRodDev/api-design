## HTTP requests

**GET /users**
Get all users

**GET /users/{id}**
Get a specific user by the given id

**POST /users**
Create a new user

**PUT /users/{id}**
Update a user by the given id

**DELETE /users/{id}**
Delete a user by the given id

## Relationships between resources

**GET /teamwork/{id}/users**
Get all the users by the given teamwork id

**GET /teamwork/{id}/users/{id}**
Get a specific user by the given teamwork and user id

## HTTP response codes

**200 OK**  

- Used to indicate success (all verbs)

**201 CREATED**  

- Successful creation (POST/PUT)  
- Set the Location header with the link to the newly-created resource (POST)  
- Response body content may or may not be present  

**204 NO CONTENT**  

- Indicates success but nothing is in the response body (PUT/DELETE)

**400 BAD REQUEST**  

- General error when fulfilling the request would cause an invalid state (all verbs)  
e.g missing data in params or domain validation errors 

**401 UNAUTHORIZED**  

- Error code response for missing or invalid authentication (all verbs)

**403 FORBIDDEN**  

- Error code when the user is not authorized to perform the operation/resource, or this one is unavailable for some reason (all verbs)

**404 NOT FOUND**  

- Used when the requested for the resource is not found (whether it doesn't exist or security reasons) (all verbs)

**405 METHOD NOT ALLOWED**  

- Used to indicate that the requested URL exists, but the HTTP method is not applicable (all verbs)  
  e.g POST /users/123 where the API doesn't support creation of resources with a provided ID

- The Allow HTTP header must be set when returning a 405 to indicate the HTTP methods that are supported. In the previous case, the header would look like "Only allow: GET, PUT, DELETE" 

**409 CONFLICT**  

- Whenever a resource conflict would be caused by fulfilling the request (POST/PUT/DELETE)  
e.g trying to create two customers with the same id or deleting root objects when cascade-delete is not supported

**500 INTERNAL SERVER ERROR**

- Never return this intentionally (all verbs)  
- The general catch-all error when the server-side throws an exception
- Use this only for errors that the consumer cannot address from their end

