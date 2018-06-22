# Handlebars tutorial

- [Handlebars](https://handlebarsjs.com/)

## Example payloads

- In this tutorial I will be using different payloads in order to cover the most common use cases 

## Accessing data

- Handlebars uses ```{{data}}``` to access attributes
  - The same is required to access json like structures, but then to access correct information you have to "navigate" to the correct attribute, e.g. ```{{payload.hits.total}}```

#### Example
- Scenario: Watcher is almost done, it counts the number affected by a query, it's important to include enough information so that the user can determine whether if it's critical or not.
- Example message body: ```Watcher: JVM heap space on ES cluster alert triggered, value is: {{payload.hits.total}}. Check your dashboard now!```


## For loops

- Useful if there is a need to loop over buckets


###
