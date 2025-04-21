## Reqres-API-Testing-with-Postman

Reqres API Testing Collection with Postman uploaded as json file to this repository.

### Test Plan

1. Overview
   
The goal of this test plan is to verify the functionality, performance, and security of the ReqRes API. This includes verifying API responses for correctness, testing error handling, validating schema consistency, and ensuring the API functions as expected in different conditions.

2. Test Objectives
   
  •	 Validate that the ReqRes API responds correctly to valid requests.

  •	 Ensure the API handles invalid input and edge cases.

  •  Validate that the API responses match the expected structure and format.

3. Test Strategy
   
We will use Postman to test the following API endpoints:

1.	GET /api/users - Retrieve a list of users.
2.	GET /api/users/{id} - Retrieve a single user by ID.
3.	POST /api/users - Create a new user.
4.	PUT /api/users/{id} - Update a user's information.
5.	DELETE /api/users/{id} - Delete a user.
6.	GET /api/unknown - Retrieve a list of unknown items (color data).

We will create a Postman collection that contains requests for each of the endpoints and implement tests for the following scenarios.




