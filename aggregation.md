## Kibana Dev tools
```
GET index/_search?
{
  "size": 0,
  "aggs": {
	"aggs_name": {
	  "aggs_type": { "field": "field-name"}
	}
  }
}

// example
GET index/_search?
{
  "size": 0,
  "aggs": {
	"average-amount": {
	  "avg": { "field": "amount"}
	}
  }
}
```
#### aggs_type
* Metric - 
* Bucket - 


## URI
```
index/_search?source_content_type=application/json&source={"size":0,"aggs":{"average-amount":{"avg":{"field":"amount"}}}}
```
**Note**
* `source_content_type=application/json` is mandatory for URI query
* For retrofit (using Retrofit to consume elastic search rest API) use `@Query` for `source` i.e `@Query("source") String jsonString`:
```
public interface IRestElasticService {

	@GET("my_index/_search?source_content_type=application/json")
	Call<ElasticAggregationResponse> getAggregation(@Query("source") String jsonString);
}
```
