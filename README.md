# JWT Authentication .NET Sample

## Description

The **JWT Authentication .NET Sample** is an **sample ASP.NET Web API** to help understand how role based authentication can be implemented via JWTs in a **.NET 6** application. It utilizes an **InMemory database** using **Entity Framework Core** for storing user data and the **BCrypt** library for encrypting passwords.

The API has 1 controller:

* **AuthController**: Contains the login, registration, and test APIs

### AuthController

The `AuthController` contains the login, registration, and test APIs we are using to get and try the JWT token authentication.

* POST `/auth/login`

    * Returns the JWT token along with the user information from the database after the user enters their email and password.
    * Post Http Request Link: `https://<YOUR-DOMAIN:PORT>//auth/login`
    * Request Body Example:

        ```json
        {
            "userName": "adityaoberai1",
            "password": "test123"
        }
        ```

    * Response Example:

        ```json
        {
            "userName": "adityaoberai1",
            "name": "Aditya",
            "role": "Everyone",
            "isActive": true,
            "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJuYW1lIjoiYWRpdHlhb2JlcmFpMSIsImdpdmVuX25hbWUiOiJBZGl0eWEiLCJyb2xlIjoiRXZlcnlvbmUiLCJuYmYiOjE2NjA3NzA0NDQsImV4cCI6MTY2MDc3MjI0NCwiaWF0IjoxNjYwNzcwNDQ0fQ.20KEe53MsDeapYk0EkeayfZqmsyPSuVOVBzsHpmFMS4",
            "password": "$2a$11$DdJgRS3BKpoo64ap940g9.TsFzharf5PwCn1BH4e/oIBeNf7FKiOe"
        }
        ```

* POST `/auth/register`

    * Adds the user's details to the database and returns the JWT token along with the user information after the user enters their information.
    * Post Http Request Link: `https://<YOUR-DOMAIN:PORT>/auth/register`
    * Request Body Example:

        ```json
        {
            "name": "Aditya",
            "userName": "adityaoberai1",
            "password": "test123",
            "role": "Everyone"
        }
        ```

    * Response Example:

        ```json
        {
            "userName": "adityaoberai1",
            "name": "Aditya",
            "role": "Everyone",
            "isActive": true,
            "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJuYW1lIjoiYWRpdHlhb2JlcmFpMSIsImdpdmVuX25hbWUiOiJBZGl0eWEiLCJyb2xlIjoiRXZlcnlvbmUiLCJuYmYiOjE2NjA3NzAzNjAsImV4cCI6MTY2MDc3MjE2MCwiaWF0IjoxNjYwNzcwMzYwfQ.oCK_udTh83F-OM7yLYK7NBQa8basKTVQpMF3GUYtUtA",
            "password": "$2a$11$DdJgRS3BKpoo64ap940g9.TsFzharf5PwCn1BH4e/oIBeNf7FKiOe"
        }
        ```

        *Note: Token returned will be different from the example*

* GET `/auth/test`

    * Returns claims from the JWT sent as the **Bearer token** in the `Authorization` header with **Everyone** role.
    * Get Http Request Link: `https://<YOUR-DOMAIN:PORT>/auth/test`
    * Request Header Example:

        `Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJuYW1lIjoiYWRpdHlhb2JlcmFpMSIsImdpdmVuX25hbWUiOiJBZGl0eWEiLCJyb2xlIjoiRXZlcnlvbmUiLCJuYmYiOjE2NjA3NzA0NDQsImV4cCI6MTY2MDc3MjI0NCwiaWF0IjoxNjYwNzcwNDQ0fQ.20KEe53MsDeapYk0EkeayfZqmsyPSuVOVBzsHpmFMS4`

    * Response Example:

        ```json
        {
            "name": "adityaoberai1",
            "given_name": "Aditya",
            "role": "Everyone",
            "nbf": "1660770444",
            "exp": "1660772244",
            "iat": "1660770444"
        }
        ```

