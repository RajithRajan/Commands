Authentication with the confluent and save info on a file
```
confluent login --save
```
List the environment available
```
confluent environment list
```
Use an environment
```
confluent environment use <env-name>
```
List the kafka cluster available in current environment
```
confluent kafka cluster list
```
Use a kafka cluster 
```
confluent kafka cluster <cluster_id>
```
Create an Api key to interract with the kafka cluster
```
confluent api-key create --resource <cluster_id>
```
Use the api-key for the kafka cluster
```
confluent api-key use <api_key> --resource <cluster_id>
```
List the topic available in the current kafka cluster
```
confluent kafka topic list
```
*Consumer* : List the messages/values in the kafka topic from the beginning
```
confluent kafka topic consume --from-beginning <topic_name>
```
*Producer* : Create new messages (key & value) for the kafka topic
```
confluent kafka topic produce <topic_name> --parse-key
<key>:<value>
```
