---
description: >-
  Returns a list of existing live sessions that belong to the requested live
  entity, in sorted order where the most recently created live session shows up
  first.
---

# List all live sessions

{% api-method method="get" host="https://api.uiza.sh" path="/v1/live\_entities/:id/live\_sessions" %}
{% api-method-summary %}
/v1/live\_entities/:id/live\_sessions
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The identifier of the live entity whose live sessions are to be retrieved.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter name="page\_size" type="string" required=false %}
The maximum number of objects to be returned, between 1 and 100.
{% endapi-method-parameter %}

{% api-method-parameter name="page\_token" type="string" required=false %}
The pagination cursor of the result page to be retrieved.
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Cake successfully retrieved.
{% endapi-method-response-example-description %}

```
{
  "data": [
    {
      "id": "1a513f1a-fe0e-4662-9512-233db26811b3",
      "entity_id": "ddb781eb-38d1-42bf-921f-0d2d9130ce15",
      "stream_key": "live_rJZ7mbPPYw",
      "duration": 220.329,
      "created_at": "2019-10-10T14:41:11Z",
      "updated_at": "2019-10-10T14:44:51Z"
    },
    {
      "id": "7263ba91-22a8-4cac-98ee-3651e5da4e1f",
      "entity_id": "ddb781eb-38d1-42bf-921f-0d2d9130ce15",
      "stream_key": "live_rJZ7mbPPYw",
      "duration": 24.305,
      "created_at": "2019-10-10T14:38:26Z",
      "updated_at": "2019-10-10T14:38:50Z"
    }
  ],
  "next_page_token": "eyJjcmVhdGVkX2F0IjoxNTc2MDA4NjkxMDAwLCJpZCI6IjAwNzVmZjcyLWE0ODYtNDg0Ni05Y2NjLWY1ZWU4YTA0MmQ0NSJ9"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
 "message": "Your request is missing id parameter. Please, verify and resubmit.",
 "error_type": "invalid_request_error"
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

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
 "message": "The live session you requested does not exist.",
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
curl -X GET https://api.uiza.sh/v1/live_entities/22013d8a-d5fa-48f0-9a63-1f471ca9e81d/sessions 
    -H 'Accept: */*' 
    -H 'Authorization: uap-c1ffbff4db954ddcb050c6af0b43ba56-41193b64' 
    -H 'Cache-Control: no-cache' 
    -H 'Connection: keep-alive'
```
{% endcode %}



