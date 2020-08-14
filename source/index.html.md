---
title: SGS-ODP API Reference

# language_tabs: # must be one of https://git.io/vQNgJ
#   # - shell
#   # - ruby
#   # - python
  - javascript

toc_footers:
  # - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true
---

# Introduction

Welcome to the SGS-ODP API! You can use our API to access SGS-ODP API endpoints, which can get information on graduate student development plans in our database.

<!-- We have language bindings in Shell, Ruby, Python, and JavaScript!  -->
<!-- You can view code examples in the dark area to the right. -->
<!-- , and you can switch the programming language of the examples with the tabs in the top right. -->

This API documentation page was created with [Slate](https://github.com/slatedocs/slate).

# Authentication

> To authorize, use this code:

<!-- ```ruby
require 'SGS-ODP'

api = SGS-ODP::APIClient.authorize!('scarletknightsthrive')
``` -->

<!-- ```python
import SGS-ODP

api = SGS-ODP.authorize('scarletknightsthrive')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: scarletknightsthrive"
``` -->

```javascript
const SGS-ODP = require('SGS-ODP');

let api = SGS-ODP.authorize('scarletknightsthrive');
```

> Make sure to replace `scarletknightsthrive` with your API key.

SGS-ODP uses API keys to allow access to the API once a user has logged in with CAS.

SGS-ODP expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer 
scarletknightsthrive`

<aside class="notice">
You must replace <code>scarletknightsthrive</code> with your personal API key.
</aside>

# Users

## Get All Users
<!-- 
```ruby
require 'SGS-ODP'

api = SGS-ODP::APIClient.authorize!('scarletknightsthrive')
api.students.get
```

```python
import SGS-ODP

api = SGS-ODP.authorize('scarletknightsthrive')
api.students.get()
```

```shell
curl "http://example.com/api/students"
  -H "Authorization: scarletknightsthrive"
``` -->
```javascript
const SGS-ODP = require('SGS-ODP');

let api = SGS-ODP.authorize('scarletknightsthrive');
let students = api.users.get();
```
> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "netId": "pw0001",
    "firstName": "Phillis",
    "lastName": "Wheatley",
    "email": "apoet@youshouldknow.com", 
    "role": 'student'
  },
  {
    "id": 2,
    "netId": "mjp0001",
    "firstName": "Mary Jane",
    "lastName": "Patterson",
    "email": "ascholar@youshouldknow.com",
    "role": ['faculty', 'administrator']
  }
]
```

This endpoint retrieves all users and is only accessible by administrators.

### HTTP Request

`GET http://example.com/api/users`

## Get a Specific User
<!-- ```ruby
require 'SGS-ODP'

api = SGS-ODP::APIClient.authorize!('scarletknightsthrive')
api.students.get(2)
```

```python
import SGS-ODP

api = SGS-ODP.authorize('scarletknightsthrive')
api.students.get(2)
```

```shell
curl "http://example.com/api/students/2"
  -H "Authorization: scarletknightsthrive"
``` -->
```javascript
const SGS-ODP = require('SGS-ODP');

let api = SGS-ODP.authorize('scarletknightsthrive');
let mary = api.users.get(2);
```

> The above command returns JSON structured like this:

```json
{
    "id": 3,
    "netId": "mem0001",
    "firstName": "Mary Eliza",
    "lastName": "Mahoney",
    "email": "anurse@youshouldknow.com",
    "role": "student"
  }
```

This endpoint retrieves a specific user.



### HTTP Request

`GET http://example.com/users/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the student to retrieve


## Update a Specific User

```javascript
const SGS-ODP = require('SGS-ODP');

let api = SGS-ODP.authorize('scarletknightsthrive');
let mary = api.users.put(3);
```

> The above command returns JSON structured like this:

```json
{
    "message": 'User updated successfully.'
  }
```

This endpoint updates a specific user.  It expects the user id in the path and for the request body to include information to be updated.  

### HTTP Request

`PUT http://example.com/users/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the student to retrieve

## Create a User
```javascript
const SGS-ODP = require('SGS-ODP');

let api = SGS-ODP.authorize('scarletknightsthrive');
let mary = api.users.post();
```

> The above command returns JSON structured like this:

```json
{
    "id": 4,
    "netId": "mlw0001",
    "firstName": "Maggie Lena",
    "lastName": "Walker",
    "email": "abankpresident@youshouldknow.com", 
    "role": "faculty"
  }
```

This endpoint creates a user record in the database.  It expects the netId, firstName, lastName, and email to be included in the request body.


### HTTP Request

`POST http://example.com/users`


## Delete a Specific User
<!-- ```ruby
require 'SGS-ODP'

api = SGS-ODP::APIClient.authorize!('scarletknightsthrive')
api.students.delete(2)
```

```python
import SGS-ODP

api = SGS-ODP.authorize('scarletknightsthrive')
api.students.delete(2)
```

```shell
curl "http://example.com/api/students/2"
  -X DELETE
  -H "Authorization: scarletknightsthrive"
``` -->
```javascript
const SGS-ODP = require('SGS-ODP');

let api = SGS-ODP.authorize('scarletknightsthrive');
let max = api.users.delete(5);
```

> The above command returns JSON structured like this:

```json
{
  "id": 5,
  "deleted" : ":("
}
```

This endpoint deletes a specific user.

### HTTP Request

`DELETE http://example.com/users/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the user to delete


# Students

## Get All Students

```javascript
const SGS-ODP = require('SGS-ODP');

let api = SGS-ODP.authorize('scarletknightsthrive');
let students = api.students.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 10,
    "netId": "cc0001",
    "admissionSemester": "F20",
    "admissionYear": 2020,
    "department": 1,
    "program": 6,
    "advisor": 7
  },
  {
    "id": 11,
    "netId": "cct0001",
    "admissionSemester": "S20",
    "admissionYear": 2020,
    "department": 1,
    "program": 6,
    "advisor": 7
  }
]
```
This endpoint retrieves all students and is only accessible by administrators.

### HTTP Request

`GET http://example.com/api/students`


