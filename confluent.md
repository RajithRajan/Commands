# Auth
Authentication with the confluent and save info on a file
```
confluent login --save
```
# Environment
List the environment available
```
confluent environment list
```
Use an environment
```
confluent environment use <env-name>
```
# Kafka Cluster
List the kafka cluster available in current environment
```
confluent kafka cluster list
```
Use a kafka cluster 
```
confluent kafka cluster <cluster_id>
```
Describe the cluster to get information regarding the cluster
```
confluent kafka cluster describe
```
# Security
Create an Api key to interract with the kafka cluster
```
confluent api-key create --resource <cluster_id>
```
Store the API key generated else where (UI or terraform), it will prompt to enter api key adn secret
```
confluent api-key store --resource <cluster_id>
```
Use the api-key for the kafka cluster
```
confluent api-key use <api_key> --resource <cluster_id>
```
# Topics
Get information regarding the topic
```
confluent kafka topic describe <topic_name>
```
Create a topic
```
confluent kafka topic create --partitions <#> <topic_name>
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
