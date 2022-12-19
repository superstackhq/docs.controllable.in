---
layout: default
title: Java
parent: Client SDKs
nav_order: 2
---

# Java Client SDK

### Add Dependency via Maven / Gradle

https://jitpack.io/#superstackhq/controllable-java-sdk/v1-alpha


### Read Property Value Example

```java
package in.controllable;

import in.controllable.client.ControllableClient;
import in.controllable.model.ExecutionResponse;
import in.controllable.model.PropertyReference;
import in.controllable.model.ReadPropertyRequest;
import in.controllable.model.ReadPropertyRequests;

import java.io.IOException;
import java.util.List;
import java.util.Map;

public class Main {

    private static final String serverEndpoint = "<endpoint>";

    private static final String appKey = "<app_key>";

    private static final String environment = "<env>";

    private static final Integer callTimeoutInMS = 1000;

    public static void main(String[] args) throws IOException {
        ControllableClient client = new ControllableClient(serverEndpoint, appKey, environment, callTimeoutInMS);

        ReadPropertyRequest readPropertyRequest = new ReadPropertyRequest(new PropertyReference(
                List.of("services", "userservice"),
                "min_password_len",
                "v1"
        ), Map.of("country", "IN"));

        ReadPropertyRequests requests = new ReadPropertyRequests();
        requests.add(readPropertyRequest);

        ExecutionResponse response = client.readPropertyValue(requests);

        System.out.println(response.getResponses().get(0).getValue().getData());
    }
}
```
