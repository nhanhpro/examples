---
description: >-
  Returns a list of existing video entities in sorted order where the most
  recently created entities show up first.
---

# List all video entities

{% api-method method="get" host="https://api.uiza.sh" path="/v1/video\_entities" %}
{% api-method-summary %}
/v1/video\_entities
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
   "id": "f42b4ac3-869e-4010-8e21-042e40be7655",
   "name": "Sample Demo-Video",
   "description": "Lorem ipsum dolor sit amet, vis odio oratio scripserit ut",
   "short_description": "Duo ad graeci principes, legimus mnesarchum scribentur ut pro",
   "view": 1000,
   "poster": "Lorem ipsum dolor",
   "thumbnail": "Lorem ipsum dolor",
   "type": "VOD",
   "duration": 11213,
   "publish_to_cdn": "queue",
   "created_at": "2019-12-11T02:47:04Z",
   "updated_at": "2019-12-11T02:47:04Z"
  }
 ],
 "next_page_token": "eyJjcmVhdGVkX2F0IjoxNTc2MDA4NjkxMDAwLCJpZCI6IjAwNzVmZjcyLWE0ODYtNDg0Ni05Y2NjLWY1ZWU4YTA0MmQ0NSJ9",
 "prev_page_token": "2MDA4NjkxMDAwLCJpZCI6IjAwNzVmZjeyJjcmVhdGVkX2F0IjoxNTc1ZWU4YTA0MmQ0NSJ9cyLWE0ODYtNDg0Ni05Y2NjLWY"
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
curl -X GET https://api.uiza.sh/v1/video_entities 
     -H 'Authorization: uap-c1ffbff4db954ddcb050c6af0b43ba56-41193b64' 
```
{% endcode %}

