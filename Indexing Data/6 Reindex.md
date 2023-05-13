
````

POST _reindex
{
  "source": {
    "index": "bank"
  },
  "dest": {
    "index": "bank_new"
  }
}
````
````
{
  "took" : 2797,
  "timed_out" : false,
  "total" : 1000,
  "updated" : 0,
  "created" : 1000,
  "deleted" : 0,
  "batches" : 1,
  "version_conflicts" : 0,
  "noops" : 0,
  "retries" : {
    "bulk" : 0,
    "search" : 0
  },
  "throttled_millis" : 0,
  "requests_per_second" : -1.0,
  "throttled_until_millis" : 0,
  "failures" : [ ]
}

````
````
reindex.remote.whitelist:"privayeip:9200,privayeip:9200"
reindex.ssl.verifictaion_mode: certificate
reindex.ssl.truststore.type: PKCS12
reindex.ssl.keystore.type: PKCS12
reindex.ssl.keystore.path: certs/name of the certificate
reindex.ssl.keystore.path: certs/name of the certificate
````
````
./bin/elasticsearch-keystore add reindex.truststore.secure_password

./bin/elasticsearch-keystore add reindex.keystore.secure_password
````
````
Restart Elasticsearch
````
````
POST _reindex
{
  "source": {
    "remote": {
      "host": "https://provateip:9200",
      "username": "",
      "password": ""
    },
    "index": "bank"
    "query": {
       "term": {
          "gender.keyword": {
             "value": "M"
             }
       }
    }
  },
  "dest": {
#  "pipeline" : "Pipelinemame"  #### we can use the reindex with pipeline
    "index": "bank_reindex"
  },
  "script": {
  "lang": "painless",
  "source": "ctx._source.remove('gender')"
  }
}
````
````
POST bank/_update_by_query
````
````
GET bank/_doc/1
````

