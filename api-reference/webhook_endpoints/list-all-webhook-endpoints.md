---
description: >-
  Returns a list of existing webhook endpoints in sorted order where the most
  recently created endpoints show up first.
---

# List all webhook endpoints

{% api-method method="get" host="https://api.uiza.sh" path="/v1/webhook\_endpoints" %}
{% api-method-summary %}
/v1/webhook\_endpoints
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="status" type="string" required=false %}
Indicates the current status of the webhook endpoint, either disabled or enabled.
{% endapi-method-parameter %}

{% api-method-parameter name="page\_token" type="string" required=false %}
The maximum number of objects to be returned, between 1 and 100.
{% endapi-method-parameter %}

{% api-method-parameter name="page\_size" type="string" required=false %}
The pagination cursor of the result page to be retrieved.
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
 "data": [
  {
   "id": "f0f207af-b338-4b7f-8d32-fe9cfa9566eb",
   "url": "https://webhook-test.com/live/created",
   "status": "enabled",
   "created_at": "2019-12-16T10:57:32Z",
   "updated_at": "2019-12-16T10:57:32Z"
  }
 ],
 "next_page_token": "eyJjcmVhdGVkX2F0IjoxNTc2MDA4NjkxMDAwLCJpZCI6IjAwNzVmZjcyLWE0ODYtNDg0Ni05Y2NjLWY1ZWU4YTA0MmQ0NSJ9"
}
```
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
curl -X GET 'https://api.uiza.sh/v1/webhook_endpoints' 
     -H 'Authorization: uap-c1ffbff4db954ddcb050c6af0b43ba56-41193b64' 
```
{% endcode %}



