## Blacklist alerting


### Creating a blacklist alert requires some manual editing

- What do you want to blacklist?
- How many hits before triggering an alert?


- In the condition part of a watcher, define it like you normally would with script conditions
- Below are ways of doing it






```json
{
  "script": {
    "script": "payload.hits.total > 0"
  },
  "anomaly": {
    "field_to_check": "http_status",
    "normal_values": [
      200,
      201,
      302
    ]
  }
}
```

- The script below is triggered when this range query hits on http status codes in range [400,600]

```json
{
  "script": {
    "script": "payload.hits.total > 0"
  },
  "range": {
    "field_to_check": "http_status",
    "min": 400,
    "max": 600,
    "tolerance": 0
  }
}

```
