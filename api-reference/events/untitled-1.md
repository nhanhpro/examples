---
description: >-
  Returns a list of all occurred events, in sorted order where the most recently
  created event shows up first.
---

# List all events

{% api-method method="get" host="https://api.uiza.sh" path="/v1/events" %}
{% api-method-summary %}
/v1/events
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
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

{% endapi-method-response-example-description %}

```
{
 "object": "list",
 "data": [
  {
   "id": "769f8a36-3d11-4a71-921c-0b2fedb79ede",
   "object": "event",
   "api_version": "v1",
   "created_at": "2019-12-24T03:03:58.000321Z",
   "data": {
    "object": {
     "live_entity": {
      "id": "7e949bcd-2eee-4e6d-8cd8-5249f9ccdcd7",
      "name": "Demo allocate13",
      "description": "AFF CUP",
      "ingest": {
       "url": "rtmp://7e949bdcd7-in.streamwiz.dev/transcode",
       "key": "live_0wIJlIGEEH"
      },
      "region": "asia-south1",
      "status": "ready",
      "deleted": false,
      "created_at": "2019-12-24T03:03:54Z",
      "updated_at": "2019-12-24T03:03:54Z"
     },
     "live_session": null
    }
   },
   "type": "live_entities.ready",
   "request_id": "0aba0531-4a5f-48c8-ac0d-6b926b35eba1"
  }
 ]
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
curl -X GET https://api.uiza.sh/v1/events 
     -H 'Authorization: uap-c1ffbff4db954ddcb050c6af0b43ba56-41193b64x'
```
{% endcode %}

