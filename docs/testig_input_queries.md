## Testing input queries

- There are several ways to test the watchers input query, the simplest is to go in Kibana dev tools and test it.
- Copy the query from the visualization SPY request tab and go to dev tools.
- The dev tools require HTTP verbs such as GET, POST, PUT, DELETE. To test the input query, use ```GET _msearch```   [Doc](https://www.elastic.co/guide/en/kibana/current/console-kibana.html)
- If the query is copied from the visualization SPY you will need to specify index name.
  - The query is not ready just yet, you will need a json object with an index field.
  - e.g.


<!--- TODO Why can't the JSON be unindented? Why does _msearch query break? -->
```json
GET _msearch
{"index": ["logstash-2018.06.21"]}
```
  - Luckily you can simply copy the query from the visualization SPY directly under the json object above.

```json
GET _msearch
{"index": ["logstash-2018.06.21"]}
{"size":0,"_source":{"excludes":[]},"aggs":{"2":{"date_histogram":{"field":"@timestamp","interval":"1m","time_zone":"Europe/Berlin","min_doc_count":1}}},"stored_fields":["*"],"script_fields":{},"docvalue_fields":["@timestamp"],"query":{"bool":{"must":[{"match_all":{}},{"range":{"@timestamp":{"gte":"now-24h/h","lte":"now/h","format":"epoch_millis"}}}],"filter":[],"should":[],"must_not":[]}}}
```
