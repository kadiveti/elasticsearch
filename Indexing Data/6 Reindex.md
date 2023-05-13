
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
    "index": "bank_reindex"
  },
  "script": {
  "lang": "painless",
  "source": "ctx._source.remove('gender')"
  }
}
````








