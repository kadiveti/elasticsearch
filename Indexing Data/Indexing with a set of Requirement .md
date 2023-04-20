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
#### To check Status of indices

````
GET _cat/indices?v
````
###### Output

---------------------------------------------------------------------------------------------------------------------------------------
|health|  status |   index      |  uuid                   |  pri | rep |  docs.count | docs.deleted  |  store.size  |   pri.store.size|
|------|---------|--------------|-------------------------|------|-----|-------------|---------------|--------------|-----------------|
|green |   open  |  .kibana_1   |  mym8BrtmSBu6-rh9AISQ9A |  1   |  1  |   6         |    5          |    115.2kb   |      54.1kb     |
|green |   open  |  logs        |  r5HFUBA2QW-LXnWkXjDsXA |  1   |  1  |   0         |    0          |    115.2kb   |      54.1kb     |
---------------------------------------------------------------------------------------------------------------------------------------

#### To Get the indices data

````
GET logs
````
###### Output

````
{
  "logs" : {
    "aliases" : { },
    "mappings" : {
      "properties" : {
        "geo" : {
          "properties" : {
            "coordinates" : {
              "type" : "geo_point"
            }
          }
        }
      }
    },
    "settings" : {
      "index" : {
        "creation_date" : "1682007340252",
        "number_of_shards" : "1",
        "number_of_replicas" : "1",
        "uuid" : "r5HFUBA2QW-LXnWkXjDsXA",
        "version" : {
          "created" : "7100299"
        },
        "provided_name" : "logs"
      }
    }
  }
}
````

#### Create Mappings for Shakespeare index
````
PUT shakespeare
{
  "mappings": {
    "properties": {
      "speaker":{
        "type": "keyword"
      },
      "play_name":{
        "type":"keyword"
      },
      "line_id":{
        "type":"integer"
      },
      "speech_number":{
        "type":"integer"
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
  "index" : "shakespeare"
}

````













