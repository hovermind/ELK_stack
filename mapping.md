
## Why Mapping
Mapping can be compared to database table scheme.   

Although Elasticsearch is schemeless, mapping defines how a document is indexed and how its fields are indexed and stored:
* it describes the fields/properties of document ((json object)), the datatype of each field (e.g., string, integer, or date), and how those fields should be indexed and stored by Lucene
* defines which string fields should be treated as full text fields
* defines which fields contain numbers, dates, or geolocations
* defines whether the values of all fields in the document should be indexed into the catch-all _all field
* defines the format of date values
* defines custom rules to control the mapping for dynamically added fields

**Note**   
It is very important to define the mapping after we create an index — an inappropriate preliminary definition and mapping may result in the wrong search results   

**See:**   
* [RDBMS vs Elasticsearch](#)
* [Mapping Fields Data Types](https://www.elastic.co/guide/en/elasticsearch/reference/current/mapping-types.html#mapping-types)

**Creating index and assigning mapping (Kibana Devtools):**
```
PUT my_index 
{
  "mappings": {
    "my_type": { 
      "properties": { 
        "field": { "type": "xxx"  },
	    "field": { "type": "xxx"  },
	    ... .... ...
      }
    }
  }
}
```
**Example**
```
PUT user_profile 
{
  "mappings": {
    "user": { 
      "properties": { 
        "title": { "type": "string"  }, 
        "name": { "type": "string"  }, 
        "age": { "type": "integer" },
        "dob": {
          "type":   "date", 
          "format": "strict_date_optional_time||epoch_millis"
        }
      }
    }
  }
}
```

