---
layout: default
title: Setting Up Your Controllable Server
parent: Getting Started
nav_order: 3
---

# Setting Up Your Controllable Server

### Setup Dependencies

- MongoDB is a dependency in order to run Controllable server. There are a wide variety of options available in order to setup or host MongoDB.

- Please refer to [MongoDB installation guide](https://www.mongodb.com/docs/manual/installation/) in order to setup MongoDB. Ensure that the MongoDB host is reachable from your host machine where you will setup Controllable Server.

### Setup Controllable Server

Controllable Server is available as a [Docker Image](https://hub.docker.com/r/superstackhq/controllable) for use. Follow the below steps to quickly spin up a Controllable Server Container.

- Ensure Docker is set and running on your host machine. Please refer to [Docker installation instructions](https://docs.docker.com/get-docker/) in case you need to setup Docker.

- Run the following command from your terminal in order to spin up a Controllable Server container. Remember to replace the environment variables with the correct values.

```sh
docker run -i -t \
  -e "MONGO_ENDPOINT=mongodb://<your_mongo_host>:27017" \
  -e "MONGO_DATABASE=<your_mongo_database>" \
  -e "LICENSE_KEY=<paste_your_license_key>" \
  -e "INSTANCE_ID=<your_instance_id>" \
  -e "CREATE_PROPERTY_VALUE_EXECUTION_TIMEOUT_IN_MS=5000" \
  -e "READ_PROPERTY_VALUE_EXECUTION_TIMEOUT_IN_MS=1000" \
  -e "UPDATE_PROPERTY_VALUE_EXECUTION_TIMEOUT_IN_MS=5000" \
  -e "DELETE_PROPERTY_VALUE_EXECUTION_TIMEOUT_IN_MS=5000" \
  -p 8080:8080 \
  --name controllable-server superstackhq/controllable
```

- Your Controllable Server should be available on http://<Host/ContainerIP>:8080. Optionally you can setup a Load Balancer and a Domain Name in order to access the Controllable Server endpoint.

- Once all of this is setup, ensure that the endpoint setup during instance creation on [SuperStack](https://superstack.one/home.html) matches this endpoint. You can check this on the Instance details page on SuperStack.

![SuperStack Instance Endpoint](/assets/images/superstack-instance-endpoint.png)

- From your browser open the Controllable Server Endpoint, if your setup was done correctly you should see the following page.

![Controllable Server Landing Page](/assets/images/controllable-server-landing.png)
