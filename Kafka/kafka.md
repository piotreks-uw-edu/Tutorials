### List the topics using the kafka-topics script with suitable arguments
kafka-topics --bootstrap-server $BOOTSTRAP_SERVERS --list

### Create a new topic with the kafka-topics
kafka-topics --bootstrap-server $BOOTSTRAP_SERVERS --create --topic piotreks-uw-edu-topic

### Describe a topic
kafka-topics --bootstrap-server $BOOTSTRAP_SERVERS --describe --topic piotreks-uw-edu-topic

### Start a console producer using kafka-console-producer and tell it to produce into the topic
kafka-console-producer --bootstrap-server $BOOTSTRAP_SERVERS --topic piotreks-uw-edu-topic

### Start a console consumer using kafka-console-consumer and tell it to read from the topic your publisher is publishing into
kafka-console-consumer --bootstrap-server $BOOTSTRAP_SERVERS --topic piotreks-uw-edu-topic --from-beginning