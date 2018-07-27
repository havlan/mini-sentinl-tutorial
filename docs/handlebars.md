# Handlebars tutorial

- [Handlebars tutorial](#handlebars-tutorial)
  - [Example payloads](#example-payloads)
  - [Accessing data](#accessing-data)
      - [Example](#example)

## Example payloads

- In this tutorial I will be using different payloads in order to cover the most common use cases.
- Example output from a request:

```json
{
    "responses": [
        {
            "took": 2,
            "timed_out": false,
            "_shards": {
                "total": 20,
                "successful": 20,
                "skipped": 0,
                "failed": 0
            },
            "hits": {
                "total": 76,
                "max_score": 0.0,
                "hits": []
            },
            "aggregations": {
                "2": {
                    "doc_count_error_upper_bound": 0,
                    "sum_other_doc_count": 0,
                    "buckets": [
                        {
                            "key": "uib_hr_wt",
                            "doc_count": 74
                        },
                        {
                            "key": "uib_alice",
                            "doc_count": 2
                        }
                    ]
                }
            },
            "status": 200
        }
    ]
}
```

## Accessing data

- Handlebars uses ```{{data}}``` to access attributes
  - The same is required to access json like structures, but then to access correct information you have to "navigate" to the correct attribute, e.g. ```{{payload.hits.total}}```
- In this case with out example data ```{{payload.hits.total}}``` would result in the message ```76```
<!-- An iteration over buckets could be done in this style:
  
  {{#each item in payload.aggregations['2'].buckets}}
    Key: {{item.key}}, Count: {{item.doc_count}}
  {{/each}}

   -->



#### Example
- Scenario: Watcher is almost done, it counts the number affected by a query, it's important to include enough information so that the user can determine whether if it's critical or not.
- Example message body: ```Watcher: JVM heap space on ES cluster alert triggered, value is: {{payload.hits.total}}. Check your dashboard now!```