## Get a Specific Student

```javascript
const SGS-ODP = require('SGS-ODP');

let api = SGS-ODP.authorize('scarletknightsthrive');
let max = api.students.get(11);
```

> The above command returns JSON structured like this:

```json
{
    "id": 11,
    "netId": "cct0001",
    "admissionSemester": "S20",
    "admissionYear": 2020,
    "department": 1,
    "program": 6,
    "advisor": 7
  }
```

This endpoint retrieves a specific student.

### HTTP Request

`GET http://example.com/students/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the student to retrieve

## Update a Specific Student

```javascript
const SGS-ODP = require('SGS-ODP');

let api = SGS-ODP.authorize('scarletknightsthrive');
let mary = api.students.put(3);
```

> The above command returns JSON structured like this:

```json
{
    "message": 'Student updated successfully.'
  }
```

This endpoint updates a specific user.  It expects the student id in the path and for the request body to include information to be updated.  

### HTTP Request

`PUT http://example.com/students/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the student to retrieve

## Create a Student
```javascript
const SGS-ODP = require('SGS-ODP');

let api = SGS-ODP.authorize('scarletknightsthrive');
let mary = api.students.post();
```

> The above command returns JSON structured like this:

```json
{
    "id": 11,
    "netId": "cct0001",
    "admissionSemester": "S20",
    "admissionYear": 2020,
    "department": 1,
    "program": 6,
    "advisor": 7
  }
```

This endpoint creates a user record in the database.  It expects the netId, admissionSemester, admissionYear, department id, program id, and advisor id to be included in the request body.


### HTTP Request

`POST http://example.com/students`



## Delete a Specific Student

```javascript
const SGS-ODP = require('SGS-ODP');

let api = SGS-ODP.authorize('scarletknightsthrive');
let max = api.students.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific student.

### HTTP Request

`DELETE http://example.com/students/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the student to delete


# Programs

## Get All Programs

