## Multi-Field
It is often useful to index the same field in different ways for different purposes. This is the purpose of multi-fields. 
For instance, a string field could be mapped as a text field for full-text search, and as a keyword field for sorting or aggregations:
```
PUT my_index
{
  "mappings": {
    "_doc": {
      "properties": {
        "city": {
          "type": "text",
          "fields": {
            "raw": { 
              "type":  "keyword"
            }
          }
        }
      }
    }
  }
}

PUT my_index/_doc/1
{
  "city": "New York"
}

PUT my_index/_doc/2
{
  "city": "York"
}

GET my_index/_search
{
  "query": {
    "match": {
      "city": "york" 
    }
  },
  "sort": {
    "city.raw": "asc" 
  },
  "aggs": {
    "Cities": {
      "terms": {
        "field": "city.raw" 
      }
    }
  }
}
```
See: [Multi-Field Details](https://www.elastic.co/guide/en/elasticsearch/reference/current/multi-fields.html)
