---
description: >-
  Updates a specified video entity's name, description, poster and thumbnail
  imaged. Any parameters not provided will be left unchanged.
---

# Update a video entity

{% api-method method="put" host="https://api.uiza/sh" path="/v1/video\_entities/:id" %}
{% api-method-summary %}
/v1/video\_entities/:id
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The identifier of the video entity to be updated.
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="name" type="string" required=false %}
The new name of the video entity to be updated.
{% endapi-method-parameter %}

{% api-method-parameter name="description" type="string" required=false %}
The new description of the video entity to be updated.
{% endapi-method-parameter %}

{% api-method-parameter name="short\_description" type="string" required=false %}
The new short description of the video entity to be updated.
{% endapi-method-parameter %}

{% api-method-parameter name="poster" type="string" required=false %}
The URL of the new video entity's poster image to be updated.
{% endapi-method-parameter %}

{% api-method-parameter name="thumbnail" type="string" required=false %}
The URL of the new video entity's thumbnail image to be updated.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
 "id": "f42b4ac3-869e-4010-8e21-042e40be7655",
 "name": "Sample Demo-Video 1",
 "description": "Habemus nusquam tractatos ut eam, eu brute aliquam fuisset sea",
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
curl -X PUT https://api.uiza.sh/v1/video_entities/f42b4ac3-869e-4010-8e21-042e40be7655 
     -H 'Authorization: uap-c1ffbff4db954ddcb050c6af0b43ba56-41193b64' 
     -d '{"name":"Sample Demo-Video 1", "description":"Habemus nusquam tractatos ut eam, eu brute aliquam fuisset sea"}'
```
{% endcode %}

