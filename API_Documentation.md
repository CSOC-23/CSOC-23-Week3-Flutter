# API Description

## Auth System

For this API, you will have to use Token-based Authorization. We have already created a model named **Token** required to create token for a user, for your reference. All the requests made to the API (except the Login and Register endpoints) shall need an _Authorization header_ with a valid token and the prefix _Token_. Make sure to add proper permissions in the views to implement this.

For authorization, a `createToken()` has been created in the `controllers/user.js`. Generally we use jwt for authentication but here we have created a model for the same.

In order to obtain a valid token it's necessary to send a request `POST /auth/login/` with **username** and **password**. To register a new user it's necessary to make a request `POST /auth/register/` with name, email, username and password.

## End Points

**Auth**

- `POST /auth/login/`

  Takes the username and password as input, validates them and returns the **Token**, if the credentials are valid.

  Request Body (Sample):

  ```
  {
    "username": "string",
    "password": "string"
  }
  ```

  Response Body (Sample):

  ```
  {
    "token":  "string"
  }
  ```

  Response Code: `200`

- `POST /auth/register/`

  Register a user in Django by taking the name, email, username and password as input.

  Request Body (Sample):

  ```
  {
    "name": "string",
    "email": "user@example.com",
    "username": "string",
    "password": "string"
  }
  ```

  Response Body (Sample):

  ```
  {
    "token":  "string"
  }
  ```

  Response Code: `200`

- `POST /auth/profile/`

  Retrieve the id, name, email and username of the logged in user. Requires token in the Authorization header.

  Response Body (Sample):

  ```
  {
    "id":  1,
    "name":  "string",
    "email":  "user@example.com",
    "username":  "string"
  }
  ```

  Response Code: `200`

**Todo**

- `GET /todo/`

  Get all the Todos of the logged in user. Requires token in the Authorization header.

  Response Body (Sample):

  ```
  [
    {
      "id":  1,
      "title":  "string"
    },
    {
      "id":  2,
      "title":  "string"
    }
  ]
  ```

  Response Code: `200`

- `POST /todo/create/` **(The Response Body of this endpoint is different from what we have created for Task 1)**

  Create a Todo entry for the logged in user. Requires token in the Authorization header.

  Request Body (Sample):

  ```
  {
    "title": "string"
  }
  ```

  Response Body (Sample):

  ```
  {
    "id":  1,
    "title":  "string"
  }
  ```

  Response Code: `200`

- `GET /todo/:id/`

  Get the Todo of the logged in user with given id. Requires token in the Authorization header.

  Response Body (Sample):

  ```
  {
    "id":  1,
    "title":  "string"
  }
  ```

  Response Code: `200`

- `PUT /todo/:id/`

  Change the title of the Todo with given id, and get the new title as response. Requires token in the Authorization header.

  Request Body (Sample):

  ```
  {
    "title": "string"
  }
  ```

  Response Body (Sample):

  ```
  {
    "id":  1,
    "title":  "string"
  }
  ```

- `PATCH /todo/:id/`

  Change the title of the Todo with given id, and get the new title as response. Requires token in the Authorization header.

  Request Body (Sample):

  ```
  {
    "title": "string"
  }
  ```

  Response Body (Sample):

  ```
  {
    "id":  1,
    "title":  "string"
  }
  ```

- `DELETE /todo/:id/`

  Delete the Todo with given id. Requires token in the Authorization header.

  Response Code: `204`
