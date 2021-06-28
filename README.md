# Todo list API + UI Assessment

The goal of this assessment is to implement a todolist backend (API) and/or frontend (UI). The result will then be submitted for code review in order to establish your software engineering level.

## General Recommendations

- Please put your code on a Git host like Github/Gitlab/Bitbucket etc.
- Please provide clear steps on how to run your application in a README.md. 
- Use a package manager (npm/yarn/pip/poetry/pipenv/composer etc...) and do **not** commit/upload your third party dependencies. 
- Write some tests (a medior programmer should know how to do this properly)
- Feel free to Dockerize your application
- Tip: If you are unsure about new techniques, write code in the way you are used to do, this assessment is about seeing what you already know. Ofcourse you are free to try new technique as well
- For the backend exercise: The reviewer will run your code in order to determine how well you implemented the API spec
- As a last resort you

## Backend exercise: Implement Todo List API

Implement the API specified on the bottom of the page.

## Frontend exercise: create a UI for Todo List API

Implement a UI against the API specified at the bottom of the page.
You will be provided with a development API baseurl to develop against.

## Fullstack exercise: implement both API + UI

Implement the API specified in this document, then implement the UI against that API.

## Bonus exercises:

### Backend
- add authentication to the backend
- Only delete if list is empty, create a force option to force delete a non-empty list
- create an audit trail on a list that keeps track of al mutations of the list itself and it's items

### Frontend
- add authentication to the frontend
- show the audit trail (for frontend-only, the audit-trail is included in the provided development API)
- implement a "move item to another list" by only using POST/DELETE

### DevOps
- Dockerize backend
- Dockerize frontend
- Run in the cloud or on a PaaS.

## API specification

| method | uri                     | description                            | response                                                                                            | success http status code |
| ------ | ----------------------- | -------------------------------------- | --------------------------------------------------------------------------------------------------- | ------------------- |
| POST   | /list                   | Add a new list                         | `{"data": {"id": 0}}`                                                                               |                 201 |
| GET    | /list/{listId}          | Get a list by id                       | `{"data": {"name": "Grocery List", "createdAt": "2021-06-28T12:35:12.025Z", "items": []}}`          |                 200 |
| GET    | /list                   | Get all lists (think about pagination) | `{"data": [{"id": 0, "name": "Grocery List"}, {"id": 1, "name": "Another List"}]}`                  |                 200 |
| PUT    | /list/{listId}          | Update list details                    | `{"data": {"name": "Grocery Shopping List", "createdAt": "2021-06-28T12:35:12.025Z", "items": []}}` |                 200 |
| PUT    | /list/{listId}          | Delete list                            | `{}`                                                                                                |                 200 |
| POST   | /list/{listId}          | Add new item to list                   | `{"data": {"id": 0, "name": "Buy Apples", "status": "todo"}}`                                       |                 200 |
| GET    | /list/{listId}/{itemId} | Get single item                        | `{"data": {"id": 0, "name": "Buy Apples", "status": "todo"}}`                                       |                 200 |
| PUT    | /list/{listId}/{itemId} | Update item details                    | `{"data": {"id": 0, "name": "Buy Apple", "status": "done"}}`                                        |                 200 |
| DELETE | /list/{listId}/{itemId} | Delete item                            | `{}`                                                                                                |                 200 |

