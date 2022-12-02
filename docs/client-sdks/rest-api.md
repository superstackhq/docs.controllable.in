---
layout: default
title: REST API
parent: Client SDKs
nav_order: 2
---

# REST API

### Read Property Value

Request
{: .label }

```
POST /api/v1/properties/execute HTTP/1.1
Host: localhost:8001
Authorization: AppKey <APP_KEY>
Content-Type: application/json
Content-Length: 787

{
    "operation": "READ_PROPERTY_VALUE",
    "environment": "production",
    "requests": [
        {
            "property": {
                "namespace": ["services", "userservice"],
                "key": "min_password_len",
                "version": "v1"
            },
            "params": {
                "tenant": "superstack",
                "client": "controllable",
                "country": "US"
            }
        },
        {
            "property": {
                "namespace": ["services", "userservice"],
                "key": "min_password_len",
                "version": "v1"
            },
            "params": {
                "tenant": "superstack",
                "client": "controllable",
                "country": "IN"
            }
        }
    ]
}
```

Response
{: .label .label-green }

```json
{
    "responses": [
        {
            "success": true,
            "value": {
                "id": "6385da0a03c91ff1924c1e2a",
                "data": 17,
                "rule": {
                    "expression": ""
                },
                "segment": {
                    "path": [
                        {
                            "name": "tenant",
                            "value": "superstack"
                        },
                        {
                            "name": "client",
                            "value": "controllable"
                        }
                    ]
                }
            }
        },
        {
            "success": true,
            "value": {
                "id": "63848d1c7ef6ceba9223da1f",
                "data": 10,
                "rule": {
                    "expression": "country == \"IN\""
                },
                "segment": {
                    "path": [
                        {
                            "name": "tenant",
                            "value": "superstack"
                        },
                        {
                            "name": "client",
                            "value": "controllable"
                        }
                    ]
                }
            }
        }
    ]
}
```

-------------

### Create Property Value

Request
{: .label }

```
POST /api/v1/properties/execute HTTP/1.1
Host: localhost:8001
Authorization: AppKey <APP_KEY>
Content-Type: application/json
Content-Length: 787

{
    "operation": "CREATE_PROPERTY_VALUE",
    "environment": "production",
    "requests": [
        {
            "property": {
                "namespace": ["services", "userservice"],
                "key": "min_password_len",
                "version": "v1"
            },
            "value": {
                "data": 8,
                "segment": {
                "path": [
                    {
                        "name": "tenant",
                        "value": "superstack"
                    },
                    {
                        "name": "client",
                        "value": "controllable"
                    }]
                },
                "rule": {"expression": "country==\"US\""}
            }
        }
    ]
}
```

Response
{: .label .label-green }

```json
{
    "responses": [
        {
            "success": true,
            "value": {
                "id": "638a1cb231887fa5c9bd8bbf",
                "data": 8,
                "rule": {
                    "expression": "country==\"US\""
                },
                "segment": {
                    "path": [
                        {
                            "name": "tenant",
                            "value": "superstack"
                        },
                        {
                            "name": "client",
                            "value": "controllable"
                        }
                    ]
                }
            }
        }
    ]
}
```

--------------

### Update Property Value

Request
{: .label }

```
POST /api/v1/properties/execute HTTP/1.1
Host: localhost:8001
Authorization: AppKey <APP_KEY>
Content-Type: application/json
Content-Length: 839

{
    "operation": "UPDATE_PROPERTY_VALUE",
    "environment": "production",
    "requests": [
        {
            "property": {
                "namespace": ["services", "userservice"],
                "key": "min_password_len",
                "version": "v1"
            },
            "value": {
                "id": "6384e7ed9a1a21be9d556ef4",
                "data": 12,
                "segment": {
                "path": [
                    {
                        "name": "tenant",
                        "value": "superstack"
                    },
                    {
                        "name": "client",
                        "value": "controllable"
                    }]
                },
                "rule": {"expression": "country==\"US\""}
            }
        }
    ]
}
```

Response
{: .label .label-green }

```json
{
    "responses": [
        {
            "success": true,
            "value": {
                "id": "638a1ced31887fa5c9bd8bc1",
                "data": 12,
                "rule": {
                    "expression": "country==\"US\""
                },
                "segment": {
                    "path": [
                        {
                            "name": "tenant",
                            "value": "superstack"
                        },
                        {
                            "name": "client",
                            "value": "controllable"
                        }
                    ]
                }
            }
        }
    ]
}
```

----------

### Delete Property Value

Request
{: .label }

```
POST /api/v1/properties/execute HTTP/1.1
Host: localhost:8001
Authorization: AppKey GRVjUF2utBSVvrJxVMjNMYHNwYJdqRFLki1hImnnbAXizdDVThZaWXou4TMTnBMiKqojAZQyqoS32k6w8MtVFDdr5BjXTSaU1zlKTifXIKoQqjscvWoP6SCFBEJvwoeY
Content-Type: application/json
Content-Length: 397

{
    "operation": "DELETE_PROPERTY_VALUE",
    "environment": "production",
    "requests": [
        {
            "property": {
                "namespace": ["services", "userservice"],
                "key": "min_password_len",
                "version": "v1"
            },
            "value": {
                "id": "638a1cb231887fa5c9bd8bbf"
            }
        }
    ]
}
```

Response
{: .label .label-green }

```json
{
    "responses": [
        {
            "success": true,
            "value": {
                "id": "638a1cb231887fa5c9bd8bbf",
                "data": null,
                "rule": null,
                "segment": null
            }
        }
    ]
}
```

