# Todo list Web API + user interface Assessment

The goal of this assessment is to implement a todolist backend (API) and/or frontend (UI). The result will then be submitted for code review in order to establish your software engineering level.

## General Recommendations

- Please put your code on a Git host like Github/Gitlab/Bitbucket etc.
- Please provide clear steps on how to run your application in a README.md.
- Use a package manager (npm/yarn/pip/poetry/pipenv/composer etc...) and do **not** commit/upload your third party dependencies.
- Write some tests (a medior programmer should know how to do this properly)
- Dockerize your application if you are applying to a DevOps related role.
- Tip: Write code in the way you are already used to do, this assessment is about seeing what you already know, not about learning new stuff.
- For the backend exercise: The reviewer will run your code in order to determine how well you implemented the API spec

## Backend exercise: Implement Todo List Web API

Implement the API specified on the bottom of the page.

## Frontend exercise: create a user interface for Todo List Web API

Implement a UI against the API specified at the bottom of the page.
Use https://todo-api.niveaubepaling.nl to develop your user interface against.

## Fullstack exercise: implement both Web API + user interface

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

## Web API specification

| method | uri                     | description                            | request body                                                                                                                                      | response body                                                                                       | success http status code |
| ------ | ----------------------- | -------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | ------------------------ |
| POST   | /list                   | Add a new list                         | `{"name": "the name of your list"}`                                                                                                               | `{"data": {"id": 0}}`                                                                               | 201                      |
| GET    | /list/{listId}          | Get a list by id                       | N/A                                                                                                                                               | `{"data": {"name": "Grocery List", "createdAt": "2021-06-28T12:35:12.025Z", "items": []}}`          | 200                      |
| GET    | /list                   | Get all lists (think about pagination) | N/A                                                                                                                                               | `{"data": [{"id": 0, "name": "Grocery List"}, {"id": 1, "name": "Another List"}]}`                  | 200                      |
| PATCH  | /list/{listId}          | Update list details                    | `{"name": "some new name of your list"}`                                                                                                          | `{"data": {"name": "Grocery Shopping List", "createdAt": "2021-06-28T12:35:12.025Z", "items": []}}` | 200                      |
| DELETE | /list/{listId}          | Delete list                            | N/A                                                                                                                                               | `{}`                                                                                                | 200                      |
| POST   | /list/{listId}          | Add new item to list                   | `{"name": "the name of your item"}`                                                                                                               | `{"data": {"id": 0, "name": "Buy Apples", "completed": false}}`                                     | 201                      |
| GET    | /list/{listId}/{itemId} | Get single item                        | N/A                                                                                                                                               | `{"data": {"id": 0, "name": "Buy Apples", "completed": false}}`                                     | 200                      |
| PATCH  | /list/{listId}/{itemId} | Update item details                    | `{"name": "the name of your item", "completed" :true}` Fields `name` and `completed` are both optional but at least one of them has to be present | `{"data": {"id": 0, "name": "Buy Apple", "completed": true}}`                                       | 200                      |
| DELETE | /list/{listId}/{itemId} | Delete item                            | N/A                                                                                                                                               | `{}`                                                                                                | 200                      |