````
  "_index" : "bank",
  "_type" : "_doc",
  "_id" : "1",
  "_version" : 3,
  "_seq_no" : 2000,
  "_primary_term" : 4,
  "found" : true,
  "_source" : {
    "account_number" : 1,
    "balance" : 39225,
    "firstname" : "Amber",
    "lastname" : "Duke",
    "age" : 32,
    "gender" : "M",
    "address" : "880 Holmes Lane",
    "employer" : "Pyrami",
    "email" : "amberduke@pyrami.com",
    "city" : "Brogan",
    "state" : "IL"

````

````
POST bank/_update_by_query?pipeline=mypipelie
{ 
  "query": {
     "term": {
        "gender.keyword" = "F"
     }
  },
  "script": {
    "lang": "painless",
    "source": """
    ctx._source.balance += ctx._source.balance*0.03;
    if (ctx._source.transaction == null) {
      ctx._source.transaction = 1;
    } else {
      ctx._source.transaction++;
    }
    """
  }
}

````

````
GET bank/_search
````

````
{
  "took" : 585,
  "timed_out" : false,
  "_shards" : {
    "total" : 1,
    "successful" : 1,
    "skipped" : 0,
    "failed" : 0
  },
  "hits" : {
    "total" : {
      "value" : 1000,
      "relation" : "eq"
    },
    "max_score" : 1.0,
    "hits" : [
      {
        "_index" : "bank",
        "_type" : "_doc",
        "_id" : "1",
        "_score" : 1.0,
        "_source" : {
          "account_number" : 1,
          "firstname" : "Amber",
          "address" : "880 Holmes Lane",
          "balance" : 41613,
          "gender" : "M",
          "city" : "Brogan",
          "employer" : "Pyrami",
          "state" : "IL",
          "age" : 32,
          "email" : "amberduke@pyrami.com",
          "transaction" : 2,
          "lastname" : "Duke"
        }
      },
      {
        "_index" : "bank",
        "_type" : "_doc",
        "_id" : "6",
        "_score" : 1.0,
        "_source" : {
          "account_number" : 6,
          "firstname" : "Hattie",
          "address" : "671 Bristol Street",
          "balance" : 6031,
          "gender" : "M",
          "city" : "Dante",
          "employer" : "Netagy",
          "state" : "TN",
          "age" : 36,
          "email" : "hattiebond@netagy.com",
          "transaction" : 2,
          "lastname" : "Bond"
        }
      },
      {
        "_index" : "bank",
        "_type" : "_doc",
        "_id" : "13",
        "_score" : 1.0,
        "_source" : {
          "account_number" : 13,
          "firstname" : "Nanette",
          "address" : "789 Madison Street",
          "balance" : 34837,
          "gender" : "F",
          "city" : "Nogal",
          "employer" : "Quility",
          "state" : "VA",
          "age" : 28,
          "email" : "nanettebates@quility.com",
          "transaction" : 2,
          "lastname" : "Bates"
        }
      },
      {
        "_index" : "bank",
        "_type" : "_doc",
        "_id" : "18",
        "_score" : 1.0,
        "_source" : {
          "account_number" : 18,
          "firstname" : "Dale",
          "address" : "467 Hutchinson Court",
          "balance" : 4434,
          "gender" : "M",
          "city" : "Orick",
          "employer" : "Boink",
          "state" : "MD",
          "age" : 33,
          "email" : "daleadams@boink.com",
          "transaction" : 2,
          "lastname" : "Adams"
        }
      },
      {
        "_index" : "bank",
        "_type" : "_doc",
        "_id" : "20",
        "_score" : 1.0,
        "_source" : {
          "account_number" : 20,
          "firstname" : "Elinor",
          "address" : "282 Kings Place",
          "balance" : 17417,
          "gender" : "M",
          "city" : "Ribera",
          "employer" : "Scentric",
          "state" : "WA",
          "age" : 36,
          "email" : "elinorratliff@scentric.com",
          "transaction" : 2,
          "lastname" : "Ratliff"
        }
      },
      {
        "_index" : "bank",
        "_type" : "_doc",
        "_id" : "25",
        "_score" : 1.0,
        "_source" : {
          "account_number" : 25,
          "firstname" : "Virginia",
          "address" : "171 Putnam Avenue",
          "balance" : 43008,
          "gender" : "F",
          "city" : "Nicholson",
          "employer" : "Filodyne",
          "state" : "PA",
          "age" : 39,
          "email" : "virginiaayala@filodyne.com",
          "transaction" : 2,
          "lastname" : "Ayala"
        }
      },
      {
        "_index" : "bank",
        "_type" : "_doc",
        "_id" : "32",
        "_score" : 1.0,
        "_source" : {
          "account_number" : 32,
          "firstname" : "Dillard",
          "address" : "702 Quentin Street",
          "balance" : 51013,
          "gender" : "F",
          "city" : "Veguita",
          "employer" : "Quailcom",
          "state" : "IN",
          "age" : 34,
          "email" : "dillardmcpherson@quailcom.com",
          "transaction" : 2,
          "lastname" : "Mcpherson"
        }
      },
      {
        "_index" : "bank",
        "_type" : "_doc",
        "_id" : "37",
        "_score" : 1.0,
        "_source" : {
          "account_number" : 37,
          "firstname" : "Mcgee",
          "address" : "826 Fillmore Place",
          "balance" : 19745,
          "gender" : "M",
          "city" : "Tooleville",
          "employer" : "Reversus",
          "state" : "OK",
          "age" : 39,
          "email" : "mcgeemooney@reversus.com",
          "transaction" : 2,
          "lastname" : "Mooney"
        }
      },
      {
        "_index" : "bank",
        "_type" : "_doc",
        "_id" : "44",
        "_score" : 1.0,
        "_source" : {
          "account_number" : 44,
          "firstname" : "Aurelia",
          "address" : "502 Baycliff Terrace",
          "balance" : 36586,
          "gender" : "M",
          "city" : "Yardville",
          "employer" : "Orbalix",
          "state" : "DE",
          "age" : 37,
          "email" : "aureliaharding@orbalix.com",
          "transaction" : 2,
          "lastname" : "Harding"
        }
      },
      {
        "_index" : "bank",
        "_type" : "_doc",
        "_id" : "49",
        "_score" : 1.0,
        "_source" : {
          "account_number" : 49,
          "firstname" : "Fulton",
          "address" : "451 Humboldt Street",
          "balance" : 30876,
          "gender" : "F",
          "city" : "Sunriver",
          "employer" : "Anocha",
          "state" : "RI",
          "age" : 23,
          "email" : "fultonholt@anocha.com",
          "transaction" : 2,
          "lastname" : "Holt"
        }
      }
    ]
  }
}

````
````
PUT _ingest/pipeline/test-piplein
{
  "description": "Some description",
  "processors": [
    {
      "remove": {
        "field": "account_number"
      }
    },
    {
       "set": {
        "field": "_source.fullname"
        , "value": "{{_source.firstname}} {{_source.lastname}}"
      }
    },
      {
        "script": {
          "lang": "painless",
          "source": """
          if (ctx.gender == "M") {
            ctx.gender = "male"
          } else {
            ctx.gender = "female"
          }
          """
        }
        
      }
  ]
}
````
````
elasticsearch.yml

node.ingest = true

restart elasticsearch
````
````

POST _reindex
{
    "source" : {
        "index": "bank
    },
    "dest" : {
       "index": "bank_pipeline",
       "pipeline": "test_pipeline
    }
}
````


