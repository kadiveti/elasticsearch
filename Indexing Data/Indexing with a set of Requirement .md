# Indexing Data with required Mappings and settings

___
#### To Create indices with geo_point(co-ordinates) for log indices

````
PUT logs
{
  "mappings": {
    "properties": {
      "geo":{
        "properties": {
          "coordinates":{
            "type":"geo_point"
        }
        }
      }
    }
  },
  "settings": {
    "number_of_shards": 1,
    "number_of_replicas": 1
  }
}
````
###### Output
````
{
  "acknowledged" : true,
  "shards_acknowledged" : true,
  "index" : "logs"
}
````
