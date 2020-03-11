---
description: >-
  Retrieves the details of an existing Entity. The entity’s id that was returned
  upon entity creation is required for identifying the exact live entity to be
  retrieved.
---

# Retrieve a live entity

{% api-method method="get" host="https://api.uiza.sh" path="/v1/live\_entities/:id" %}
{% api-method-summary %}
/v1/live\_entities/:id
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The identifier of the live entity to be retrieved
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Cake successfully retrieved.
{% endapi-method-response-example-description %}

```http
{
  "id": "22013d8a-d5fa-48f0-9a63-1f471ca9e81d",
  "name": "Demo ap 1",
  "description": "AFF CUP",
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
  "dvr": true,
  "encode": false,
  "created_at": "2019-12-11T02:47:04Z",
  "updated_at": "2019-12-16T02:53:30Z"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```http
{
 "message": "Your request is missing id parameter. Please, verify and resubmit.",
 "error_type": "invalid_request_error"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```http
{
 "message": "You are unauthorized to access the requested resource. Please verify and resubmit.",
 "error_type": "invalid_request_error"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=404 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```http
{
 "message": "The live entity you requested does not exist.",
 "error_type": "invalid_request_error"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=500 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```http
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
```http
curl -X GET https://api.uiza.sh/v1/live_entities/22013d8a-d5fa-48f0-9a63-1f471ca9e81d 
    -H 'Accept: */*' 
    -H 'Authorization: uap-c1ffbff4db954ddcb050c6af0b43ba56-41193b64' 
    -H 'Cache-Control: no-cache' 
    -H 'Connection: keep-alive'
```
{% endcode %}

