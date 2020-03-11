---
description: Sets the 'dvr' parameter of a live entity to 'false'.
---

# Disable live entity DVR

{% api-method method="post" host="https://api.uiza.sh" path="/v1/live\_entities/{id}:disable\_dvr" %}
{% api-method-summary %}
/v1/live\_entities/{id}:disable\_dvr
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" required=true type="string" %}
.The identifier of the live entity where `dvr` will be set to `false`
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
DVR successfully set to `false`
{% endapi-method-response-example-description %}

```
{
  "id": "2b970a39-874a-4d2a-be8a-fd445646d74c",
  "name": "Test Event",
  "description": "Event for Test",
  "region": "in-bangalore-1",
  "status": "init",
  "dvr": false,
  "encode": false,
  "ingest": null,
  "playback": null,
  "relay": [
    {
      "url": "rtmp://youtu.be/live",
      "key": "Abco1"
    }
  ],
  "created_at": "2019-10-03T17:34:49Z",
  "updated_at": "2019-10-03T17:34:49Z"
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
 "message": "The live entity you requested does not exist.",
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
curl -X POST https://api.uiza.sh/v1/live_entities/22013d8a-d5fa-48f0-9a63-1f471ca9e81d:disable_dvr 
    -H 'Accept: */*' 
    -H 'Authorization: uap-c1ffbff4db954ddcb050c6af0b43ba56-41193b64' 
    -H 'Cache-Control: no-cache' 
    -H 'Connection: keep-alive'the identifier of the live entity where dvr will be set to false
```
{% endcode %}

