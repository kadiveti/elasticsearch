# Curd Operations


___
#### To check Status of indices

````
GET _cat/indices?v
````
###### Output

|health|  status |   index      |  uuid                   |  pri | rep |  docs.count | docs.deleted  |  store.size  |   pri.store.size|
|------|---------|--------------|-------------------------|------|-----|-------------|---------------|--------------|-----------------|
|green |   open  |  .kibana_1   |  mym8BrtmSBu6-rh9AISQ9A |  1   |  1  |   6         |    5          |    115.2kb   |      54.1kb     |


#### To create an Index 

````
PUT Sample-1
````

###### Output

````
{
  "error" : {
    "root_cause" : [
      {
        "type" : "invalid_index_name_exception",
        "reason" : "Invalid index name [Sample-1], must be lowercase",
        "index_uuid" : "_na_",
        "index" : "Sample-1"
      }
    ],
    "type" : "invalid_index_name_exception",
    "reason" : "Invalid index name [Sample-1], must be lowercase",
    "index_uuid" : "_na_",
    "index" : "Sample-1"
  },
  "status" : 400
}

````

[##### Note:] Create index name with lowercase

````
PUT sample-1
````
###### Output

````
{
  "acknowledged" : true,
  "shards_acknowledged" : true,
  "index" : "sample-1"
}

````
#### To check Created Index

````
GET Sample-1
````

###### Output

````
{
  "sample-1" : {
    "aliases" : { },
    "mappings" : { },
    "settings" : {
      "index" : {
        "creation_date" : "1682002381795",
        "number_of_shards" : "1",
        "number_of_replicas" : "1",
        "uuid" : "OCRupfQ7SjK1DRO62EjcRg",
        "version" : {
          "created" : "7100299"
        },
        "provided_name" : "sample-1"
      }
    }
  }
}
````

#### To Delete Index

````
DELETE sample-1
````

###### Output

````

{
  "acknowledged" : true
}

````

#### To check Delete Index

````
GET Sample-1
````

###### Output

````
{
  "error" : {
    "root_cause" : [
      {
        "type" : "index_not_found_exception",
        "reason" : "no such index [sample-1]",
        "resource.type" : "index_or_alias",
        "resource.id" : "sample-1",
        "index_uuid" : "_na_",
        "index" : "sample-1"
      }
    ],
    "type" : "index_not_found_exception",
    "reason" : "no such index [sample-1]",
    "resource.type" : "index_or_alias",
    "resource.id" : "sample-1",
    "index_uuid" : "_na_",
    "index" : "sample-1"
  },
  "status" : 404
}

````
