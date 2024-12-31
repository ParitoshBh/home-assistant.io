---
title: Appwrite
description: Execute Appwrite functions.
ha_category:
  - Network
ha_release: 2025.2
ha_iot_class: Cloud Polling
ha_codeowners:
  - '@ParitoshBh'
ha_domain: appwrite
ha_config_flow: true
ha_integration_type: integration
---

With the **Appwrite** {% term integration %}, you can execute functions in your self-hosted Appwrite instance or their cloud offering.

The integration provides `appwrite.execute_function_{id}` action which can be used to trigger a function. Multiple instances of Appwrite are supported as long as the project id is unique.

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

[Appwrite Project ID Reference](https://appwrite.io/docs/references#api)

[Appwrite API Key Reference](https://appwrite.io/docs/advanced/platform/api-keys)

## Example Payload For Action

```yaml
action: appwrite.execute_function_{id}
data:
  function_id: "name-of-your-function"
  function_body: "['this','is','test']"
  function_path: "?query=value"
  function_headers:
    header: value
  function_scheduled_at: "2020-10-15T06:38:00.000Z"
  function_async: true
  function_method: "GET"
```

## Remove integration

This integration follows standard integration removal, no extra steps are required.

{% include integrations/remove_device_service.md %}
