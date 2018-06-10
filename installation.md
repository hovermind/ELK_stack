* Install JDK and set `JAVA_HOME` environment variable (C:\Program Files\Java\jdk1.8.0_172)
* Create a folder in `C:` drive named `ELK`    

## Download elasticsearch & install as service
* [elasticsearch zip](https://www.elastic.co/guide/en/elasticsearch/reference/current/zip-windows.html)   
* unzip in ELK folder
* right click on bin folder of elasticsearch >> Open PowerShell Window Here
* `.\elasticsearch-service.bat install`
* `.\elasticsearch-service.bat manager` >> name your elasticsearch service
* Config
`C:\ELK\Elasticsearch\config\elasticsearch.yml`
```
cluster.name: esdemo
node.name: node-1
```
* Check running: windows services >> start elasticsearch >> `http://localhost:9200` (`GET` request from postman)
* [Important Elasticsearch configuration](https://www.elastic.co/guide/en/elasticsearch/reference/current/important-settings.html)

## X-Pack for elasticsearch
* [x-pack zip](https://www.elastic.co/guide/en/elasticsearch/reference/6.2/installing-xpack-es.html)
* put zip in ELK folder (no need to unzip)
* right click on bin folder of elasticsearch >> Open PowerShell Window Here
* `.\elasticsearch-plugin install file:///C:/ELK/x-pack-6.2.4.zip`
* setup passwords: `x-pack/setup-passwords interactive -v` (i.e. 'espassword' for elastic)
* restart elasticsearch from services
* check with postman basic authentication: `http://localhost:9200`

[kibana](https://www.elastic.co/guide/en/kibana/current/windows.html)   
[logstash]()   


