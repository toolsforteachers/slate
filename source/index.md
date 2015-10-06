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

# Curriculum

## Get all available Curricula

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

It should be noted that a curriculum has the following hierarchical attributes.

1. Subject (e.g. *Maths*)
2. Level (e.g. *Year 6*)
3. Topic (e.g. *Algebra*)
4. Prompt (if defined, e.g. *Students are expected to*)
4. Objective (e.g. *Enumerate possibilities of combinations of 2 variables*)

### HTTP Request

`GET https://toolsforteachers.org.uk/api/v1/curricula`


## Get a Curriculum Description

> Note that the attributes to be returned are defined by the `depth` parameter.

```json
{
"key": "national-curriculum-in-england",
"name": "National Curriculum in England",
"editor": "John Doe",

"subjects":
  [
    {
      "name": "Maths",
      "key": "national-curriculum-maths",
      "levels":
        [
          {
            "name": "Year 5",
            "key": "maths-year-5"
          },
          {
            "name": "Year 6",
            "key": "maths-year-6",
            "topics":
              [
                {
                  "name": "Algebra",
                   "key": "maths-year-6-algebra"
                }
              ]
          },
        ]
    }
  ]
}

```

This endpoint retrieves the descriptive attributes of a specific curriculum.

Use the `curriculum-attribute` endpoint to retrieve `objectives`.

The parameter `depth` determines which attributes are retrieved for that curriculum. Choosing `level`, for example, will retrieve Subject and Level attributes.


### HTTP Request

`GET https://toolsforteachers.org.uk/api/v1/curricula/<key>`

### URL Parameters

Parameter | Description
--------- | -----------
key | The key of the curriculum to retrieve
depth | Choose from `subject`, `level` or `topic`. Defaults to `level` (optional)

## Get Curriculum Objectives

> This example json would be returned from a request for a `topic` attribute,

```json
{
"finder": "maths-year-6-algebra",
"objectives":
  [
    {
      "curriculum": "National Curriculum in England",
      "subject": "Maths",
      "level": "Year 6",
      "topic": "Algebra",
      "prompt": "Students are expected to:",
      "name": "Enumerate possibilities of combinations of 2 variables",
      "key": "enumerate-possibilities-of-combinations-of-2-variables"
    },
    {
      "curriculum": "National Curriculum in England",
      "subject": "Maths",
      "level": "Year 6",
      "topic": "Algebra",
      "name": "Use simple formula",
      "key": "use-simple-formula"
    }
  ]
}
```

This endpoint accepts a key for any attribute in the curriculum attribute hierarchy and returns all the objectives associated with that finder.

### HTTP Request

`GET https://toolsforteachers.org.uk/api/v1/curriculum-objectives/<key>`

### URL Parameters

Parameter | Description
--------- | -----------
key | The key of the curriculum attribute to retrieve. Can be a `subject`, `level`, `topic` or `objective`

# Pedagogy

## Get all available Pedagogies

> The endpoint returns JSON structured like this:

```json
[
  {
    "key": "character-learning-targets-exemplar",
    "name": "Character Learning Targets Exemplar",
    "editor": "John Doe"
  }
]
```

This endpoint retrieves all available pedagogie

### HTTP Request

`GET https://toolsforteachers.org.uk/api/v1/pedagogies`


## Get Pedagogy Objectives

```json
{
"key": "character-learning-targets-exemplar",
"name": "Character Learning Targets Exemplar",
"editor": "John Doe",
"objectives":
  [
    {
      "learning_attribute": "Collaboration and Leadership",
      "learning_skill": "I can engage positively with others",
      "name": "I can walk-my-talk by being a good role model",
      "key": "i-can-walk-my-talk"
    }
  ]
}
```

This endpoint retrieves the objectives of a specific pedagogy.

It should be noted that a pedagogy has the following hierarchical attributes.

1. Learning attribute (e.g. *Collaboration and leadership*)
2. Learning skill (if defined, e.g. *I can engage positively with others*)
4. Objective (e.g. *I can walk-my-talk by being a good role model*)

### HTTP Request

`GET https://toolsforteachers.org.uk/api/v1/pedagogy-objectives/<key>`

### URL Parameters

Parameter | Description
--------- | -----------
key | The key of the pedagogy to retrieve
