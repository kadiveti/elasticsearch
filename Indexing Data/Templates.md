We can roll over index on daily basis or Weekly basis.

It helps to remove the index which are not much useful.

Like you can roll over index on daily basis and remove the index which are not in use.


PUT logs-2020-04-01
PUT logs-2020-04-02
PUT logs-2020-04-03
PUT logs-2020-04-04
PUT logs-2020-04-05
PUT logs-2020-04-06
PUT logs-2020-04-07

We can also roll over the index on size basis as well.

PUT logs-01
PUT logs-02
PUT logs-03
PUT logs-04
PUT logs-05
PUT logs-06
PUT logs-07


PUT _template/logs
{
  "aliases": {
    "log_sample": {}
  },
  "mappings": {
    "properties": {
      "field1":{
        "type": "keyword"
      }
    }
  },
  "settings": {
    "number_of_shards": 1,
    "number_of_replicas": 1
  },
  "index_patterns": ["logs-*"]
}


{
  "acknowledged" : true
}

Note: Aliases should not match existing index name

PUT logs-2020-04-01

{
  "acknowledged" : true,
  "shards_acknowledged" : true,
  "index" : "logs-2020-04-01"
}

GET log_sample

{
  "logs-2020-04-01" : {
    "aliases" : {
      "log_sample" : { }
    },
    "mappings" : {
      "properties" : {
        "field1" : {
          "type" : "keyword"
        }
      }
    },
    "settings" : {
      "index" : {
        "creation_date" : "1682163688463",
        "number_of_shards" : "1",
        "number_of_replicas" : "1",
        "uuid" : "m3pGnKEsRVa5EXS5RahB4w",
        "version" : {
          "created" : "7100299"
        },
        "provided_name" : "logs-2020-04-01"
      }
    }
  },
  "logs-2020-04-02" : {
    "aliases" : {
      "log_sample" : { }
    },
    "mappings" : {
      "properties" : {
        "field1" : {
          "type" : "keyword"
        }
      }
    },
    "settings" : {
      "index" : {
        "creation_date" : "1682163744115",
        "number_of_shards" : "1",
        "number_of_replicas" : "1",
        "uuid" : "S1HTC4Z2RUSkq3-A0LSE5g",
        "version" : {
          "created" : "7100299"
        },
        "provided_name" : "logs-2020-04-02"
      }
    }
  }
}


