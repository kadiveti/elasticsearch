[root@0b77f80cbacb ~]# mkdir elasticsearch
[root@0b77f80cbacb ~]# cd elasticsearch/
[root@0b77f80cbacb elasticsearch]# mkdir sample_data
[root@0b77f80cbacb elasticsearch]# cd sample_data/
[root@0b77f80cbacb sample_data]# curl -O "https://raw.githubusercontent.com/kadiveti/elasticsearch/main/sample%20data/accounts.json"
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  237k  100  237k    0     0   209k      0  0:00:01  0:00:01 --:--:--  209k
[root@0b77f80cbacb sample_data]# curl -O "https://raw.githubusercontent.com/kadiveti/elasticsearch/main/sample%20data/logs.json"
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 7800k  100 7800k    0     0  2246k      0  0:00:03  0:00:03 --:--:-- 2245k
[root@0b77f80cbacb sample_data]# curl -O "https://raw.githubusercontent.com/kadiveti/elasticsearch/main/sample%20data/shakespeare.json"
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 6359k  100 6359k    0     0  5449k      0  0:00:01  0:00:01 --:--:-- 5449k
[root@0b77f80cbacb sample_data]# ls -l
total 14404
-rw-r--r-- 1 root root  242848 Apr 22 00:29 accounts.json
-rw-r--r-- 1 root root 7988132 Apr 22 00:30 logs.json
-rw-r--r-- 1 root root 6512024 Apr 22 00:31 shakespeare.json
[root@0b77f80cbacb sample_data]# head accounts.json 
{"index":{"_id":"1"}}
{"account_number":1,"balance":39225,"firstname":"Amber","lastname":"Duke","age":32,"gender":"M","address":"880 Holmes Lane","employer":"Pyrami","email":"amberduke@pyrami.com","city":"Brogan","state":"IL"}
{"index":{"_id":"6"}}
{"account_number":6,"balance":5686,"firstname":"Hattie","lastname":"Bond","age":36,"gender":"M","address":"671 Bristol Street","employer":"Netagy","email":"hattiebond@netagy.com","city":"Dante","state":"TN"}
{"index":{"_id":"13"}}
{"account_number":13,"balance":32838,"firstname":"Nanette","lastname":"Bates","age":28,"gender":"F","address":"789 Madison Street","employer":"Quility","email":"nanettebates@quility.com","city":"Nogal","state":"VA"}
{"index":{"_id":"18"}}
{"account_number":18,"balance":4180,"firstname":"Dale","lastname":"Adams","age":33,"gender":"M","address":"467 Hutchinson Court","employer":"Boink","email":"daleadams@boink.com","city":"Orick","state":"MD"}
{"index":{"_id":"20"}}
{"account_number":20,"balance":16418,"firstname":"Elinor","lastname":"Ratliff","age":36,"gender":"M","address":"282 Kings Place","employer":"Scentric","email":"elinorratliff@scentric.com","city":"Ribera","state":"WA"}
[root@0b77f80cbacb sample_data]# head shakespeare.json 
{"index":{"_index":"shakespeare","_id":0}}
{"type":"act","line_id":1,"play_name":"Henry IV", "speech_number":"","line_number":"","speaker":"","text_entry":"ACT I"}
{"index":{"_index":"shakespeare","_id":1}}
{"type":"scene","line_id":2,"play_name":"Henry IV","speech_number":"","line_number":"","speaker":"","text_entry":"SCENE I. London. The palace."}
{"index":{"_index":"shakespeare","_id":2}}
[root@0b77f80cbacb sample_data]# head logs.json 
{"index":{"_index":"logs"}}
{"@timestamp":"2015-05-18T09:03:25.877Z","ip":"185.124.182.126","extension":"gif","response":"404","geo":{"coordinates":{"lat":36.518375,"lon":-86.05828083},"src":"PH","dest":"MM","srcdest":"PH:MM"},"@tags":["success","info"],"utc_time":"2015-05-18T09:03:25.877Z","referer":"http://twitter.com/error/william-shepherd","agent":"Mozilla/5.0 (X11; Linux x86_64; rv:6.0a1) Gecko/20110421 Firefox/6.0a1","clientip":"185.124.182.126","bytes":804,"host":"motion-media.theacademyofperformingartsandscience.org","request":"/canhaz/gemini-7.gif","url":"https://motion-media.theacademyofperformingartsandscience.org/canhaz/gemini-7.gif","@message":"185.124.182.126 - - [2015-05-18T09:03:25.877Z] \"GET /canhaz/gemini-7.gif HTTP/1.1\" 404 804 \"-\" \"Mozilla/5.0 (X11; Linux x86_64; rv:6.0a1) Gecko/20110421 Firefox/6.0a1\"","spaces":"this   is   a   thing    with lots of     spaces       wwwwoooooo","xss":"<script>console.log(\"xss\")</script>","headings":["<h3>f-i-j-nl-ng</h5>","http://facebook.com/success/lodewijk-van-den-berg"],"links":["daniel-tani@facebook.com","http://nytimes.com/security/kathryn-sullivan","www.nytimes.com"],"relatedContent":[{"url":"http://www.laweekly.com/news/cbs-crew-rat-fink-2368032","og:type":"article","og:title":"CBS Crew Rat Fink","og:description":"Near a couple of auto body shops (and a sharp new Space Invader mosaic that we&#039;ll post soon) near Temple and Westmoreland is a CBS wall with a nice Rat ...","og:url":"http://www.laweekly.com/news/cbs-crew-rat-fink-2368032","article:published_time":"2008-01-14T08:05:26-08:00","article:modified_time":"2014-10-28T14:59:52-07:00","article:section":"News","article:tag":"Mark Mauer","og:image":"http://IMAGES1.laweekly.com/imager/cbs-crew-rat-fink/u/original/2430299/img_2049.jpg","og:image:height":"360","og:image:width":"480","og:site_name":"LA Weekly","twitter:title":"CBS Crew Rat Fink","twitter:description":"Near a couple of auto body shops (and a sharp new Space Invader mosaic that we&#039;ll post soon) near Temple and Westmoreland is a CBS wall with a nice Rat ...","twitter:card":"summary","twitter:image":"http://IMAGES1.laweekly.com/imager/cbs-crew-rat-fink/u/original/2430299/img_2049.jpg","twitter:site":"@laweekly"},{"url":"http://www.laweekly.com/news/push-and-retna-in-koreatown-2368043","og:type":"article","og:title":"Push and Retna in Koreatown","og:description":"Yeah, I originally had this posted this morning as Push &amp; Ayer - Sorry. It looked like a Retna piece, but I saw the Ayer in there and thought that must ...","og:url":"http://www.laweekly.com/news/push-and-retna-in-koreatown-2368043","article:published_time":"2008-01-29T07:28:32-08:00","article:modified_time":"2014-10-28T14:59:54-07:00","article:section":"News","article:tag":"Shelley Leopold","og:image":"http://IMAGES1.laweekly.com/imager/push-and-retna-in-koreatown/u/original/2430376/img_3671.jpg","og:image:height":"360","og:image:width":"480","og:site_name":"LA Weekly","twitter:title":"Push and Retna in Koreatown","twitter:description":"Yeah, I originally had this posted this morning as Push &amp; Ayer - Sorry. It looked like a Retna piece, but I saw the Ayer in there and thought that must ...","twitter:card":"summary","twitter:image":"http://IMAGES1.laweekly.com/imager/push-and-retna-in-koreatown/u/original/2430376/img_3671.jpg","twitter:site":"@laweekly"},{"url":"http://www.laweekly.com/news/asylm-ruets-pdb-on-santa-monica-2368012","og:type":"article","og:title":"Asylm, Ruets, PDB on Santa Monica","og:description":"Not a new piece, but a well-hidden gem a little south of Santa Monica Blvd. in an alley off of Heliotrope or Edgemont. I&#039;ve been sitting on this for a w...","og:url":"http://www.laweekly.com/news/asylm-ruets-pdb-on-santa-monica-2368012","article:published_time":"2008-04-22T15:11:15-07:00","article:modified_time":"2014-10-28T14:59:48-07:00","article:section":"News","article:tag":"Culture and Lifestyle","og:image":"http://images1.laweekly.com/imager/asylm-ruets-pdb-on-santa-monica/u/original/2430137/img_5027.jpg","og:image:height":"360","og:image:width":"480","og:site_name":"LA Weekly","twitter:title":"Asylm, Ruets, PDB on Santa Monica","twitter:description":"Not a new piece, but a well-hidden gem a little south of Santa Monica Blvd. in an alley off of Heliotrope or Edgemont. I&#039;ve been sitting on this for a w...","twitter:card":"summary","twitter:image":"http://images1.laweekly.com/imager/asylm-ruets-pdb-on-santa-monica/u/original/2430137/img_5027.jpg","twitter:site":"@laweekly"},{"url":"http://www.laweekly.com/news/laurence-tribe-tangles-with-cbs-and-la-city-hall-2396867","og:type":"article","og:title":"Laurence Tribe Tangles with CBS and L.A. City Hall","og:description":"The United States Court of Appeals for the Ninth Circuit&rsquo;s Courtroom 3 - a miniature auditorium with comfortable, smoked salmon-colored seats - wa...","og:url":"http://www.laweekly.com/news/laurence-tribe-tangles-with-cbs-and-la-city-hall-2396867","article:published_time":"2008-06-04T14:16:10-07:00","article:modified_time":"2014-11-26T14:43:59-08:00","article:section":"News","og:site_name":"LA Weekly","twitter:title":"Laurence Tribe Tangles with CBS and L.A. City Hall","twitter:description":"The United States Court of Appeals for the Ninth Circuit&rsquo;s Courtroom 3 - a miniature auditorium with comfortable, smoked salmon-colored seats - wa...","twitter:card":"summary","twitter:site":"@laweekly"}],"machine":{"os":"win xp","ram":3221225472},"@version":"1"}
{"index":{"_index":"logs"}}
{"@timestamp":"2015-05-18T12:28:25.013Z","ip":"79.1.14.87","extension":"gif","response":"200","geo":{"coordinates":{"lat":35.16531472,"lon":-107.9006142},"src":"GN","dest":"US","srcdest":"GN:US"},"@tags":["success","info"],"utc_time":"2015-05-18T12:28:25.013Z","referer":"http://www.slate.com/warning/b-alvin-drew","agent":"Mozilla/5.0 (X11; Linux i686) AppleWebKit/534.24 (KHTML, like Gecko) Chrome/11.0.696.50 Safari/534.24","clientip":"79.1.14.87","bytes":774,"host":"motion-media.theacademyofperformingartsandscience.org","request":"/canhaz/james-mcdivitt.gif","url":"https://motion-media.theacademyofperformingartsandscience.org/canhaz/james-mcdivitt.gif","@message":"79.1.14.87 - - [2015-05-18T12:28:25.013Z] \"GET /canhaz/james-mcdivitt.gif HTTP/1.1\" 200 774 \"-\" \"Mozilla/5.0 (X11; Linux i686) AppleWebKit/534.24 (KHTML, like Gecko) Chrome/11.0.696.50 Safari/534.24\"","spaces":"this   is   a   thing    with lots of     spaces       wwwwoooooo","xss":"<script>console.log(\"xss\")</script>","headings":["<h3>charles-bolden</h5>","http://www.slate.com/success/barry-wilmore"],"links":["george-nelson@twitter.com","http://facebook.com/info/anatoly-solovyev","www.www.slate.com"],"relatedContent":[],"machine":{"os":"osx","ram":8589934592},"@version":"1"}
{"index":{"_index":"logs"}}
{"@timestamp":"2015-05-18T17:44:34.357Z","ip":"178.209.1.7","extension":"php","response":"200","geo":{"coordinates":{"lat":36.38025,"lon":-88.98547778},"src":"US","dest":"ET","srcdest":"US:ET"},"@tags":["success","security"],"utc_time":"2015-05-18T17:44:34.357Z","referer":"http://facebook.com/success/voskhod-1","agent":"Mozilla/5.0 (X11; Linux i686) AppleWebKit/534.24 (KHTML, like Gecko) Chrome/11.0.696.50 Safari/534.24","clientip":"178.209.1.7","bytes":7417,"host":"theacademyofperformingartsandscience.org","request":"/people/type:astronauts/name:john-phillips/profile","memory":296680,"phpmemory":296680,"url":"https://theacademyofperformingartsandscience.org/people/type:astronauts/name:john-phillips/profile","@message":"178.209.1.7 - - [2015-05-18T17:44:34.357Z] \"GET /people/type:astronauts/name:john-phillips/profile HTTP/1.1\" 200 7417 \"-\" \"Mozilla/5.0 (X11; Linux i686) AppleWebKit/534.24 (KHTML, like Gecko) Chrome/11.0.696.50 Safari/534.24\"","spaces":"this   is   a   thing    with lots of     spaces       wwwwoooooo","xss":"<script>console.log(\"xss\")</script>","headings":["<h3>scott-parazynski</h5>","http://twitter.com/success/carl-walz"],"links":["lee-morin@www.slate.com","http://facebook.com/info/oleg-makarov","www.twitter.com"],"relatedContent":[{"url":"http://www.laweekly.com/news/entropy-at-the-french-cottage-hollywood-2368119","og:type":"article","og:title":"Entropy at the French Cottage, Hollywood","og:description":"The French Cottage hotel stood a few feet away from Sunset and Highland, near a stretch of old hotels and motels which are vanishing as steadily and unn...","og:url":"http://www.laweekly.com/news/entropy-at-the-french-cottage-hollywood-2368119","article:published_time":"2007-08-09T08:48:14-07:00","article:modified_time":"2014-10-28T15:00:07-07:00","article:section":"News","og:image":"http://images1.laweekly.com/imager/entropy-at-the-french-cottage-hollywood/u/original/2430875/img_1444.jpg","og:image:height":"480","og:image:width":"640","og:site_name":"LA Weekly","twitter:title":"Entropy at the French Cottage, Hollywood","twitter:description":"The French Cottage hotel stood a few feet away from Sunset and Highland, near a stretch of old hotels and motels which are vanishing as steadily and unn...","twitter:card":"summary","twitter:image":"http://images1.laweekly.com/imager/entropy-at-the-french-cottage-hollywood/u/original/2430875/img_1444.jpg","twitter:site":"@laweekly"}],"machine":{"os":"win 8","ram":15032385536},"@version":"1"}



