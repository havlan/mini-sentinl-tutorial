## Anomaly alerting

- Below is a condition to check for a field called mos which is random integer [1,8]
- Leaving the condition like this the watcher would use the [68-95-99_7 rule](https://en.wikipedia.org/wiki/68%E2%80%9395%E2%80%9399.7_rule), as a way to check for anomalies.
-


```json
{
  "script": {
    "script": "payload.hits.total > 0"
  },
  "anomaly": {
    "field_to_check": "mos"
  }
}
```

- Unfortunately there is no specific way to pass useful information to the body of the email or similar
- It's up to the individual user to create reasonable alert bodies

```json
ANOMALY ALERT on index: mos-* !
```

- Another way to do this is by specifying normal values
  - Lets say this index contains logs of http status codes
  - Alerts when there has been 10000 non 200 responses from the query

```json
{
  "script": {
    "script": "payload.hits.total > 10000"
  },
  "anomaly": {
    "field_to_check": "http_status",
    "normal_values": [
      200
    ]
  }
}
```
