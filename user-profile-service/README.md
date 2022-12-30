# User Profile Service
![Screenshot](https://github.com/jackson0726/10k-steps-challenge/blob/main/ingest-service/src/main/resources/images/user_profile_service_architecture.png)

### Description
+ The user profile service manages the profile data for a unique user.
+ A user is identified by the following information:
  + A username (must be unique).
  + A password.
  + An email address.
  + A city.
  + A pedometer device identifier (must be unique).
  + Whether the user wants to appear in public rankings or not.

+ API:
  + /user/register: POST - Register a new user (200: success, 409: username already exists, 500: internal error).
  + /user/<username>: GET - Get a user's details (200: success, 404: username does not exists, 500: internal error).
  + /user/<username>: PUT - Update some user details (200: success, 404: username does not exists, 500: internal error).
  + /user/authenticate: POST - Credentials validation (200: success, 401: when authentication fails).
  + /user/owns/<deviceId>: GET - Reverse lookup of a user by their device (200: success, 409: device does not exists, 500: internal error).
