# Idaithalam - Lowcode Test Automation

[![Maven Central](https://img.shields.io/maven-central/v/io.virtualan/idaithalam.svg?label=Maven%20Central)](https://search.maven.org/search?q=g:%22io.virtualan%22%20AND%20a:%22idaithalam%22) 
                          
## What is it:

Low code Test automation framework using cucumber and supports Behavior Driven Development (BDD). Can build test cases using Excel and Postman collection. It allows to build and test api workflow in minutes. 

**Idaithalam is a BDD style Cucumber based low code automation product.**

As a user: You need to export the POSTMAN Collection or create Excel and pass to Idaithalam. 

Currently It supports generate Feature files for **POSTMAN Collection** and  **Excel** format. 
This will covert REST APIs based on POST, GET, PUT, DELETE and PATCH action as respective domain specific language which helps you to describe API/business behavior without the need to go into detail of implementation. 

## Project Setup 
 - [POSTMAN Collection Project](https://github.com/virtualansoftware/idaithalam-postman-collection-lowcode-automation) 
 - [Microservices-lowcode-testautomation Project](https://github.com/virtualansoftware/microservices-lowcode-testautomation) 

 ## Maven dependency:
  
  ```mvn 
    <dependency>
      <groupId>io.virtualan</groupId>
       <artifactId>idaithalam</artifactId>
       <version>${idaithalam.version}</version>
    </dependency>
  ```  

## How to Integrate: 


1. Code to Invoke Automation testcase Execution for POSTMAN Collection:
> Example Project: [idaithalam-postman-apitesting](https://github.com/virtualansoftware/idaithalam-postman-collection-lowcode-automation)

```yml
parallelExecution: 4
timeout:  30000
apiExecutor:
  - reportTitle: "API Testing POSTMAN Collection 1 with 2 files"
    env: dev
    outputDir: target/postman/1
    cucumblanProperties:
      service.api: https://live.virtualandemo.com
      service.api.xml: https://www.w3schools.com
      virtualan.data.load: idaithalan.postman_collection.json;virtualan-xml.json;
      virtualan.data.heading: PETAPI-Testing;SOAP-Temperature-Testing;
      virtualan.data.type: POSTMAN
```

2. Code to Invoke Automation testcase Execution for Excel:
> Example Project: [idaithalam-excel-apitesting](https://github.com/virtualansoftware/microservices-lowcode-testautomation)

```yml
parallelExecution: 4
timeout:  30000
apiExecutor:
  - reportTitle: "Lakeside Mutual - Customer Self-Service - API alone"
    env: test
    outputDir: target/LakesideMutual/Customer-Self-Service/1
    inputExcel: css/customer-self-service.xlsx
    cucumblanProperties:
      service.api.css: http://microservices.virtualandemo.com:8080
      service.api.quote: http://microservices.virtualandemo.com:8090
```

3. Sample code to invoke the api:

```java
public void workflowExecution_1() {
    try {
        boolean isSuccess = VirtualanTestPlanExecutor
                .invoke("lakeside-Mutual-Customer-Self-Service.yml");
        Assert.assertTrue(isSuccess);
    } catch (InterruptedException e) {
        Assert.assertTrue(false);
    }
}
```

## Used for API testing.
* Most of the common use case, You can execute as Regression test suite for the test case executed manually via POSTMAN.
* Run the testcase via POSTMAN and store the response as Example with response data in the POSTMAN for all the test cases that you had executed. 
* Export all the API request and Response as POSTMAN collection.
* POSTMAN Collection can be passed as Input as Idaithalam.
* Idaithalam can be integrated along Continuous Integration and Continuous Delivery(CI/CD) with Pipeline.
* Idaithalam take the POSTMAN Collection as Input and Covert as Cucumber Feature file. 
* Cucumblan-API another product will execute the feature file and Produce the Cucumber Report with BDD style.

## Used for Contract testing.
* Support for Contract testing. 

## Used for Production Checkout.
* Utilized to run against selected use case that needs to validated against Production Checkout(Validation during the production release).   

## Used for Agile sprint-end Regression testing.
* During the sprint, You can run all the test cases Manually and then save the response via POSTMAN. Using Idaithalam, Export the POSTMAN Collection and Pass Collection to Idaithalam and will execute and produce the Excellent cucumber HTML Report with all the charts.

----