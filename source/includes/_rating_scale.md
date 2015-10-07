# Rating Scale

## Get all Rating Scales

> Returns the following json:

``` json
[
  {
    "name": "Likert",
    "key": "rating-likert",
    "max_score": 5,
    "ordinals":
      [
        {
          "name": "N/A",
          "value": 0
        },
        {
          "name": "Strongly disagree",
          "value": 1
        },
        {
          "_etc": "..."
        }
      ]

  }
]
```

### HTTP Request
`GET https://toolsforteachers.org.uk/api/v1/rating-scales`

The rating scale is composed of:

1. `name`. A description given by the editor.

2. `ordinals`. An ordered list of the `name` and `value` that describes the score.

3. `max_score`. The maximum score that can be achieved.

4. `key`. A system generated unique identifier.

<aside class='notice'>
  A note about ordinals. The `value` attribute is the basis of the scoring system and is always numeric. The `name` attribute is an optional descriptor, intended to enhance the UI display.
</aside>

## Set Default Rating Scale

> Returns the following json:

``` json
{
  "default_rating_scale": "rating-scale-key"
}
```

### HTTP Request
`PATCH https://toolsforteachers.org.uk/api/v1/rating-scales/default/<rating-scale-key>`



An assessor can set the default rating scale that will be used in all assessment activities. Note that this setting can be overwritten when an assessment is recorded.


