## Index Creation from Kibana Devtools
#### Create Index
Go to kibana backend, select devtools
```
PUT /index_name
```
#### Assign Mapping Shceme
```
PUT index_name/_mapping/type_name
{
	"properties": {
		"property_name" : {"type" : "property_type"},
		... ...,
		... ...
	}
}
```
**Note:**
* Only one type allowed per index. See: [removal of type from index](https://www.elastic.co/guide/en/elasticsearch/reference/6.x/removal-of-types.html)
* One index should contain only one type of data, create multiple indices for multiple type of data

## Insert Data
```
POST index_name/type_name/id
{
    // json data that conforms to mapping scheme of index
}
``
