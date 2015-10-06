---
title: Tools for Teachers API

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

Tools for Teachers uses API keys to allow access to the API. You can request a new API key by email [admin@toolsforteachers.org.uk](admin@toolsforteachers.org.uk).

Tools for Teachers expects the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: your-api-key`

<aside class="notice">
You must replace <code>your-api-key</code> with your personal API key.
</aside>

# Curricula

## Get a list of the available Curricula

> The endpoint returns JSON structured like this:

```json
[
  {
    "key": "national-curriculum-in-england",
    "name": "National Curriculum in England",
    "editor": "John Doe"
  },
  {
    "key": "open-water-scuba-diving",
    "name": "Open Water Scuba Diving",
    "editor": "Jack Custow"
  }
]
```

This endpoint retrieves all available curricula

### HTTP Request

`GET https://toolsforteachers.org.uk/api/v1/curricula`


## Get a specific Curriculum

> The above command returns JSON structured like this. Note that the attributes returned are defined by the `depth` parameter.

```json
{
 "key": "national-curriculum-in-england",
 "name": "National Curriculum in England",
 "editor": "John Doe",
 "attributes":
  [
    {
      "subject":
        {
          "name": "Maths",
          "key": "national-curriculum-maths"
        },
      "level":
        {
          "name": "Year 6",
          "key": "maths-year-6"
        },
      "topic":
        {
          "name": "Algebra",
          "key": "maths-year-6-algebra"
        },
      "prompt": "Students are expected to:",
      "objective":
        {
          "name": "Enumerate possibilities of combinations of 2 variables",
          "key": "enumerate-possibilities-of-combinations-of-2-variables"
        }
    }
  ]
}
```

This endpoint retrieves the details of a specific curriculum.

It should be noted that curriculum has the following hierarchical attributes.

1. Subject (e.g. *Maths*)
2. Level (e.g. *Year 6*)
3. Topic (e.g. *Algebra*)
4. Prompt (optional descriptive text, e.g. *Students are expectected to*)
4. Objective (e.g. *Enumerate possibilities of combinations of 2 variables*)

The parameter `depth` determines which attributes are retrieved for that curriculum. Choosing `topic`, for example, will retrieve Subject, Level and Topic attributes.

Note that choosing `objective` might return a large, unwieldy dataset.

### HTTP Request

`GET https://toolsforteachers.org.uk/api/v1/curricula/<key>`

### URL Parameters

Parameter | Description
--------- | -----------
key | The key of the curriculum to retrieve
_depth | Choose from `subject`, `level`, `topic`, `objective`. Defaults to `subject` (optional)
