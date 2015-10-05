---
title: API Reference

toc_footers:
  - <a href='mailto:admin@toolsforteachers.org.uk'>Request a Developer Key</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Tools for Teachers API. You can use our API to access endpoints that are implemented in the Tools for Teachers web app.

# Authentication

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: your-api-key"
```

> Make sure to replace `your-api-key` with your API key.

Tools for Teahers uses API keys to allow access to the API. You can request a new API key by email [admin@toolsforteachers.org.uk](admin@toolsforteachers.org.uk).

Tools for Teachers expects the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: your-api-key`

<aside class="notice">
You must replace <code>your-api-key</code> with your personal API key.
</aside>

# Curricula

## Get a list of the available Curricula

```shell
curl "https://toolsforteachers.org.uk/api//v1/curricula"
  -H "Authorization: your-api-key"
```

> The above command returns JSON structured like this:

```json
[
  {
    "key": "national-curriculum-in-england",
    "name": "National Curriculum in England",
    "createdBy": "John Doe"
  },
  {
    "key": "open-water-scuba-diving",
    "name": "Open Water Scuba Diving",
    "createdBy": "Jack Custow"
  }
]
```

This endpoint retrieves all available curricula

### HTTP Request

`GET https://toolsforteachers.org.uk/api/v1/curricula`


## Get a specific Curriculum

```shell
curl "https://toolsforteachers.org.uk/api/v1/curricula/national-curriculum-in-england"
  -H "Authorization: your-api-key"
```

> The above command returns JSON structured like this:

```json
{
 WIP: json-to-retrieve
}
```

This endpoint retrieves a specific curricuculm.


### HTTP Request

`GET https://toolsforteachers.org.uk/api/v1/curricula/<key>`

### URL Parameters

Parameter | Description
--------- | -----------
key | The key of the curriculum to retrieve

