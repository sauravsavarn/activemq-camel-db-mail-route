# Getting Started

### Application Overview
![application-overview.png](assets%2Fimages%2Fapplication-overview.png)

* In this example we are going to build the Retail Inventory Systems, where the Items of the retail inventory system will be persisted in the DB. 
* The upstream for the system will be coming from the bunch of users or any other external system(s) and all these upstream messages will be posted into the activemq. The queue name of activemq is 'input_item_queue'.  
* The Camel Route is going to read the messages from the queue 'input_item_queue', and then perform the data validation on those data and if the validation is SUCCESSful that will be persisted as records into the Database. If there is any failure or any data validation issues then in that case we are going to send an email event to the configured email address and also we are going to have a designated error queue named 'error_queue', just to put the error messages into the queue.


### Active-MQ setup
* this is done using the docker command below :

    $> docker run --detach --name spring-camel-route-activemq -p 61616:61616 -p 8161:8161 --rm apache/activemq-artemis:latest-alpine

* alternatively, activemq can be spined from the docker-compose file placed in the director location 'docs/assets/docker-compose-files/spin-activemq'.

  >  REF: https://activemq.apache.org/components/artemis/documentation/latest/docker.html#official-images

* to access the management console for queue creation launch the below url in browser: <br/>
   url : http://localhost:8161   <br/>
   username : artemis <br/>
   password : artemis
* Below snapshot shows the queue created in activemq/artemis
  ![activemq-queue-created-in-artemis.png](assets%2Fimages%2Factivemq-queue-created-in-artemis.png)

### [Setup ActiveMQ]  Dependencies required to connect to artemis activemq from camel
![dependencies-activemq.png](assets%2Fimages%2Fdependencies-activemq.png)

### Necessary config needed for activemq
![config-needed-in-application-yaml-for-activemq.png](assets%2Fimages%2Fconfig-needed-in-application-yaml-for-activemq.png)

### Data Contracts From Upstream System
![data-contracts-from-upstream-system.png](assets%2Fimages%2Fdata-contracts-from-upstream-system.png)

Here we will define the data contracts for the messages that we are going to receive from the Upstream system.
* The upstream system is going to send items.
* The Items are going to come to activeMQ as JSON String

 

