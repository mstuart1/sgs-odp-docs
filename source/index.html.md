---
title: SGS-ODP API Reference

# language_tabs: # must be one of https://git.io/vQNgJ
#   # - shell
#   # - ruby
#   # - python
#   - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
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

```ruby
require 'SGS-ODP'

api = SGS-ODP::APIClient.authorize!('scarletknightsthrive')
```

```python
import SGS-ODP

api = SGS-ODP.authorize('scarletknightsthrive')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: scarletknightsthrive"
```

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

This endpoint retrieves all users and is only accessible by administrators.

### HTTP Request

`GET http://example.com/api/users`




# Students

## Get All Students

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
```

```javascript
const SGS-ODP = require('SGS-ODP');

let api = SGS-ODP.authorize('scarletknightsthrive');
let students = api.students.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```



## Get a Specific Student

```ruby
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
```

```javascript
const SGS-ODP = require('SGS-ODP');

let api = SGS-ODP.authorize('scarletknightsthrive');
let max = api.students.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific student.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/students/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the student to retrieve

## Delete a Specific Student

```ruby
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
```

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

