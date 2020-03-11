---
description: >-
  Returns a list of existing live entities in sorted order where the most
  recently created entities show up first.
---

# List all live entities

{% api-method method="get" host="https://api.uiza.sh" path="/v1/live\_entities" %}
{% api-method-summary %}
/v1/live\_entities
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="page\_size" type="number" required=false %}
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

{% endapi-method-response-example-description %}

```
{
  "data": [
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
  ],
  "next_page_token": "eyJjcmVhdGVkX2F0IjoxNTc2MDA4NjkxMDAwLCJpZCI6IjAwNzVmZjcyLWE0ODYtNDg0Ni05Y2NjLWY1ZWU4YTA0MmQ0NSJ9",
  "prev_page_token": ""
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

{% api-method method="get" host="https://api.uiza.sh" path="/v1/live\_entities" %}
{% api-method-summary %}

{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="" type="string" required=false %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=401 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% code title="Sample Request" %}
```text
curl -X GET https://api.uiza.sh/v1/live_entities 
    -H 'Accept: */*' 
    -H 'Authorization: uap-c1ffbff4db954ddcb050c6af0b43ba56-41193b64' 
    -H 'Cache-Control: no-cache' 
    -H 'Connection: keep-alive'
```
{% endcode %}

