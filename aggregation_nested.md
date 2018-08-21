## Nested Aggs
Result of an aggregation can be source for nested aggregation
```
GET index/_search
{
  "size": 0,
  "aggs": {
    "aggs-name": {
      "terms": { "field": "field-name" },
      "aggs": {
        "aggs-name-nested": {
          "avg": { "field": "amount" }
        }
      }
    }
  }
}
```

## Bucket Aggs by Index
```
GET index/_search
{
  "size": 0,
  "aggs": {
    "index": {
      "terms": { "field": "_index" },
      "aggs": {
        "aggs-name-nested-1": {
        "terms": { "field": "field-name" },
         "aggs":{
            "aggs-name-nested-2": {
              "avg": { "field": "amount" }
            }
         }
        }
      }
    }
  }
}
```
**Notes**
* for aggregation by index name must be 'index'
* field name must be `_index` i.e. `"terms": { "field": "_index" }`
