---
layout: default
title: Python
parent: Client SDKs
nav_order: 1
---

# Python Client SDK

### Installation

- Install the Python Client SDK using `pip` command

```sh
pip install controllable
```

### Read Property Example

```python
from controllable import *
controllable_client = Client("<https://controllable_server_endpoint>", "<app_key>", "<environment_name>", {"read_property_value": 1})

read_property_requests = ReadPropertyRequests()
read_property_requests.add(ReadPropertyRequest(PropertyReference(["services", "userservice"], "min_password_len", "v1"), {"country": "IN", "tenant": "superstack", "client": "controllable"}))

controllable_client.read_property_value(read_property_requests)
print(result.get()[0].get_property_value().get_value())
```
