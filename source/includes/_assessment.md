# Assesssment

An assessment object is composed of the following attributes:

1. `objective`. This can be derived from a `curriculum` or a `pedagogy`.

2. `learner`. The person who is being assessed.

3. `assessor`. The person or activity who is assessing the learner.

4. `score`. A decimal representation of the learner's achievement, e.g. 0.6.

5. `rating_scale`. The key of the rating scale used to define and interpret the score. A score of 0.6, for example, might be interpreted as a percentage (60%), a fraction (3/5) or a string ('Apprentice').

6. `notes`. Free text for the assessor to record observations, comments, etc.

## Create an Assessment
> Returns the following json:

```json
{
  "assessment": "a-unique-identifier-for-the-assessment",
  "created": "2014-07-01T10:59:51.357Z"
}
```

### HTTP Request

`POST https://toolsforteachers.org.uk/api/v1/asessment/`

### Parameters

Parameter | Type | Description
--------- | ----- | ----------
objective | String | Objective#key
learner | String | Learner#key or an email address
score | Float | Less than or equal to 1. Use 0 for non-participation.
rating_scale | String | RatingScale#key (optional). Defaults to the authenticated user's preferred rating scale.
notes | String | Free text (optional)

## Update an Assessment
> Returns the following json:

```json
{
  "assessment": "a-unique-identifier-for-the-assessment",
  "updated": "2014-07-01T10:59:51.357Z"
}
```

### HTTP Request

`PATCH https://toolsforteachers.org.uk/api/v1/asessments/a-unique-identifier-for-the-assessment`

### Parameters

Parameter | Type | Description
--------- | ----- | ----------
score | Float | Less than or equal to 1. Use 0 for non-participation.
