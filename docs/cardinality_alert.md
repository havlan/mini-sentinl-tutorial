## Cardinality alerting



```json
GET /logstash-*/_search
{
    "size" : 0,
    "aggs" : {
        "ip_addr" : {
            "cardinality" : {
              "field" : "ip"
            }
        }
    }
}
```
