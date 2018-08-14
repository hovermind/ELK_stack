## Mapping for Array of JSON Objects
If you need to index arrays of objects and to maintain the independence of each object in the array, you should use the nested datatype instead of the object datatype.
Internally, nested objects index each object in the array as a separate hidden document, meaning that each nested object can be queried independently of the others, with the nested query:
```
{
  "users":[
    {
      "id" : 1234,
      "name" : "Hassan"
    },
    { },
    { },
    ... ...
  ]
}
```
Mapping
```
PUT users
{
  "mappings": {
    "_doc": { 
      "properties": {
          "users": {
             "type" : "nested",
             "properties" : {
                "id" : {"type" : "integer"}
                "name" : {"type" : "text"}
             }
          }
      }
    }
  }
}
```
