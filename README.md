# WEEK 1 - Authentication and Authorization

API is powered by json-server. You must implement the client with the specifications below.

## API overview 

To run the API execute the following npm script:

``yarn run-server``

### Authentication routes
- POST ``/register``
    - Body Payload
    ```json
        {
            email: string;
            password: string;
        }
    ```
- POST ``/login``
    - Body payload
    ```json
        {
            email: string;
            password: string;
        }
    ```

On a successfull register or login, the API response is a JSON containing a JWT token in the ``accessToken`` field. Every subsequent request to an API resource should include it on the Authorization header, like so (``XXX`` should be replaced with the access token):

``Authorization: Bearer XXX``

### Resource Routes

- GET ``/640/users``
  - Lists all users
  - Needs authorization header

- GET ``/664/posts``
  - Lists all posts
  - Public access

- POST ``/664/posts``
  - Adds a new post
  - Needs authorization header
  - Body Payload
  ```json
        {
            title: string;
        }
    ```

- DELETE ``/664/posts/{id}``
  - Deletes a post
  - Needs authorization header

## Client overview

### Routes:

- ``/register``
    - Show a form for user sign up
    - If user is already logged in, redirect to ``/``
- ``/login``
    - Show a form for user sign in
    - If user is already logged in, redirect to ``/``
- ``/posts``
    - Lists all posts
    - Button that display a form when clicked to create a new post
    - Button to delete the post
    - Show a message if there are no posts to show
- ``/users``
    - Lists all users
- ``/``
    - Redirects to /posts if logged, else to /login

There should be a navbar present in all routes which links to all routes above.

If a request fails, show in the UI the error from API if available, else show a generic error message.