```javascript
const SGS-ODP = require('SGS-ODP');

let api = SGS-ODP.authorize('scarletknightsthrive');
let programs = api.programs.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 101,
    "name": "Ecology and Evolution",
    "description": ""
  },
  {
    "id": 110,
    "name": "Computer Science - Data Science",
    "description": ""
  }
]
```
This endpoint retrieves all programs.

### HTTP Request

`GET http://example.com/api/programs`


## Get a Specific Program

```javascript
const SGS-ODP = require('SGS-ODP');

let api = SGS-ODP.authorize('scarletknightsthrive');
let max = api.programs.get(110);
```

> The above command returns JSON structured like this:

```json
{
    "id": 110,
    "name": "Computer Science - Data Science",
    "description": ""
  }
```

This endpoint retrieves a specific program.

### HTTP Request

`GET http://example.com/programs/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the program to retrieve

## Update a Specific Program

```javascript
const SGS-ODP = require('SGS-ODP');

let api = SGS-ODP.authorize('scarletknightsthrive');
let mary = api.programs.put(3);
```

> The above command returns JSON structured like this:

```json
{
    "message": 'Program updated successfully.'
  }
```

This endpoint updates a specific program.  It expects the program id in the path and for the request body to include information to be updated.  

### HTTP Request

`PUT http://example.com/programs/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the program to retrieve

## Create a Program
```javascript
const SGS-ODP = require('SGS-ODP');

let api = SGS-ODP.authorize('scarletknightsthrive');
let mary = api.programs.post();
```

> The above command returns JSON structured like this:

```json
{
    "id": 111,
    "name": "Education - Ph.D.",
    "description": ""
  }
```

This endpoint creates a program record in the database.  It expects the name of the program to be included in the request body.


### HTTP Request

`POST http://example.com/programs`



## Delete a Specific Program

```javascript
const SGS-ODP = require('SGS-ODP');

let api = SGS-ODP.authorize('scarletknightsthrive');
let max = api.programs.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific program.

### HTTP Request

`DELETE http://example.com/programs/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the program to delete



# Departments

## Get All Departments

```javascript
const SGS-ODP = require('SGS-ODP');

let api = SGS-ODP.authorize('scarletknightsthrive');
let departments = api.departments.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 101,
    "name": "Animal Sciences",
    "description": ""
  },
  {
    "id": 110,
    "name": "Marine and Coastal Sciences",
    "description": ""
  }
]
```
This endpoint retrieves all departments.

### HTTP Request

`GET http://example.com/api/departments`


## Get a Specific Department

```javascript
const SGS-ODP = require('SGS-ODP');

let api = SGS-ODP.authorize('scarletknightsthrive');
let max = api.departments.get(110);
```

> The above command returns JSON structured like this:

```json
{
    "id": 110,
    "name": "Marine and Coastal Sciences",
    "description": ""
  }
```

This endpoint retrieves a specific department.

### HTTP Request

`GET http://example.com/departments/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the department to retrieve

## Update a Specific Department

```javascript
const SGS-ODP = require('SGS-ODP');

let api = SGS-ODP.authorize('scarletknightsthrive');
let mary = api.departments.put(3);
```

> The above command returns JSON structured like this:

```json
{
    "message": 'Department updated successfully.'
  }
```

This endpoint updates a specific department.  It expects the department id in the path and for the request body to include information to be updated.  

### HTTP Request

`PUT http://example.com/departments/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the department to retrieve

## Create a Department
```javascript
const SGS-ODP = require('SGS-ODP');

let api = SGS-ODP.authorize('scarletknightsthrive');
let mary = api.departments.post();
```

> The above command returns JSON structured like this:

```json
{
    "id": 110,
    "name": "Marine and Coastal Sciences",
    "description": ""
  }
```

This endpoint creates a department record in the database.  It expects the name of the department to be included in the request body.


### HTTP Request

`POST http://example.com/departments`



## Delete a Specific Department

```javascript
const SGS-ODP = require('SGS-ODP');

let api = SGS-ODP.authorize('scarletknightsthrive');
let max = api.departments.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific department.

### HTTP Request

`DELETE http://example.com/departments/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the department to delete

