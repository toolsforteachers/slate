# Metadata

## Get all Curricula

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

1. `subject` (e.g. *Maths*)

2. `level` (e.g. *Year 6*)

3. `topic` (e.g. *Algebra*)

4. `prompt` (if defined, e.g. *Students are expected to*)

5. `objective` (e.g. *Enumerate possibilities of combinations of 2 variables*)

### HTTP Request

`GET https://toolsforteachers.org.uk/api/v1/metadata/curricula`


## Get a Curriculum

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

`GET https://toolsforteachers.org.uk/api/v1/metadata/curricula/<key>`

### URL Parameters

Parameter | Description
--------- | -----------
key | The key of the curriculum to retrieve
depth | Choose from `subject`, `level` or `topic`. Defaults to `level` (optional)

## Get Curriculum Objectives

> This example json would be returned from a request for a `topic` attribute with a key `maths-year-6-algebra`:

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

`GET https://toolsforteachers.org.uk/api/v1/metadata/objectives/<key>`

### URL Parameters

Parameter | Description
--------- | -----------
key | The key of the curriculum attribute to retrieve. Can be a `subject`, `level`, `topic` or `objective`

## Get all Pedagogies

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

This endpoint retrieves all available pedagogies

### HTTP Request

`GET https://toolsforteachers.org.uk/api/v1/metadata/pedagogies`


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

It should be noted that a pedagogy has the following hierarchical attributes:

1. Learning attribute (e.g. *Collaboration and leadership*)
2. Learning skill (if defined, e.g. *I can engage positively with others*)
4. Objective (e.g. *I can walk-my-talk by being a good role model*)

### HTTP Request

`GET https://toolsforteachers.org.uk/api/v1/metadata/objectives/<key>`

### URL Parameters

Parameter | Description
--------- | -----------
key | The key of the pedagogy to retrieve
