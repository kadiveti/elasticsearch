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

##### Create index name with lowercase only.See example error

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



PUT sample-1

{
  "acknowledged" : true,
  "shards_acknowledged" : true,
  "index" : "sample-1"
}


GET sample-1


{
  "sample-1" : {
    "aliases" : { },
    "mappings" : { },
    "settings" : {
      "index" : {
        "creation_date" : "1682038694434",
        "number_of_shards" : "1",
        "number_of_replicas" : "1",
        "uuid" : "YvM7r2mFTamKaURQV47aAA",
        "version" : {
          "created" : "7100299"
        },
        "provided_name" : "sample-1"
      }
    }
  }
}



# You can specify any id after doc if not specified it will generate random ID

POST sample-1/_doc/
{
  "firstname":"Sai",
  "secondname":"K"
}


{
  "_index" : "sample-1",
  "_type" : "_doc",
  "_id" : "-WFVoYcBOj-cH8rtrEuz",
  "_version" : 1,
  "result" : "created",
  "_shards" : {
    "total" : 2,
    "successful" : 2,
    "failed" : 0
  },
  "_seq_no" : 0,
  "_primary_term" : 1
}

GET sample-1



{
  "sample-1" : {
    "aliases" : { },
    "mappings" : {
      "properties" : {
        "firstname" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "secondname" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        }
      }
    },
    "settings" : {
      "index" : {
        "creation_date" : "1682038694434",
        "number_of_shards" : "1",
        "number_of_replicas" : "1",
        "uuid" : "YvM7r2mFTamKaURQV47aAA",
        "version" : {
          "created" : "7100299"
        },
        "provided_name" : "sample-1"
      }
    }
  }
}

If we don't specify any mappings it will creating Global Dynamic Mapping.

In this example it creating all text fields which is analyazed and keyword which is not analyzed

firstname.keyword will gives the keyword version of firstname

GET sample-1/_search


{
  "took" : 819,
  "timed_out" : false,
  "_shards" : {
    "total" : 1,
    "successful" : 1,
    "skipped" : 0,
    "failed" : 0
  },
  "hits" : {
    "total" : {
      "value" : 1,
      "relation" : "eq"
    },
    "max_score" : 1.0,
    "hits" : [
      {
        "_index" : "sample-1",
        "_type" : "_doc",
        "_id" : "-WFVoYcBOj-cH8rtrEuz",
        "_score" : 1.0,
        "_source" : {
          "firstname" : "Sai",
          "secondname" : "K"
        }
      }
    ]
  }
}


GET sample-1/_doc/-WFVoYcBOj-cH8rtrEuz



{
  "_index" : "sample-1",
  "_type" : "_doc",
  "_id" : "-WFVoYcBOj-cH8rtrEuz",
  "_version" : 1,
  "_seq_no" : 0,
  "_primary_term" : 1,
  "found" : true,
  "_source" : {
    "firstname" : "Sai",
    "secondname" : "K"
  }
}

If you want to remove meta data and only want to see source.

GET sample-1/_source/-WFVoYcBOj-cH8rtrEuz

{
  "firstname" : "Sai",
  "secondname" : "K"
}

Update the document.

WE can do two types of update one is doc update and other one is script update.

Doc update

POST sample-1/_update/-WFVoYcBOj-cH8rtrEuz
{
  "doc":{
    "secondname":"kadiveti",
    "middlename":"Kumar"
  }
}


{
  "_index" : "sample-1",
  "_type" : "_doc",
  "_id" : "-WFVoYcBOj-cH8rtrEuz",
  "_version" : 2,
  "result" : "updated",
  "_shards" : {
    "total" : 2,
    "successful" : 2,
    "failed" : 0
  },
  "_seq_no" : 1,
  "_primary_term" : 1
}


We are here at version in document

Result is updated

GET sample-1/_source/-WFVoYcBOj-cH8rtrEuz

{
  "firstname" : "Sai",
  "secondname" : "kadiveti",
  "middlename" : "Kumar"
}

GET sample-1

Dynamic Mappings are added to middlename

{
  "sample-1" : {
    "aliases" : { },
    "mappings" : {
      "properties" : {
        "firstname" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "middlename" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "secondname" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        }
      }
    },
    "settings" : {
      "index" : {
        "creation_date" : "1682038694434",
        "number_of_shards" : "1",
        "number_of_replicas" : "1",
        "uuid" : "YvM7r2mFTamKaURQV47aAA",
        "version" : {
          "created" : "7100299"
        },
        "provided_name" : "sample-1"
      }
    }
  }
}
