---
author: "matthew-keelan"
comments: true
date: 2016-05-09T12:00:00-05:00
draft: false
image: ""
menu: ""
share: true
categories:
  - technology
date: 2016-12-31T14:29:51-06:00
description: ""
tags: 
  - logstash
  - elasticsearch
summary: If you want to store data coming from logstash in an elasticsearch index with the date as a suffix, like logstash-2016.12.31, that's easily acheivable.  But what if you don't want to send the @timestamp field to elasticsearch?
title: Logstash drop @timestamp but still use it in elasticsearch index name
share: true
slug: logstash-drop-timestamp-but-still-use-it-in-elasticserach-index-name
---

If you want to store data coming from logstash in an elasticsearch index with the date as a suffix, like logstash-2016.12.31, that's easily acheivable with this output:

```javascript
output {
    elasticsearch {
        hosts => [
            'elastic01.example.com:9200',  
            'elastic02.example.com:9200',  
            'elastic03.example.com:9200'  
        ]
        index => "logstash-%{+YYY.MM.dd}"  
    }
}
```

Logstash will get the date from @timestamp, and format it as indicated in the index setting.

This is a test
a test

But what if you don't want the @timestamp field indexed in Elasticsearch? For instance, what if you want to rename that field? Then you'll have to do some trickery.

```json
filter {
    mutate {
        add_field => {
            "[@metadata][indexDate]" => "%{+YYYY.MM.dd}"
        }
        rename => {
            "@timestamp" => "receivedTimestamp"
        }
    }
}
output {
    elasticsearch {
        hosts => [
            'elastic01.example.com:9200',
            'elastic02.example.com:9200',
            'elastic03.example.com:9200'
        ]
        index => "logstash-%{[@metadata][indexDate]}"
    }
}
```

We'll use the [@metadata](https://www.elastic.co/guide/en/logstash/current/event-dependent-configuration.html#metadata) field. Fields in @metadata are not passed on to the output, so this is a perfect use for it.