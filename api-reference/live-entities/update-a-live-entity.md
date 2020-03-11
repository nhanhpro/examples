---
description: >-
  Updates a specified live entity's name and/or description. Any parameters not
  provided will be left unchanged.
---

# Update a live entity

{% api-method method="put" host="https://api.uiza.sh" path="/v1/live\_entities/:id" %}
{% api-method-summary %}
/v1/live\_entities/:id
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The identifier of the live entity to be updated.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="name" type="string" required=false %}
The new name of the live entity to be updated.
{% endapi-method-parameter %}

{% api-method-parameter name="description" type="string" required=false %}
The new description of the live entity to be updated.
{% endapi-method-parameter %}

{% api-method-parameter name="dvr" type="string" required=false %}
Set to true to enable and to false to disable video recording.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Cake successfully retrieved.
{% endapi-method-response-example-description %}

```
{
  "id": "22013d8a-d5fa-48f0-9a63-1f471ca9e81d",
  "name": "Test Event Updated",
  "description": "Event for Test",
  "ingest": {
    "url": "rtmp://f45dd07a0e-in.uizadev.io/transcode",
    "key": "live_TB62vHgxSY"
  },
  "playback": {
    "hls": "https://f45dd07a0e.uizadev.io/fmp4/22013d8a-d5fa-48f0-9a63-1f471ca9e81d/master.m3u8"
  },
  "relay": [
    {
      "url": "rtmp://youtu.be/live",
      "key": "Abco1"
    }
  ],
  "region": "in-bangalore-1",
  "status": "ready",
  "dvr": false,
  "encode": false,
  "created_at": "2019-12-11T02:47:04Z",
  "updated_at": "2019-12-16T02:53:30Z"
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
curl -X PUT https://api.uiza.sh/v1/live_entities/22013d8a-d5fa-48f0-9a63-1f471ca9e81d 
    -H 'Accept: */*' 
    -H 'Authorization: uap-c1ffbff4db954ddcb050c6af0b43ba56-41193b64' 
    -H 'Cache-Control: no-cache' 
    -H 'Connection: keep-alive' 
    -d '{"name": "Test Event Updated", "description": "Event for Test"}, "dvr": false'
```
{% endcode %}

