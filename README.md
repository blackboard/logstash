# logstash configurations

## Blackboard Learn
Deployment
```
collector(log shipper: logstash)* -> 
platform(message queue: redis -> 
         log indexer: logstash(filters) -> 
         full text search engine: Elasticsearch)
```

Log shipper configuration file
```
shipper.conf
```

Log indexer configurationi file
```
indexer.conf
```

This deployment approach provides the following benefits:
* Enables modification of the parsing and processing logic without updating the logstash agents on the each server that you're collecting logs from. The number of index instances on the platform tier can be as little as one depending on the throughput volume to the message queue.
* Enables modification of the parsing and processing logic without interrupting the throughput from the shipper agent to the platform. The message queue can stay up and accumulate logs while the indexers are getting updated.
* Improves scalability via distributed processing and throughput control.
