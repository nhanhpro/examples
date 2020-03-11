---
description: >-
  Updates the URL or secret of a webhook endpoint. You could also use this API
  to enable or disable your webhook endpoints. Any parameters not provided will
  be left unchanged.
---

# Update a webhook endpoint

{% api-method method="put" host="https://api.uiza.sh" path="/v1/webhook\_endpoints/:id" %}
{% api-method-summary %}
/v1/webhook\_endpoints/:id
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The identifier of the live event to be updated.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="url" type="string" required=true %}
The URL of the webhook endpoint.
{% endapi-method-parameter %}

{% api-method-parameter name="disabled" type="boolean" required=true %}
Set to true to disable the webhook endpoint. Set to false to enable.
{% endapi-method-parameter %}

{% api-method-parameter name="secret" type="string" required=true %}
The token used to validate the communication between Uiza and the webhook endpoint.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
 "id": "f0f207af-b338-4b7f-8d32-fe9cfa9566eb",
 "url": "https://webhook-test.com/live/updated-route",
 "status": "enabled",
 "secret": "updated-secret",
 "created_at": "2019-12-16T11:31:13Z",
 "updated_at": "2019-12-16T11:31:13Z"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

{% tabs %}
{% tab title="Missing id" %}
```
{
 "message": "Your request is missing id parameter. Please, verify and resubmit.",
 "error_type": "invalid_request_error"
}
```
{% endtab %}

{% tab title="Missing url" %}
```
{
 "message": "Your request is missing url parameter. Please, verify and resubmit.",
 "error_type": "invalid_request_error"
}
```
{% endtab %}

{% tab title="Missing disabled" %}
```
{
 "message": "Your request is missing disabled parameter. Please, verify and resubmit.",
 "error_type": "invalid_request_error"
}
```
{% endtab %}

{% tab title="Missing secret" %}
```
{
 "message": "Your request is missing secret parameter. Please, verify and resubmit.",
 "error_type": "invalid_request_error"
}
```
{% endtab %}
{% endtabs %}
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
 "message": "You are unauthorized to access the requested resource. Please verify and resubmit.",
 "error_type": "invalid_request_error"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
 "message": "The webhook endpoint you requested does not exist.",
 "error_type": "invalid_request_error"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=500 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
 "message": "An unexpected error occurred on Uiza's end.",
 "error_type": "api_error"
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

```text
curl -X PUT https://api.uiza.sh/v1/webhook_endpoints/f0f207af-b338-4b7f-8d32-fe9cfa9566eb 
     -H 'Authorization: uap-c1ffbff4db954ddcb050c6af0b43ba56-41193b64' 
     -d '{"url": "https://webhook-test.com/live/updated-route", "secret": "updated-secret"}'
```

