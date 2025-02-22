# Active MQ - Virtulization

[![Maven Central](https://img.shields.io/maven-central/v/io.virtualan/virtualization.svg?label=Maven%20Central)](https://search.maven.org/search?q=g:%22io.virtualan%22%20AND%20a:%22virtualization%22)


## What it is
>  Allows to Virtualize/Mocking message for Active AQ. Virtualization is a Service virtualization Product and is the simulation of the behavior of Open API that are unavailable or otherwise restricted during the preproduction stage of the software development lifecycle. 
Virtualization has RESTAPI and user-friendly interface (UI) to set up the test data for your specific type of Rest APIs. This UI would help Developer, Functional Tester or Automation Tester to set up the test data for their specific use cases and test scenarios 

## Project setup/Live demo

 |Project|  
 |----------:|
  |[AMQ Service Virtualization Project](https://github.com/virtualansoftware/virtualan/tree/master/samples/virtualan-amq)  |

## Maven dependency
```mvn 
<dependency>
	<groupId>io.virtualan</groupId>
	<artifactId>virtualaization</artifactId>
	<version>${virtualan.version}</version>
</dependency>
``` 

## How to Integrate
1. create JSON Message with following format and create file in the classpath conf/jms-config.json   
> "receiver-queue" :  Add all queue name will consume the produce mock message

```JSON
{
  "AMQ" : [
      {
        "systemName": "<Application/Service Name>",
        "broker-url" : "<Broker URL>",
        "user": "<UserName>",
        "password" :"<Password>",
        "receiver-queue": ["queue Name1", "queue Name2"]   
      }
  ]
}
```
**Example Config:**
```JSON
{
  "AMQ" : [
      {
        "systemName": "Virtualan-AMQ-1",
        "broker-url" : "tcp://virtualan:61616",
        "user": "admin",
        "password" :"admin",
        "receiver-queue": ["virtualan.input"]
      }
  ]
}
```

# Mocking and Testing {#mocking}

Tools that take specification documents as input, then publish fake messages to broker destinations for simulation purposes. May also check that publisher messages are compliant with schemas.

| Link           | Description    | Language/Kind |
| :------------- | :------------- | :------------- |
| [Microcks](https://microcks.io) | Mocking and testing platform for API and microservices. Turn your AsyncAPI, OpenAPI contract examples, or Postman collections into ready-to-use mocks. Use examples to simulate and validate received messages according to schema elements. | Kubernetes-native, Self-hosted / SaaS, Open Source |
| [Virtualan](https://virtualan.io) | Mocking and testing platform for API and microservices. Turn your OpenAPI contract. AsyncAPI examples into ready-to-use mocks. Use examples to simulate and validate received messages according to schema elements. [GitHub Reference](https://github.com/virtualansoftware/AsyncAPI-Virtualization)  | Kubernetes-native, Self-hosted / SaaS, Open Source |
| [Cucumbalan-message](https://virtualan.io) | Cucumblan-message library contains predefined Gherkin step defination for Kafka message event testing. Cucumblan-message provides options to Test engineer, Manual Testers and Subject Matter Exports write feature files without having development excelency. [GitHub Reference](https://tutorials.virtualan.io/#/Cucumblan-message) | BDD, Open Source |


## How to add Mock data
### Adding Message Mock data via REST API
- API endpoint: http://localhost:8800/virtualservices/message
- Http Action: Post

```JSON
{
  "brokerUrl": "vm://embedded",
  "requestTopicOrQueueName": "virtualan.input_1",
  "resource": "virtualan.input_1",
  "requestType" : "AMQ",
  "responseTopicOrQueueName": "virtualan.output",
  "input": "{\n  \"category\": {\n    \"id\": 0,\n    \"name\": \"string\"\n  },\n  \"id\": 101,\n  \"name\": \"doggie\",\n  \"photoUrls\": [\n    \"string\"\n  ],\n  \"status\": \"available\",\n  \"tags\": [\n    {\n      \"id\": 0,\n      \"name\": \"string\"\n    }\n  ]\n}"  ,
  "output": "{\n  \"category\": {\n    \"id\": 10,\n    \"name\": \"Elan\"\n  },\n  \"id\": 101,\n  \"name\": \"doggie\",\n  \"photoUrls\": [\n    \"string\"\n  ],\n  \"status\": \"available\",\n  \"tags\": [\n    {\n      \"id\": 0,\n      \"name\": \"string\"\n    }\n  ]\n}"
}

```

### Adding Message Mock data via UI

![Add Mock](_images/sv/amq/add_mock.png)

## How to view Mock data
### View Message Mock data via REST API
> Access via following rest endpoint ad JSON format: http://localhost:8800/virtualservices


### View Message Mock data via UI

![View Mock](_images/sv/amq/view_mock.png)

----