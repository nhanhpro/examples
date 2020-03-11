---
description: >-
  Retrieves the details of an existing video entity. The entity’s id that was
  returned upon entity creation is required for identifying the exact video
  entity to be retrieved.
---

# Retrieve a video entity

{% api-method method="get" host="https://api.uiza.sh" path="/v1/video\_entities/:id" %}
{% api-method-summary %}
/v1/video\_entities/:id
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The identifier of the video entity to be retrieved.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
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
 "message": "The video entity you requested does not exist.",
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
curl -X GET https://api.uiza.sh/v1/video_entities/f42b4ac3-869e-4010-8e21-042e40be7655 
     -H 'Authorization: uap-c1ffbff4db954ddcb050c6af0b43ba56-41193b64' 
```
{% endcode %}

