## Threshold alerting

- [Threshold alerting](threshold_alert.md)
- [Anomaly alerting](anomaly_alert.md)
- [Cardinality alerting](cardinality_alert.md)
- [Handlebars](handlebars.md)
- [Frequently asked questions](FAQ.md)


**A threshold is simply a limit (e.g. lower, higher, equals) of your defined query**

#### Examples

##### Single


#### Single date histogram

- Created using date histogram with 3m interval

```json
{
  "took": 3,
  "timed_out": false,
  "_shards": {
    "total": 15,
    "successful": 15,
    "skipped": 0,
    "failed": 0
  },
  "hits": {
    "total": 78,
    "max_score": 0,
    "hits": []
  },
  "aggregations": {
    "2": {
      "buckets": [
        {
          "key_as_string": "2018-06-22T15:54:00.000+02:00",
          "key": 1529675640000,
          "doc_count": 56
        },
        {
          "key_as_string": "2018-06-22T15:57:00.000+02:00",
          "key": 1529675820000,
          "doc_count": 22
        }
      ]
    }
  },
  "status": 200
}

```
- I want to check if the individual bucket count is larger than 50. (Accumulated over 3m)
- Lucene solution:

```json
{
  "array_compare": {
    "payload.aggregations.['2'].buckets": {
      "path": "doc_count",
      "gte": {
        "value": 50
      }
    }
  }
}

```

- Script solution:

```json
{
  "script": {
    "script": "var match=false;var data = payload.aggregations['2'].buckets; for (var i in data) { if(data[i].doc_count > 50){match = true;break;}}match;"
  }
}
```


##### Bucket
- Created with random numbers [1,5]

```json
{
  "responses": [
    {
      "took": 4,
      "timed_out": false,
      "_shards": {
        "total": 15,
        "successful": 15,
        "skipped": 0,
        "failed": 0
      },
      "hits": {
        "total": 2420,
        "max_score": 0,
        "hits": []
      },
      "aggregations": {
        "2": {
          "doc_count_error_upper_bound": 0,
          "sum_other_doc_count": 0,
          "buckets": [
            {
              "key": 1,
              "doc_count": 507
            },
            {
              "key": 4,
              "doc_count": 492
            },
            {
              "key": 3,
              "doc_count": 489
            },
            {
              "key": 5,
              "doc_count": 479
            },
            {
              "key": 2,
              "doc_count": 453
            }
          ]
        }
      },
      "status": 200
    }
  ]
}
```
