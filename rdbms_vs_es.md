## Comparison of Terms

| RDBMS         | ElasticSearch |
|---------------|---------------|
| table         | index         |
| table scheme  | mapping       |
| row           | doc (document)|
| column        | fields/properties|

See: [Mapping concepts across SQL and Elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/_mapping_concepts_across_sql_and_elasticsearch.html)

## Database Table ~ ElasticSearch Index
| id            | name          | age           |
|---------------|---------------|---------------|
| 1             | tareq hassan  | 28            |
| 2             | hover mind    | 30            |
 
```
PUT user
{
  "mappings": {
    "_doc": { 
      "properties": { 
        "id": { "type": "integer"  }, 
        "name": { "type": "string"  }, 
        "age": { "type": "integer" }
      }
    }
  }
}

PUT user/_doc/1
{
    "id": 1, 
    "name": "tareq hassan", 
    "age": 28
}


GET user/_doc/1
{
    "id": 1, 
    "name": "tareq hassan", 
    "age": 28
}
```
