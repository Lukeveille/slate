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

api = Event Board::APIClient.authorize!('api-key')
```

```python
import eventboard

api = eventboard.authorize('api-key')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: api-key"
```

```javascript
const eventboard = require('eventboard');

let api = eventboard.authorize('api-key');
```

> Make sure to replace `"api-key"` with your API key.

Event Board uses API keys to allow access to the API. You can register a new Event Board API key at our [developer portal](http://example.com/developers).

Event Board expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: api-key`

<aside class="notice">
You must replace <code>api-key</code> with your personal API key.
</aside>

# Events

## Get All Events

```ruby
require 'eventboard'

api = Event Board::APIClient.authorize!('api-key')
api.events.get
```

```python
import eventboard

api = eventboard.authorize('api-key')
api.events.get()
```

```shell
curl --location --request POST "http://example.com/api/events"
  --header "Authorization: api-key"
```

```javascript
const eventboard = require('eventboard');

let api = eventboard.authorize('api-key');
let events = api.events.get();
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

This endpoint retrieves all events.

### HTTP Request

`GET http://example.com/api/events`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include events that have already been adopted.

<aside class="success">
Remember — a happy event is an authenticated event!
</aside>

## Get a Specific Event

```ruby
require 'eventboard'

api = Event Board::APIClient.authorize!('api-key')
api.events.get(2)
```

```python
import eventboard

api = eventboard.authorize('api-key')
api.events.get(2)
```

```shell
curl "http://example.com/api/events/2"
  -H "Authorization: api-key"
```

```javascript
const eventboard = require('eventboard');

let api = eventboard.authorize('api-key');
let max = api.events.get(2);
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

This endpoint retrieves a specific event.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/events/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the event to retrieve

## Delete a Specific Event

```ruby
require 'eventboard'

api = Event Board::APIClient.authorize!('api-key')
api.events.delete(2)
```

```python
import eventboard

api = eventboard.authorize('api-key')
api.events.delete(2)
```

```shell
curl "http://example.com/api/events/2"
  -X DELETE
  -H "Authorization: api-key"
```

```javascript
const eventboard = require('eventboard');

let api = eventboard.authorize('api-key');
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

`DELETE http://example.com/events/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the event to delete

