---
layout: default
title: Golang
parent: Client SDKs
nav_order: 3
---

# Golang Client SDK

### Add Dependency

```sh
go get github.com/superstackhq/controllable-go-sdk
```

### Read Property Value Example

```go
package main

import (
	"context"
	"fmt"
	"log"
	"time"

	"github.com/superstackhq/controllable-go-sdk/pkg/client"
)

const (
	ServerEndpoint = "<server_endpoint>"
	AppKey         = "<app_key>"
	Environment    = "<env>"
)

func main() {
	controllableClient := client.NewControllableClient(&client.ControllableClientConfig{
		ServerEndpoint: ServerEndpoint,
		Environment:    Environment,
		AppKey:         AppKey,
		ClientTimeout:  1 * time.Second,
	})

	ctx, cancel := context.WithTimeout(context.Background(), 1*time.Second)
	defer cancel()

	result, err := controllableClient.ReadPropertyValue(ctx, &client.ReadPropertyRequests{
		Requests: []*client.ReadPropertyRequest{
			{
				Reference: &client.PropertyReference{
					Namespace: []string{"services", "userservice"},
					Key:       "min_password_len",
					Version:   "v1",
				},
				Params: map[string]interface{}{
					"country": "IN",
				},
			},
		},
	})

	if err != nil {
		log.Println(err)
		return
	}

	fmt.Println(result.Responses[0].Value.Data)
}
```
