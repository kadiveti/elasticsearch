# Dynamic Mapping

##### Mappings will be created based on the type if you are providing any explict mappings.

````
POST sample-1/_doc
{
  "firstname":"sai",
  "secondname":"kumar"
}

````

##### output
````
{
  "_index" : "sample-1",
  "_type" : "_doc",
  "_id" : "EltUFYgBKnDXQvSTsrjd",
  "_version" : 1,
  "result" : "created",
  "_shards" : {
    "total" : 2,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 0,
  "_primary_term" : 1
}

````
##### check index
````
GET sample-1
````
##### output
````
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
        "creation_date" : "1683985051816",
        "number_of_shards" : "1",
        "number_of_replicas" : "1",
        "uuid" : "elgREYOoQYOfzbVSgw_2Pg",
        "version" : {
          "created" : "7100299"
        },
        "provided_name" : "sample-1"
      }
    }
  }
}

````
##### Index Dynamics Mapping with index patern

````
PUT _template/sample
{
  "index_patterns": [
    "sample-*"
  ],
  "mappings": {
    "dynamic_templates": [
      {
        "strings_to_keyword": {
          "match_mapping_type": "string",
          "unmatch": "*_text",
          "mapping": {
            "type": "keyword"
          }
        }
      },
      {
        "long_to_integer":{
          "match_mapping_type": "long",
          "mapping":{
            "type":"integer"
          }
        }
      },
      {
        "string_to_text":{
          "match_mapping_type": "string",
          "match": "*_text",
          "mapping":{
            "type":"text"
          }
        }
      }
    ]
  }
}
````
##### Output
````
{
  "acknowledged" : true
}

````
##### Adding data in sample index
````
POST sample-2/_doc
{
  "firstname":"sai",
  "secondname":"kumar",
  "age":10,
  "bio_text":"Texting for dynamics template"
}
````
````
{
  "acknowledged" : true
}

````
###### Sample mappings
````
GET sample-2
````
````
{
  "sample-2" : {
    "aliases" : { },
    "mappings" : {
      "dynamic_templates" : [
        {
          "strings_to_keyword" : {
            "unmatch" : "*_text",
            "match_mapping_type" : "string",
            "mapping" : {
              "type" : "keyword"
            }
          }
        },
        {
          "long_to_integer" : {
            "match_mapping_type" : "long",
            "mapping" : {
              "type" : "integer"
            }
          }
        },
        {
          "string_to_text" : {
            "match" : "*_text",
            "match_mapping_type" : "string",
            "mapping" : {
              "type" : "text"
            }
          }
        }
      ],
      "properties" : {
        "age" : {
          "type" : "integer"
        },
        "bio_text" : {
          "type" : "text"
        },
        "firstname" : {
          "type" : "keyword"
        },
        "secondname" : {
          "type" : "keyword"
        }
      }
    },
    "settings" : {
      "index" : {
        "creation_date" : "1683986543931",
        "number_of_shards" : "1",
        "number_of_replicas" : "1",
        "uuid" : "oA90ML0nRc-8nFO1OWRMVg",
        "version" : {
          "created" : "7100299"
        },
        "provided_name" : "sample-2"
      }
    }
  }
}
````


