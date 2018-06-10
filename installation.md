* Install JDK and set `JAVA_HOME` environment variable (C:\Program Files\Java\jdk1.8.0_172)
* Create a folder in `C:` drive named `ELK`    

## Download elasticsearch & install as service
* [elasticsearch zip](https://www.elastic.co/guide/en/elasticsearch/reference/current/zip-windows.html)   
* unzip in ELK folder
* right click on bin >> Open PowerShell Window Here
* `.\elasticsearch-service.bat install`
* `.\elasticsearch-service.bat manager` >> name your elasticsearch service
* Config
`C:\ELK\Elasticsearch\config\elasticsearch.yml`
```
cluster.name: esdemo
node.name: node-1
```
* Check running: `http://localhost:9200` (`GET` request from postman)
* [Important Elasticsearch configuration](https://www.elastic.co/guide/en/elasticsearch/reference/current/important-settings.html)

[x-pack]()   
[kibana]()   
[logstash]()   


