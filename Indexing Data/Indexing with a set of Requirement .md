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
#### Check Shakespeare index
````
GET shakespeare
````
###### Output
````
{
  "shakespeare" : {
    "aliases" : { },
    "mappings" : {
      "properties" : {
        "line_id" : {
          "type" : "integer"
        },
        "play_name" : {
          "type" : "keyword"
        },
        "speaker" : {
          "type" : "keyword"
        },
        "speech_number" : {
          "type" : "integer"
        }
      }
    },
    "settings" : {
      "index" : {
        "creation_date" : "1682009004385",
        "number_of_shards" : "1",
        "number_of_replicas" : "1",
        "uuid" : "Sl91jFdgR5SNguBJINnRIg",
        "version" : {
          "created" : "7100299"
        },
        "provided_name" : "shakespeare"
      }
    }
  }
}
````
#### Create Bank index with settings
````
PUT bank
{
  "settings": {
    "number_of_replicas": 1,
    "number_of_shards": 1
  }
}

````
###### Output
````
{
  "acknowledged" : true,
  "shards_acknowledged" : true,
  "index" : "bank"
}
````
#### Check Bank index
````
GET bank
````

###### Output

````
{
  "bank" : {
    "aliases" : { },
    "mappings" : { },
    "settings" : {
      "index" : {
        "creation_date" : "1682009599115",
        "number_of_shards" : "1",
        "number_of_replicas" : "1",
        "uuid" : "AHpo0TpiR2mi7kgPdR5OHg",
        "version" : {
          "created" : "7100299"
        },
        "provided_name" : "bank"
      }
    }
  }
}
````
#### Check All indexes
````
GET _cat/indices?v
````

````
health status index       uuid                   pri rep docs.count docs.deleted store.size pri.store.size
green  open   bank        AHpo0TpiR2mi7kgPdR5OHg   1   1          0            0       416b           208b
green  open   shakespeare Sl91jFdgR5SNguBJINnRIg   1   1          0            0       416b           208b
green  open   .kibana_1   mym8BrtmSBu6-rh9AISQ9A   1   1         13           41    115.1kb         51.9kb
green  open   logs        r5HFUBA2QW-LXnWkXjDsXA   1   1          0            0       416b           208b
````







