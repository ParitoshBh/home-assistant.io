---
title: Appwrite
description: Execute Appwrite functions.
ha_category:
  - Network
ha_release: 2025.2
ha_iot_class: Cloud Push
ha_codeowners:
  - '@ParitoshBh'
ha_domain: appwrite
ha_config_flow: true
ha_integration_type: integration
---

With the **Appwrite** {% term integration %}, you can execute functions in your self-hosted Appwrite instance or their cloud offering.

The integration provides an action in the format `appwrite.execute_function_<instance_id>` which can be used to trigger functions. Multiple Appwrite instances are supported, but each must have a unique project ID in your Home Assistant configuration.

{% include integrations/config_flow.md %}

{% configuration_basic %}
URL:
    description: "The URL of Appwrite instance."
    required: true
    type: string
Project ID:
    description: "The ID of project in Appwrite."
    required: true
    type: string
API key:
    description: "The api key should have `execution.write` and `health.read` scopes."
    required: true
    type: string
{% endconfiguration_basic %}

For more information:

- [How to find your Project ID in Appwrite](https://appwrite.io/docs/references#api)
- [How to create and manage API keys with required scopes](https://appwrite.io/docs/advanced/platform/api-keys)

## Example Payload For Action

```yaml
# Basic example
action: appwrite.execute_function_1234560
data:
  function_id: "send_notification"  # Required: The function's ID in Appwrite
  function_method: "POST"          # Optional: HTTP method (default: GET)
  function_body: '{"message": "Motion detected in garage"}'  # Optional: Function body

# Advanced example with all options
action: appwrite.execute_function_0987654
data:
  function_id: "process_image"
  function_body: '{"image_url": "https://example.com/image.jpg"}'   # Optional: Function body
  function_path: "?format=jpg"  # Optional: Additional path parameters
  function_headers:              # Optional: Custom headers
    X-Custom-Header: "value"
  function_scheduled_at: "2025-02-15T06:38:00.000Z"  # Optional: Schedule future execution
  function_async: true          # Optional: Run asynchronously (default: false)
  function_method: "POST"       # Optional: HTTP method (default: GET)
```

## Remove integration

This integration follows standard integration removal, no extra steps are required.

{% include integrations/remove_device_service.md %}
