## Reqres-API-Testing-with-Postman

Reqres API Testing Collection with Postman uploaded as json file to this repository.

### Test Plan

1. Overview
   
The goal of this test plan is to verify the functionality of ReqRes API. This includes verifying API responses for correctness, testing error handling, validating schema consistency, and ensuring the API functions as expected in different conditions.

2. Test Objectives
   
  •	 Validate that the ReqRes API responds correctly to valid requests.

  •	 Ensure the API handles invalid input and edge cases.

  •    Validate that the API responses match the expected structure and format.

3. Test Strategy
   
Postman is used to test the following API endpoints:

1.	GET /api/users - Retrieve a list of users.
2.	GET /api/users/{id} - Retrieve a single user by indicated ID.
3.	GET /api/users/{id} - Single user by indicated ID not found.
4.	GET /api/unknown - Return a list of all available color resources.
5.	GET /api/unknown/{id} - Return the color resource of indicated ID.
6.	GET /api/unknown/{id} - Color resource by indicated ID not found.
7.	POST /api/users - Create a new user.
8.	PUT /api/users/{id} - Replace a user's full information with new data.
9.	PATCH /api/users/{id} - Modify only specific fields of a user's information.
10. DELETE /api/users/{id} - Delete a user.
11. POST /api/register - Register a new user (successful scenario).
12. POST /api/register - Register a new user (unsuccessful scenario).
13. POST /api/login - Authenticate a user (successful login).
14. POST /api/login - Attempt to authenticate a user (unsuccessful login).
15. GET /api/users?delay={id} - Retrieve user data with a delay.

Postman_collection_version1 file contains all above requests as indicated in reqres.in website.




