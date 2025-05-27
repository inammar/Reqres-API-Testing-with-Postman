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

   Tests in Postman:

        //assertion test to verify response status
        pm.test("Status code is 200", function () {
            pm.response.to.have.status(200);
        });
        //checks that the response has a data field and that it's an array, to confirm the API returns a list of users in the correct format
        pm.test("Response is an array", function () {
            pm.response.to.have.jsonBody('data');
            pm.expect(pm.response.json().data).to.be.an('array');
        });
        //checks that the first user in the response has all expected attributes (id, email, first_name, last_name, and avatar), to ensure each user object includes the required fields.
        pm.test("User attributes are present", function () {
            var jsonData = pm.response.json();
            pm.expect(jsonData.data[0]).to.have.property('id');
            pm.expect(jsonData.data[0]).to.have.property('email');
            pm.expect(jsonData.data[0]).to.have.property('first_name');
            pm.expect(jsonData.data[0]).to.have.property('last_name');
            pm.expect(jsonData.data[0]).to.have.property('avatar');
        });

•	Test Case 2: GET /api/users/{id}

o	Objective: Verify that the API returns the correct user when querying by a valid id.

o	Test Steps:

1.	Send a GET request to /api/users/{id} with an existing user ID (e.g., GET /api/users/2).
   
2.	Check that the response status code is 200 OK.
   
3.	Validate that the response contains user data with the required attributes (id, email, first_name, etc.).

   Tests in Postman:

        //assertion test to verify response status
        pm.test("Status code is 200", function () {
            pm.response.to.have.status(200);
        });
        //checks that the response has a data object and that this object contains id and email fields, confirming user details are returned—typically used when requesting a single user
        pm.test("User data is returned", function () {
            var jsonData = pm.response.json();
            pm.expect(jsonData).to.have.property('data');
            pm.expect(jsonData.data).to.have.property('id');
            pm.expect(jsonData.data).to.have.property('email');
        });

•	Test Case 3: GET /api/users/{id}

o	Objective: Verify that the API does not return user with indicated ID.

o	Test Steps:

1.	Send a GET request to /api/users/{id} with a non existing user ID (e.g., GET /api/users/23).
   
2.	Verify the response status code is 404 Not Found.
   
 Tests in Postman:

        //assertion test to verify response status
        pm.test("Status code is 404", function () {
            pm.response.to.have.status(404);
        });

•	Test Case 4: GET /api/unknown

o	Objective: Verify that the API correctly returns a list of all available color resources.

o	Test Steps:

1.	Send a GET request to /api/unknown.
   
2.	Check that the response status code is 200 OK.

   Tests in Postman:

        //assertion test to verify response status
        pm.test("Status code is 200", function () {
            pm.response.to.have.status(200);
        });

•	Test Case 5: GET /api/unknown/{id}

o	Objective: Verify that the API correctly returns the color resource of indicated ID.

o	Test Steps:

1.	Send a GET request to /api/unknown/{id} with an existing user ID (e.g., GET /api/unknown/2).
   
2.	Check that the response status code is 200 OK.

   Tests in Postman:

        //assertion test to verify response status
        pm.test("Status code is 200", function () {
            pm.response.to.have.status(200);
        });

•	Test Case 6: GET /api/unknown/{id}

o	Objective: Verify that the API does not return color resource with indicated ID.

o	Test Steps:

1.	Send a GET request to /api/unknown/{id} with a non existing user ID (e.g., GET /api/unknown/23).
   
2.	Verify the response status code is 404 Not Found.
   
 Tests in Postman:

        //assertion test to verify response status
        pm.test("Status code is 404", function () {
            pm.response.to.have.status(404);
        });

•	Test Case 7: POST /api/users

o	Objective: Verify that the API creates a new user.

o	Test Steps:

1.	Send a POST request to /api/users with valid data in the request body (e.g., { "name": "morpheus", "job": "leader" }).
   
2.	Verify the response status code is 201 or 202 Created.
   
3.	Check that the response contains the name and job fields, and their values are correct.

  Tests in Postman:

        //assertion test to verify response status
        pm.test("Successful POST request", function () {
            pm.expect(pm.response.code).to.be.oneOf([201, 202]);
        });
        //checks that the response includes name and job fields with specific values ('morpheus' and 'leader'), to confirm the API correctly 
        returned or accepted user details—often used after a POST or PUT request
        pm.test("Response contains user details", function () {
            var jsonData = pm.response.json();
            pm.expect(jsonData).to.have.property('name', 'morpheus');
            pm.expect(jsonData).to.have.property('job', 'leader');
        });

•	Test Case 8: PUT /api/users/{id}

o	Objective: Verify that the API updates an existing user.

o	Test Steps:

1. Send a PUT request to /api/users/{id} with valid updated data in the request body (e.g., { "name": "morpheus", "job": "zion resident" }).

2. Verify the response status code is 200 OK.

3. Check that the response contains the updated name and job fields with their expected values.

  Tests in Postman:

       //assertion test to verify response status
       pm.test('Status code is 200', function () {
           pm.response.to.have.status(200);
       });
       //checks that the response includes name and job fields with specific values ('morpheus' and 'zion resident'), to confirm the API 
       correctly returned or accepted user details—often used after a POST or PUT request
       pm.test("Response contains updated user details", function () {
           var jsonData = pm.response.json();
           pm.expect(jsonData).to.have.property('name', 'morpheus');
           pm.expect(jsonData).to.have.property('job', 'zion resident');
       });

•	Test Case 9: PATCH /api/users/{id}

o	Objective: Verify that the API correctly updates the user resource when sending a PATCH request to /api/users/{id} with valid data.

o	Test Steps:

1. Send a PATCH request to /api/users/{id} with an existing user ID (e.g., /api/users/2) and a valid request body.

2. Check that the response status code is 200 OK.

  Tests in Postman:

       //assertion test to verify response status
       pm.test('Status code is 200', function () {
           pm.response.to.have.status(200);
       });


Other test steps and Postman tests will be added later.




