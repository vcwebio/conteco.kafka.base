# `kafka.base` - ContEco

Confluent Kafka Base image, with configuration changes.
See `conteco.docs.overview` for more information on the ContEco ecosystem.

## Configuration Changes

```bash
# enabled log cleaner and added delete policy
log.cleaner.enable=true
log.cleanup.policy=delete

# reduced retention to 1 hour
log.retention.hours=1

# set zookeeper connect to ContEco Default
zookeeper.connect=zookeeper:2181
```

## Tags

* 5.4.0  
* 5.3.1  
* 5.2.3  
