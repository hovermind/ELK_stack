## Mapping for Nested JSON Object
```
{ 
  "country": "Japan",
  "company": { 
    "id": 1234,
	"name": "Hovermind",
    "profile": { 
      "established": 2018-01-01,
	  "ceo": "Hassan"
    }
  }
}
```
Mapping
```
PUT international_company
{
  "mappings": {
    "_doc": { 
      "properties": {
        "country": { "type": "keyword" },
        "company": { 
          "properties": {
            "id":  { "type": "integer" },
            "name":  { "type": "text" },
            "profile": { 
              "properties": {
                "established": {"type":   "date"},
                "ceo":  { "type": "text" }
              }
            }
          }
        }
      }
    }
  }
}
```
**Note**    
For better understanding you can use `"type":"object"` for nested JSON objects:
```
{
  "mappings": {
    "_doc": { 
      "properties": {
        ... ...
        "company": {
	  "type" : "object",
          "properties": {
            ... ...
          }
        }
      }
    }
  }
}
```
