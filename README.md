# task-mananger-api

## Scheme:
We'll need at least the following entities to implement the service:

**User**:
| Column | Type |
|--------|------|
| ID | STRING/UUID |
| name | STRING |
| email | STRING |
| password | STRING |
| tokens | [token]|
| Avatar | Buffer |

**Task**:
| Column | Type |
|--------|------|
| description | STRING |
| completed | STRING |
| owner | ObjectId: "User" |

## Server

A simple HTTP server is responsible for authentication, serving stored data, and
potentially ingesting and serving analytics data.

- Node.js is selected for implementing the server for speed of development.
- Express.js is the web server framework.
- Sequelize to be used as an ORM.

### Auth

For v1, a simple JWT-based auth mechanism is to be used, with passwords
encrypted and stored in the database. OAuth is to be added initially or later
for Google + Facebook and maybe others (Github?).

### API

**Auth**:

```
/signIn   [POST]
/signUp   [POST]
/signOut  [POST]
```

**Users**:

```
// Show user
/users/me     [GET] ✅
// Show user by id
/users/:id      [GET] ✅
// Edit patch users
/users/me     [PATCH] ✅
// Delete user
/users/me     [DELETE] ✅
// Change avatar
/users/me/avatar      [POST] ✅
// Show avatat
/users/me/avatar      [GET] ✅
// Edit
/users/edit/:id       [POST] ✅
```


**Tasks**:

```
// Add Task
/tasks     [POST] ✅
// Filter Tasks
// GET completed
/tasks?completed=true      [POST] ✅
// GET by limit & skip
/tasks?limit=10&skip=20     [POST] ✅
// GET sortBy createdAt:desc
/tasks?sortBy=createdAt:desc     [POST] ✅

// Show task by id
/tasks/:id      [GET] ✅
// Edit patch tasks
/tasks/:id     [PATCH] ✅
// Delete task
/tasks/:id      [DELETE] ✅
```