[root@0b77f80cbacb sample_data]# curl -H 'Content-Type: application/x-ndjson' -XPOST "http://localhost:9200/bank/_bulk?pretty" --data-binary @accounts.json > accounts_bulk.json
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  581k  100  344k  100  237k   156k   107k  0:00:02  0:00:02 --:--:--  263k



GET bank/_search


{
  "took" : 806,
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
      },
      {
        "_index" : "bank",
        "_type" : "_doc",
        "_id" : "6",
        "_score" : 1.0,
        "_source" : {
          "account_number" : 6,
          "balance" : 5686,
          "firstname" : "Hattie",
          "lastname" : "Bond",
          "age" : 36,
          "gender" : "M",
          "address" : "671 Bristol Street",
          "employer" : "Netagy",
          "email" : "hattiebond@netagy.com",
          "city" : "Dante",
          "state" : "TN"
        }
      },
      {
        "_index" : "bank",
        "_type" : "_doc",
        "_id" : "13",
        "_score" : 1.0,
        "_source" : {
          "account_number" : 13,
          "balance" : 32838,
          "firstname" : "Nanette",
          "lastname" : "Bates",
          "age" : 28,
          "gender" : "F",
          "address" : "789 Madison Street",
          "employer" : "Quility",
          "email" : "nanettebates@quility.com",
          "city" : "Nogal",
          "state" : "VA"
        }
      },
      {
        "_index" : "bank",
        "_type" : "_doc",
        "_id" : "18",
        "_score" : 1.0,
        "_source" : {
          "account_number" : 18,
          "balance" : 4180,
          "firstname" : "Dale",
          "lastname" : "Adams",
          "age" : 33,
          "gender" : "M",
          "address" : "467 Hutchinson Court",
          "employer" : "Boink",
          "email" : "daleadams@boink.com",
          "city" : "Orick",
          "state" : "MD"
        }
      },
      {
        "_index" : "bank",
        "_type" : "_doc",
        "_id" : "20",
        "_score" : 1.0,
        "_source" : {
          "account_number" : 20,
          "balance" : 16418,
          "firstname" : "Elinor",
          "lastname" : "Ratliff",
          "age" : 36,
          "gender" : "M",
          "address" : "282 Kings Place",
          "employer" : "Scentric",
          "email" : "elinorratliff@scentric.com",
          "city" : "Ribera",
          "state" : "WA"
        }
      },
      {
        "_index" : "bank",
        "_type" : "_doc",
        "_id" : "25",
        "_score" : 1.0,
        "_source" : {
          "account_number" : 25,
          "balance" : 40540,
          "firstname" : "Virginia",
          "lastname" : "Ayala",
          "age" : 39,
          "gender" : "F",
          "address" : "171 Putnam Avenue",
          "employer" : "Filodyne",
          "email" : "virginiaayala@filodyne.com",
          "city" : "Nicholson",
          "state" : "PA"
        }
      },
      {
        "_index" : "bank",
        "_type" : "_doc",
        "_id" : "32",
        "_score" : 1.0,
        "_source" : {
          "account_number" : 32,
          "balance" : 48086,
          "firstname" : "Dillard",
          "lastname" : "Mcpherson",
          "age" : 34,
          "gender" : "F",
          "address" : "702 Quentin Street",
          "employer" : "Quailcom",
          "email" : "dillardmcpherson@quailcom.com",
          "city" : "Veguita",
          "state" : "IN"
        }
      },
      {
        "_index" : "bank",
        "_type" : "_doc",
        "_id" : "37",
        "_score" : 1.0,
        "_source" : {
          "account_number" : 37,
          "balance" : 18612,
          "firstname" : "Mcgee",
          "lastname" : "Mooney",
          "age" : 39,
          "gender" : "M",
          "address" : "826 Fillmore Place",
          "employer" : "Reversus",
          "email" : "mcgeemooney@reversus.com",
          "city" : "Tooleville",
          "state" : "OK"
        }
      },
      {
        "_index" : "bank",
        "_type" : "_doc",
        "_id" : "44",
        "_score" : 1.0,
        "_source" : {
          "account_number" : 44,
          "balance" : 34487,
          "firstname" : "Aurelia",
          "lastname" : "Harding",
          "age" : 37,
          "gender" : "M",
          "address" : "502 Baycliff Terrace",
          "employer" : "Orbalix",
          "email" : "aureliaharding@orbalix.com",
          "city" : "Yardville",
          "state" : "DE"
        }
      },
      {
        "_index" : "bank",
        "_type" : "_doc",
        "_id" : "49",
        "_score" : 1.0,
        "_source" : {
          "account_number" : 49,
          "balance" : 29104,
          "firstname" : "Fulton",
          "lastname" : "Holt",
          "age" : 23,
          "gender" : "F",
          "address" : "451 Humboldt Street",
          "employer" : "Anocha",
          "email" : "fultonholt@anocha.com",
          "city" : "Sunriver",
          "state" : "RI"
        }
      }
    ]
  }
}




[root@0b77f80cbacb sample_data]# curl -H 'Content-Type: application/x-ndjson' -XPOST "http://localhost:9200/shakespeare/_bulk?pretty" --data-binary @shakespeare.json > shakespeare_bulk.json
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 16.1M  100  9.9M  100 6359k  1570k   979k  0:00:06  0:00:06 --:--:-- 2549k

Add a new line in json for shakespeare to remove the error

GET shakespeare/_search

{
  "took" : 991,
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

Defaults max no of documents hits 100000. DO cat/indices to count of documents


