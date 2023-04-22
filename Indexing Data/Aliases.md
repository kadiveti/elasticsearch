Aliased are another name of index.

Aliases are pointed to subset of filter index.


POST _aliases
{
  "actions": [
    {
      "add": {
        "index": "bank",
        "alias": "accounts"
      }
    }
  ]
}

{
  "acknowledged" : true
}


GET bank


{
  "bank" : {
    "aliases" : {
      "accounts" : { }
    },
    "mappings" : {
      "properties" : {
        "account_number" : {
          "type" : "long"
        },
        "address" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "age" : {
          "type" : "long"
        },
        "balance" : {
          "type" : "long"
        },
        "city" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "email" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "employer" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "firstname" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "gender" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "lastname" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "state" : {
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



GET accounts


{
  "bank" : {
    "aliases" : {
      "accounts" : { }
    },
    "mappings" : {
      "properties" : {
        "account_number" : {
          "type" : "long"
        },
        "address" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "age" : {
          "type" : "long"
        },
        "balance" : {
          "type" : "long"
        },
        "city" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "email" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "employer" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "firstname" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "gender" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "lastname" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "state" : {
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


GET bank/_doc/1

{
  "_index" : "bank",
  "_type" : "_doc",
  "_id" : "1",
  "_version" : 1,
  "_seq_no" : 0,
  "_primary_term" : 1,
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
  }
}


GET accounts/_doc/1


{
  "_index" : "bank",
  "_type" : "_doc",
  "_id" : "1",
  "_version" : 1,
  "_seq_no" : 0,
  "_primary_term" : 1,
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
  }
}


POST _aliases
{
  "actions": [
    {
      "remove": {
        "index": "bank",
        "alias": "accounts"
      }
    }
  ]
}

{
  "acknowledged" : true
}

Multiple Add and removes can be done in same alias Call.


GET bank


{
  "bank" : {
    "aliases" : { },
    "mappings" : {
      "properties" : {
        "account_number" : {
          "type" : "long"
        },
        "address" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "age" : {
          "type" : "long"
        },
        "balance" : {
          "type" : "long"
        },
        "city" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "email" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "employer" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "firstname" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "gender" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "lastname" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "state" : {
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



GET bank/_doc/1


{
  "_index" : "bank",
  "_type" : "_doc",
  "_id" : "1",
  "_version" : 1,
  "_seq_no" : 0,
  "_primary_term" : 1,
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
  }
}


GET accounts/_doc/1


{
  "error" : {
    "root_cause" : [
      {
        "type" : "index_not_found_exception",
        "reason" : "no such index [accounts]",
        "resource.type" : "index_expression",
        "resource.id" : "accounts",
        "index_uuid" : "_na_",
        "index" : "accounts"
      }
    ],
    "type" : "index_not_found_exception",
    "reason" : "no such index [accounts]",
    "resource.type" : "index_expression",
    "resource.id" : "accounts",
    "index_uuid" : "_na_",
    "index" : "accounts"
  },
  "status" : 404
}


POST _aliases
{
  "actions": [
    {
      "add": {
        "index": "bank",
        "alias": "sample_data"
      }
    },
    {
      "add": {
        "index": "shakespeare",
        "alias": "sample_data"
      }
    },
    {
      "add": {
        "index": "logs",
        "alias": "sample_data"
      }
    }
  ]
}

{
  "acknowledged" : true
}

GET sample_data


{
  "bank" : {
    "aliases" : {
      "sample_data" : { }
    },
    "mappings" : {
      "properties" : {
        "account_number" : {
          "type" : "long"
        },
        "address" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "age" : {
          "type" : "long"
        },
        "balance" : {
          "type" : "long"
        },
        "city" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "email" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "employer" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "firstname" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "gender" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "lastname" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "state" : {
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
  },
  "logs" : {
    "aliases" : {
      "sample_data" : { }
    },
    "mappings" : {
      "properties" : {
        "@message" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "@tags" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "@timestamp" : {
          "type" : "date"
        },
        "@version" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "agent" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "bytes" : {
          "type" : "long"
        },
        "clientip" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "extension" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "geo" : {
          "properties" : {
            "coordinates" : {
              "type" : "geo_point"
            },
            "dest" : {
              "type" : "text",
              "fields" : {
                "keyword" : {
                  "type" : "keyword",
                  "ignore_above" : 256
                }
              }
            },
            "src" : {
              "type" : "text",
              "fields" : {
                "keyword" : {
                  "type" : "keyword",
                  "ignore_above" : 256
                }
              }
            },
            "srcdest" : {
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
        "headings" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "host" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "ip" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "links" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "machine" : {
          "properties" : {
            "os" : {
              "type" : "text",
              "fields" : {
                "keyword" : {
                  "type" : "keyword",
                  "ignore_above" : 256
                }
              }
            },
            "ram" : {
              "type" : "long"
            }
          }
        },
        "memory" : {
          "type" : "long"
        },
        "phpmemory" : {
          "type" : "long"
        },
        "referer" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "relatedContent" : {
          "properties" : {
            "article:modified_time" : {
              "type" : "date"
            },
            "article:published_time" : {
              "type" : "date"
            },
            "article:section" : {
              "type" : "text",
              "fields" : {
                "keyword" : {
                  "type" : "keyword",
                  "ignore_above" : 256
                }
              }
            },
            "article:tag" : {
              "type" : "text",
              "fields" : {
                "keyword" : {
                  "type" : "keyword",
                  "ignore_above" : 256
                }
              }
            },
            "og:description" : {
              "type" : "text",
              "fields" : {
                "keyword" : {
                  "type" : "keyword",
                  "ignore_above" : 256
                }
              }
            },
            "og:image" : {
              "type" : "text",
              "fields" : {
                "keyword" : {
                  "type" : "keyword",
                  "ignore_above" : 256
                }
              }
            },
            "og:image:height" : {
              "type" : "text",
              "fields" : {
                "keyword" : {
                  "type" : "keyword",
                  "ignore_above" : 256
                }
              }
            },
            "og:image:width" : {
              "type" : "text",
              "fields" : {
                "keyword" : {
                  "type" : "keyword",
                  "ignore_above" : 256
                }
              }
            },
            "og:site_name" : {
              "type" : "text",
              "fields" : {
                "keyword" : {
                  "type" : "keyword",
                  "ignore_above" : 256
                }
              }
            },
            "og:title" : {
              "type" : "text",
              "fields" : {
                "keyword" : {
                  "type" : "keyword",
                  "ignore_above" : 256
                }
              }
            },
            "og:type" : {
              "type" : "text",
              "fields" : {
                "keyword" : {
                  "type" : "keyword",
                  "ignore_above" : 256
                }
              }
            },
            "og:url" : {
              "type" : "text",
              "fields" : {
                "keyword" : {
                  "type" : "keyword",
                  "ignore_above" : 256
                }
              }
            },
            "twitter:card" : {
              "type" : "text",
              "fields" : {
                "keyword" : {
                  "type" : "keyword",
                  "ignore_above" : 256
                }
              }
            },
            "twitter:description" : {
              "type" : "text",
              "fields" : {
                "keyword" : {
                  "type" : "keyword",
                  "ignore_above" : 256
                }
              }
            },
            "twitter:image" : {
              "type" : "text",
              "fields" : {
                "keyword" : {
                  "type" : "keyword",
                  "ignore_above" : 256
                }
              }
            },
            "twitter:site" : {
              "type" : "text",
              "fields" : {
                "keyword" : {
                  "type" : "keyword",
                  "ignore_above" : 256
                }
              }
            },
            "twitter:title" : {
              "type" : "text",
              "fields" : {
                "keyword" : {
                  "type" : "keyword",
                  "ignore_above" : 256
                }
              }
            },
            "url" : {
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
        "request" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "response" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "spaces" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "url" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "utc_time" : {
          "type" : "date"
        },
        "xss" : {
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
  },
  "shakespeare" : {
    "aliases" : {
      "sample_data" : { }
    },
    "mappings" : {
      "properties" : {
        "line_id" : {
          "type" : "integer"
        },
        "line_number" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "play_name" : {
          "type" : "keyword"
        },
        "speaker" : {
          "type" : "keyword"
        },
        "speech_number" : {
          "type" : "integer"
        },
        "text_entry" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "type" : {
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


GET _cat/indices?v


health status index       uuid                   pri rep docs.count docs.deleted store.size pri.store.size
green  open   bank        AHpo0TpiR2mi7kgPdR5OHg   1   1       1000            0    758.6kb        379.3kb
green  open   shakespeare Sl91jFdgR5SNguBJINnRIg   1   1      28755            0      9.7mb          4.8mb
green  open   .kibana_1   mym8BrtmSBu6-rh9AISQ9A   1   1         57            1    133.5kb         60.1kb
green  open   logs        r5HFUBA2QW-LXnWkXjDsXA   1   1       2106            0     13.8mb          6.9mb


POST _aliases
{
  "actions": [
    {
      "add": {
        "index": "shakespeare",
        "alias": "Henry_IV",
        "filter": {
          "term": {
            "play_name": "Henry IV"
          }
        }
      }
    }
  ]
}

{
  "acknowledged" : true
}


GET shakespeare/_search

{
  "took" : 68,
  "timed_out" : false,
  "_shards" : {
    "total" : 1,
    "successful" : 1,
    "skipped" : 0,
    "failed" : 0
  },
  "hits" : {
    "total" : {
      "value" : 10000,
      "relation" : "gte"
    },
    "max_score" : 1.0,
    "hits" : [
      {
        "_index" : "shakespeare",
        "_type" : "_doc",
        "_id" : "0",
        "_score" : 1.0,
        "_source" : {
          "type" : "act",
          "line_id" : 1,
          "play_name" : "Henry IV",
          "speech_number" : "",
          "line_number" : "",
          "speaker" : "",
          "text_entry" : "ACT I"
        }
      },
      {
        "_index" : "shakespeare",
        "_type" : "_doc",
        "_id" : "1",
        "_score" : 1.0,
        "_source" : {
          "type" : "scene",
          "line_id" : 2,
          "play_name" : "Henry IV",
          "speech_number" : "",
          "line_number" : "",
          "speaker" : "",
          "text_entry" : "SCENE I. London. The palace."
        }
      },
      {
        "_index" : "shakespeare",
        "_type" : "_doc",
        "_id" : "2",
        "_score" : 1.0,
        "_source" : {
          "type" : "line",
          "line_id" : 3,
          "play_name" : "Henry IV",
          "speech_number" : "",
          "line_number" : "",
          "speaker" : "",
          "text_entry" : "Enter KING HENRY, LORD JOHN OF LANCASTER, the EARL of WESTMORELAND, SIR WALTER BLUNT, and others"
        }
      },
      {
        "_index" : "shakespeare",
        "_type" : "_doc",
        "_id" : "3",
        "_score" : 1.0,
        "_source" : {
          "type" : "line",
          "line_id" : 4,
          "play_name" : "Henry IV",
          "speech_number" : 1,
          "line_number" : "1.1.1",
          "speaker" : "KING HENRY IV",
          "text_entry" : "So shaken as we are, so wan with care,"
        }
      },
      {
        "_index" : "shakespeare",
        "_type" : "_doc",
        "_id" : "4",
        "_score" : 1.0,
        "_source" : {
          "type" : "line",
          "line_id" : 5,
          "play_name" : "Henry IV",
          "speech_number" : 1,
          "line_number" : "1.1.2",
          "speaker" : "KING HENRY IV",
          "text_entry" : "Find we a time for frighted peace to pant,"
        }
      },
      {
        "_index" : "shakespeare",
        "_type" : "_doc",
        "_id" : "5",
        "_score" : 1.0,
        "_source" : {
          "type" : "line",
          "line_id" : 6,
          "play_name" : "Henry IV",
          "speech_number" : 1,
          "line_number" : "1.1.3",
          "speaker" : "KING HENRY IV",
          "text_entry" : "And breathe short-winded accents of new broils"
        }
      },
      {
        "_index" : "shakespeare",
        "_type" : "_doc",
        "_id" : "6",
        "_score" : 1.0,
        "_source" : {
          "type" : "line",
          "line_id" : 7,
          "play_name" : "Henry IV",
          "speech_number" : 1,
          "line_number" : "1.1.4",
          "speaker" : "KING HENRY IV",
          "text_entry" : "To be commenced in strands afar remote."
        }
      },
      {
        "_index" : "shakespeare",
        "_type" : "_doc",
        "_id" : "7",
        "_score" : 1.0,
        "_source" : {
          "type" : "line",
          "line_id" : 8,
          "play_name" : "Henry IV",
          "speech_number" : 1,
          "line_number" : "1.1.5",
          "speaker" : "KING HENRY IV",
          "text_entry" : "No more the thirsty entrance of this soil"
        }
      },
      {
        "_index" : "shakespeare",
        "_type" : "_doc",
        "_id" : "8",
        "_score" : 1.0,
        "_source" : {
          "type" : "line",
          "line_id" : 9,
          "play_name" : "Henry IV",
          "speech_number" : 1,
          "line_number" : "1.1.6",
          "speaker" : "KING HENRY IV",
          "text_entry" : "Shall daub her lips with her own childrens blood;"
        }
      },
      {
        "_index" : "shakespeare",
        "_type" : "_doc",
        "_id" : "9",
        "_score" : 1.0,
        "_source" : {
          "type" : "line",
          "line_id" : 10,
          "play_name" : "Henry IV",
          "speech_number" : 1,
          "line_number" : "1.1.7",
          "speaker" : "KING HENRY IV",
          "text_entry" : "Nor more shall trenching war channel her fields,"
        }
      }
    ]
  }
}



GET Henry_IV/_search

{
  "took" : 28,
  "timed_out" : false,
  "_shards" : {
    "total" : 1,
    "successful" : 1,
    "skipped" : 0,
    "failed" : 0
  },
  "hits" : {
    "total" : {
      "value" : 3205,
      "relation" : "eq"
    },
    "max_score" : 1.0,
    "hits" : [
      {
        "_index" : "shakespeare",
        "_type" : "_doc",
        "_id" : "0",
        "_score" : 1.0,
        "_source" : {
          "type" : "act",
          "line_id" : 1,
          "play_name" : "Henry IV",
          "speech_number" : "",
          "line_number" : "",
          "speaker" : "",
          "text_entry" : "ACT I"
        }
      },
      {
        "_index" : "shakespeare",
        "_type" : "_doc",
        "_id" : "1",
        "_score" : 1.0,
        "_source" : {
          "type" : "scene",
          "line_id" : 2,
          "play_name" : "Henry IV",
          "speech_number" : "",
          "line_number" : "",
          "speaker" : "",
          "text_entry" : "SCENE I. London. The palace."
        }
      },
      {
        "_index" : "shakespeare",
        "_type" : "_doc",
        "_id" : "2",
        "_score" : 1.0,
        "_source" : {
          "type" : "line",
          "line_id" : 3,
          "play_name" : "Henry IV",
          "speech_number" : "",
          "line_number" : "",
          "speaker" : "",
          "text_entry" : "Enter KING HENRY, LORD JOHN OF LANCASTER, the EARL of WESTMORELAND, SIR WALTER BLUNT, and others"
        }
      },
      {
        "_index" : "shakespeare",
        "_type" : "_doc",
        "_id" : "3",
        "_score" : 1.0,
        "_source" : {
          "type" : "line",
          "line_id" : 4,
          "play_name" : "Henry IV",
          "speech_number" : 1,
          "line_number" : "1.1.1",
          "speaker" : "KING HENRY IV",
          "text_entry" : "So shaken as we are, so wan with care,"
        }
      },
      {
        "_index" : "shakespeare",
        "_type" : "_doc",
        "_id" : "4",
        "_score" : 1.0,
        "_source" : {
          "type" : "line",
          "line_id" : 5,
          "play_name" : "Henry IV",
          "speech_number" : 1,
          "line_number" : "1.1.2",
          "speaker" : "KING HENRY IV",
          "text_entry" : "Find we a time for frighted peace to pant,"
        }
      },
      {
        "_index" : "shakespeare",
        "_type" : "_doc",
        "_id" : "5",
        "_score" : 1.0,
        "_source" : {
          "type" : "line",
          "line_id" : 6,
          "play_name" : "Henry IV",
          "speech_number" : 1,
          "line_number" : "1.1.3",
          "speaker" : "KING HENRY IV",
          "text_entry" : "And breathe short-winded accents of new broils"
        }
      },
      {
        "_index" : "shakespeare",
        "_type" : "_doc",
        "_id" : "6",
        "_score" : 1.0,
        "_source" : {
          "type" : "line",
          "line_id" : 7,
          "play_name" : "Henry IV",
          "speech_number" : 1,
          "line_number" : "1.1.4",
          "speaker" : "KING HENRY IV",
          "text_entry" : "To be commenced in strands afar remote."
        }
      },
      {
        "_index" : "shakespeare",
        "_type" : "_doc",
        "_id" : "7",
        "_score" : 1.0,
        "_source" : {
          "type" : "line",
          "line_id" : 8,
          "play_name" : "Henry IV",
          "speech_number" : 1,
          "line_number" : "1.1.5",
          "speaker" : "KING HENRY IV",
          "text_entry" : "No more the thirsty entrance of this soil"
        }
      },
      {
        "_index" : "shakespeare",
        "_type" : "_doc",
        "_id" : "8",
        "_score" : 1.0,
        "_source" : {
          "type" : "line",
          "line_id" : 9,
          "play_name" : "Henry IV",
          "speech_number" : 1,
          "line_number" : "1.1.6",
          "speaker" : "KING HENRY IV",
          "text_entry" : "Shall daub her lips with her own childrens blood;"
        }
      },
      {
        "_index" : "shakespeare",
        "_type" : "_doc",
        "_id" : "9",
        "_score" : 1.0,
        "_source" : {
          "type" : "line",
          "line_id" : 10,
          "play_name" : "Henry IV",
          "speech_number" : 1,
          "line_number" : "1.1.7",
          "speaker" : "KING HENRY IV",
          "text_entry" : "Nor more shall trenching war channel her fields,"
        }
      }
    ]
  }
}


GET Henry_IV

{
  "shakespeare" : {
    "aliases" : {
      "Henry_IV" : {
        "filter" : {
          "term" : {
            "play_name" : "Henry IV"
          }
        }
      },
      "sample_data" : { }
    },
    "mappings" : {
      "properties" : {
        "line_id" : {
          "type" : "integer"
        },
        "line_number" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "play_name" : {
          "type" : "keyword"
        },
        "speaker" : {
          "type" : "keyword"
        },
        "speech_number" : {
          "type" : "integer"
        },
        "text_entry" : {
          "type" : "text",
          "fields" : {
            "keyword" : {
              "type" : "keyword",
              "ignore_above" : 256
            }
          }
        },
        "type" : {
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




