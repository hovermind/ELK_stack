* Install JDK and set `JAVA_HOME` environment variable (C:\Program Files\Java\jdk1.8.0_172)
* Download zips and install as service:   
[elasticsearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/zip-windows.html)   
[x-pack]()   
[kibana]()   
[logstash]()   

## Config
`C:\Program Files\Elasticsearch\config\elasticsearch.yml`
```
cluster.name: esdemo
node.name: node-1
```

## Check running
#### elasticsearch
GET request from postman: http://localhost:9200
