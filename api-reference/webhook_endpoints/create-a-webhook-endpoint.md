---
description: >-
  A URL and a secret are required for webhook endpoint creation. While URLs are
  endpoints where Uiza sends the events to, secrets are used to generate webhook
  signatures.
---

# Create a webhook endpoint

{% api-method method="post" host="https://api.uiza.sh" path="/v1/webhook\_endpoints" %}
{% api-method-summary %}
/v1/webhook\_endpoints
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="secret" type="string" required=true %}
The token used to validate the communication between Uiza and the webhook endpoint.
{% endapi-method-parameter %}

{% api-method-parameter name="url" type="string" required=true %}
The URL of the webhook endpoint.
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
 "url": "https://webhook-test.com/live/created",
 "status": "enabled",
 "created_at": "2019-12-16T10:57:32Z",
 "updated_at": "2019-12-16T10:57:32Z"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

{% tabs %}
{% tab title="Missing URL" %}
```
{
 "message": "Your request is missing url parameter. Please, verify and resubmit.",
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

{% code title="Sample Request" %}
```text
curl -X POST https://api.uiza.sh/v1/webhook_endpoints
     -H 'Authorization: uap-c1ffbff4db954ddcb050c6af0b43ba56-41193b64'
     -d '{"url": "https://webhook-test.com/live/created", "secret": "a-secret"}'
```
{% endcode %}



