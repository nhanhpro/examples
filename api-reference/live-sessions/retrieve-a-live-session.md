---
description: >-
  Retrieves the details of an existing live session. The live session’s id that
  was returned upon retrieving all live sessions is required for identifying the
  exact one to be retrieved.
---

# Retrieve a live session

{% api-method method="get" host="https://api.uiza.sh" path="/v1/live\_entities/:entity\_id/live\_sessions/:id" %}
{% api-method-summary %}
/v1/live\_entities/:entity\_id/live\_sessions/:id
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The identifier of the live entity  to be retrieved.
{% endapi-method-parameter %}

{% api-method-parameter name="entity\_id" type="string" required=true %}
The identifier of the live entity whose live sessions are to be retrieved.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
 "id": "1a513f1a-fe0e-4662-9512-233db26811b3",
 "entity_id": "ddb781eb-38d1-42bf-921f-0d2d9130ce15",
 "ingest_key": "live_rJZ7mbPPYw",
 "duration": 220.329,
 "created_at": "2019-10-10T14:41:11Z",
 "updated_at": "2019-10-10T14:44:51Z"
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

{% tab title="Missing entity\_id" %}
```
{
 "message": "Your request is missing entity_id parameter. Please, verify and resubmit.",
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

{% tabs %}
{% tab title="Live session not found" %}
```
{
 "message": "The live session you requested does not exist.",
 "error_type": "invalid_request_error"
}
```
{% endtab %}

{% tab title="Live entity not found" %}
```
{
 "message": "The live entity you requested does not exist.",
 "error_type": "invalid_request_error"
}
```
{% endtab %}
{% endtabs %}
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
curl -X GET https://api.uiza.sh/v1/live_entities/ddb781eb-38d1-42bf-921f-0d2d9130ce15/live_sessions/1a513f1a-fe0e-4662-9512-233db26811b3 
     -H 'Authorization: uap-c1ffbff4db954ddcb050c6af0b43ba56-41193b64' 
```
{% endcode %}



