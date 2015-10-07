# Learner
Learners are identified by their system-generated key or an email address.

## Add a Learner
> Returns the following json:

``` json
{
  "learner": "a-system-generated-key-for-the-learner",
  "created": "2014-07-01T10:59:51.357Z"
}
```

### HTTP Request

`POST https://toolsforteachers.org.uk/api/v1/learners`

Parameter | Type | Description
----------| -----|------------
name | String | Display name
email | String | Email address

## Update a Learner
> Returns the following json:

``` json
{
  "learner": "a-system-generated-key-for-the-learner",
  "updated": "2014-07-01T10:59:51.357Z"
}
```

### HTTP Request

`PATCH https://toolsforteachers.org.uk/api/v1/learners/:key`

Parameter | Type | Description
----------| -----|------------
name | String | Display name
email | String | Email address


## Get a Learner Assessment Record
> Returns the following json:

``` json
{
  "learner": "learner-key",
  "assessments":
  [
    {
      "assessor": "assessor-key",
      "score": 0.6,
      "notes": "Lipsum ipsum lorem et al",
      "rating_scale": "rating-scale-key",
      "mark": 3,
      "out_of": 5,
      "objective":
       {
        "curriculum": "National Curriculum in England",
        "subject": "Maths",
        "level": "Year 6",
        "topic": "Algebra",
        "name": "Use simple formula",
        "key": "use-simple-formula"
      },
      "posted_at": "updated-or-created-date"
    }
  ]
}
```
Retrieves learner assessents, most recent first. Includes additional fields to help UI display:

1. `mark`. The score as a representation of the rating scale.

2. `out_of`. The highest achievable score as a representation of the rating scale.

3. `objective_attributes`. The complete attribute set for the objective

4. `posted_at`. Timestamp when the record was created or updated.

### HTTP Request

`GET https://toolsforteachers.org.uk/api/v1/learners/:key`

### URL Parameters

Parameter | Description
----------|------------
limit | Maximum number of records (optional). Defaults to 20.
objective | Filter by an objective (optional). Retrieves all objectives by default.
