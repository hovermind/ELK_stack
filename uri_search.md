## REST API Format
```
host:port/[index_name/wild_card*]/[type]/[_action/id]
```
`_action`
* `_search`
* `_count`

## Searching
Prefix: `http://host:port`

#### `?q=my_property:value`
```
/index/_search?q=my_property:value

/user/_search?q=last_name:hassan
```

#### Pretty Print: `&pretty`
```
/index/_search?q=my_property:value&pretty
```

#### Filter Path: `&filter_path`
```
/index/_search?filter_path=hits.hits._source

// inclusion
/index/_search?filter_path=hits.hits._source.property
/index/_search?filter_path=hits.hits._source.user

// multiple property ','
/index/_search?filter_path=hits.hits._source.user,hits.hits._source.tweets

// exclusion '-'
/index/_search?filter_path=-hits.hits._source.user
```
**Note**     
Consider response as JS object and access properties accordingly i.e. `_search?filter_path=hits.hits._source.user.name`

## Wild Card
Wild card is allowed both in index and field value
```
/index/index_name*/_count?q=property:*
```

## Range
* [] => inclusion `_search?q=year:[2017 TO 2018]`
* {} => exclusion `_search?q=year:{2017 TO 2018}`

## Regex
`_search?q=\/[regex-flags]\/`
