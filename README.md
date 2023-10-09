# Robust server structure: API testing with Supertest

## Instructions
You're given an API server that is fully working with three distinct routes, a not-found handler, and an error handler. However, the developer who created this API missed a few key tests, so you've been tasked this sprint with writing these additional tests to ensure adequate test coverage for the most essential features of the API.

To pass this assessment, you will need to write tests for a few API endpoints, as described below.

Complete the following tasks to pass the tests and this assessment.

## Existing files
| File path |	Description |
| ---- | ---- |
| src/app.js |	Contains the code for the express application. You don't need to edit this file. |
| src/server.js |	Contains the code to start the express application. You don't need to edit this file. |
| src/data/todos-data.js |	Stores several todos used as the initial todos data for app.js. Feel free to add or remove data as necessary, but keep the same shape of the data. |
| test/app.test.js |	Contains the tests your code will run against. You will need to add your tests to this file. |

## Tasks
In the app.test.js file, you will write tests to:
1. Ensure that the POST /todos endpoint handles a request containing the todo data by
- assigning a new id to the note
- storing the note
- and returning a 201 status code and the stored note as JSON on success
2. Ensure that the POST /todos endpoint returns a 400 status code if the title property is missing or empty in the incoming request body
3. Ensure that the GET /todos/:todoId handler returns an error if the :todoId does not exist
4. Ensure that the API returns the correct error message if the user tries to visit a route that is not defined:
`Not found: ${req.originalUrl}`;
Note: If you are having trouble getting your tests to pass but you think you've gotten it right, make sure to check for punctuation and spelling. The tests are looking for exact string matches.

## Existing routes
The server contains the following routes:

**GET /todos**
This route will respond to a GET request with an array of existing todos. Here's an example:

{
  "data": [
    {
      "id": 1,
      "title": "Take out the trash",
      "completed": false
    },
    {
      "id": 2,
      "title": "Clean the windows",
      "completed": false
    },
  ]
}

- If a todo is added, it is included in the array returned by this route.

**POST /todos**
This route responds to a POST request and creates a new todo if the request is valid.

**GET /todos/:todoId**
This route responds to a GET request with the todo for the provided todoId.
- If the todoId matches an existing todo, it responds with the todo.
- If the todoId doesn't match an existing note, respond with the following message.
`Todo id not found: ${req.params.todoId}`;

## Error handling
If the user goes to a route that isn't defined, the server responds with the following message:
`Not found: ${req.originalUrl}`;