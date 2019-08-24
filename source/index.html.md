---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Event Board API! You can use our API to access Event Board API endpoints, which can create events, register to attend other events, and see all upcoming events in our database.

We have language bindings in Shell, Ruby, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This API documentation page was created with [Slate](https://github.com/lord/slate).

# Authentication

> To authorize, use this code:

```ruby
require 'eventboard'

api = Event Board::APIClient.authorize!('json-web-token')
```

```python
import eventboard

api = eventboard.authorize('json-web-token')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: json-web-token"
```

```javascript
const eventboard = require('eventboard');

let api = eventboard.authorize('json-web-token');
```

> Make sure to replace `"json-web-token"` the json web token sent on login.

Event Board uses json web tokens to authenticate users. You can register a new Event Board API key at our [developer portal](http://api.eventboard.com/developers).

Event Board expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: json-web-token`

<aside class="notice">
You must replace <code>json-web-token</code> with the web token returned from the "/login" endpoint.
</aside>

# Events

## Get All Events

```ruby
require 'eventboard'

api = Event Board::APIClient.authorize!('json-web-token')
api.events.get
```

```python
import eventboard

api = eventboard.authorize('json-web-token')
api.events.get()
```

```shell
curl --location --request POST "http://api.eventboard.com/api/events"
  --header "Authorization: json-web-token"
```

```javascript
const eventboard = require('eventboard');

let api = eventboard.authorize('json-web-token');
let events = api.events.get();
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Ruby Meetup",
    "description": "A meetup for Ruby developers of all skill levels.",
    "start": 1566507630,
    "end": 1569517650,
    "lat": 43.638365132,
    "long": -79.43534586,
    "userId": 7,
    "categoryId": 1,
  },
  {
    "id": 2,
    "name": "Tech Networking Mixer",
    "description": "A meetup for tech industry professionals",
    "start": 1366507630,
    "end": 1669517650,
    "lat": 43.638561,
    "long": -79.435548151,
    "userId": 10,
    "categoryId": 3,
  }
]
```

This endpoint retrieves all events.

### HTTP Request

`GET http://api.eventboard.com/api/events`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include events that have already been adopted.

<aside class="success">
Remember — a happy user is an authenticated user!
</aside>

## Get a Specific Event

```ruby
require 'eventboard'

api = Event Board::APIClient.authorize!('json-web-token')
api.events.get(2)
```

```python
import eventboard

api = eventboard.authorize('json-web-token')
api.events.get(2)
```

```shell
curl "http://api.eventboard.com/api/events/2"
  -H "Authorization: json-web-token"
```

```javascript
const eventboard = require('eventboard');

let api = eventboard.authorize('json-web-token');
let max = api.events.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 1,
  "name": "Ruby Meetup",
  "description": "A meetup for Ruby developers of all skill levels.",
  "start": 1566507630,
  "end": 1569517650,
  "lat": 43.638365132,
  "long": -79.43534586,
  "userId": 7,
  "categoryId": 1,
}
```

This endpoint retrieves a specific event.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://api.eventboard.com/events/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the event to retrieve

## Delete a Specific Event

```ruby
require 'eventboard'

api = Event Board::APIClient.authorize!('json-web-token')
api.events.delete(2)
```

```python
import eventboard

api = eventboard.authorize('json-web-token')
api.events.delete(2)
```

```shell
curl "http://api.eventboard.com/api/events/2"
  -X DELETE
  -H "Authorization: json-web-token"
```

```javascript
const eventboard = require('eventboard');

let api = eventboard.authorize('json-web-token');
let max = api.events.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific event.

### HTTP Request

`DELETE http://api.eventboard.com/events/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the event to delete

