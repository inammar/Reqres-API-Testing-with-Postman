## Reqres-API-Testing-with-Postman

Reqres API Testing Collection with Postman uploaded as json file to this repository as version 1 and version 2 files.

### Test Plan

1. Overview
   
The goal of this test plan is to verify the functionality of ReqRes API. This includes verifying API responses for correctness, testing error handling, validating schema consistency, and ensuring the API functions as expected in different conditions.

2. Test Objectives
   
  •	 Validate that the ReqRes API responds correctly to valid requests.

  •	 Ensure the API handles invalid input and edge cases.

  •    Validate that the API responses match the expected structure and format.

3. Test Strategy
   
3.1. Postman is used to test the following API endpoints:

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

3.2. Postman_collection_version1 file contains all above requests as indicated in reqres.in website.

4. Test Scenarios and Cases
   
4.1 Functional Tests

•	Test Case 1: GET /api/users

o	Objective: Verify that the API correctly returns a list of users.

o	Test Steps:

1.	Send a GET request to /api/users.
   
2.	Check that the response status code is 200 OK.
   
3.	Verify that the response contains a list of users (e.g., an array of user objects).
   
4.	Validate the response body to ensure it contains the following attributes: id, email, first_name, last_name, avatar.

•	Test Case 2: GET /api/users/{id}

o	Objective: Verify that the API returns the correct user when querying by a valid id.

o	Test Steps:

1.	Send a GET request to /api/users/{id} with an existing user ID (e.g., GET /api/users/2).
   
2.	Check that the response status code is 200 OK.
   
3.	Validate that the response contains user data with the required attributes (id, email, first_name, etc.).

•	Test Case 3: POST /api/users

o	Objective: Verify that the API creates a new user.

o	Test Steps:

1.	Send a POST request to /api/users with valid data in the request body (e.g., { "name": "John", "job": "Developer" }).
   
2.	Verify the response status code is 201 Created.
   
3.	Check that the response contains the name and job fields, and their values are correct.






