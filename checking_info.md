### Check Mapping
```
GET index/_mapping/type
```

### Check Data
```
// URI query

host:port/_search?pretty&filter_path=hits.hits._source

host:port/_search?pretty&filter_path=hits.hits._source.my_property

host:port/_search?q=propery:value&pretty

host:port/_count?pretty
```
