## Comparison of Terms

| RDBMS         | ElasticSearch |
|---------------|---------------|
| table         | index         |
| table scheme  | mapping       |
| row           | doc (document)|
| column        | fields/properties|

#### Database Table - user
| id            | name          | age           |
|---------------|---------------|---------------|
| 1             | tareq hassan  | 28            |
| 2             | hover mind    | 30            |

#### ElasticSearch Index - user 
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
```
