---
description: >-
  Creates a video entity and requests Uiza to retrieve the video file following
  the URL provided in your request.
---

# Create a video entity

{% api-method method="post" host="https://api.uiza.sh" path="/v1/video\_entities" %}
{% api-method-summary %}
/v1/video\_entities
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="name" type="string" required=true %}
The name of your video entity.
{% endapi-method-parameter %}

{% api-method-parameter name="url" type="string" required=true %}
The URL that redirects Uiza to your video storage.
{% endapi-method-parameter %}

{% api-method-parameter name="input\_type" type="string" required=true %}
Indicates the protocol of your video storage. Could either be HTTP, FTP or S3.
{% endapi-method-parameter %}

{% api-method-parameter name="description" type="string" required=false %}
Describes the content of your video. Often useful for displaying to viewers.
{% endapi-method-parameter %}

{% api-method-parameter name="short\_description" type="string" required=false %}
A shortened version of your description.
{% endapi-method-parameter %}

{% api-method-parameter name="poster" type="string" required=false %}
The URL of the video entity's poster image.
{% endapi-method-parameter %}

{% api-method-parameter name="thumbnail" type="string" required=false %}
The URL of the video entity's thumbnail image.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```javascript
{
 "id": "f42b4ac3-869e-4010-8e21-042e40be7655",
 "name": "Sample Demo-Video",
 "description": "Lorem ipsum dolor sit amet, vis odio oratio scripserit ut",
 "short_description": "Duo ad graeci principes, legimus mnesarchum scribentur ut pro",
 "view": 0,
 "poster": "Lorem ipsum dolor",
 "thumbnail": "Lorem ipsum dolor",
 "type": "VOD",
 "publish_to_cdn": "not-ready",
 "created_at": "2019-12-11T02:47:04Z",
 "updated_at": "2019-12-11T02:47:04Z"
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

{% tabs %}
{% tab title="Missing name" %}
```javascript
{
 "message": "Your request is missing name parameter. Please, verify and resubmit.",
 "error_type": "invalid_request_error"
}
```
{% endtab %}

{% tab title="Missing url" %}
```
{
 "message": "Your request is missing url parameter. Please, verify and resubmit.",
 "error_type": "invalid_request_error"
}
```
{% endtab %}

{% tab title="Missing input\_type" %}
```
{
 "message": "Your request is missing input_type parameter. Please, verify and resubmit.",
 "error_type": "invalid_request_error"
}
```
{% endtab %}

{% tab title="Invalid input\_type" %}
```
{
 "message": "The input_type you provided is invalid. Please, make sure it is either HTTP, FTP or S3, and try again.",
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
```javascript
curl -X POST https://api.uiza.sh/v1/video_entities 
     -H 'Authorization: uap-c1ffbff4db954ddcb050c6af0b43ba56-41193b64' 
     -d '{"name":"Sample Demo-Video", "description":"Lorem ipsum dolor sit amet, vis odio oratio scripserit ut","short_description":"Duo ad graeci principes, legimus mnesarchum scribentur ut pro","view":1000,"poster":"Lorem ipsum dolor","thumbnail":"Lorem ipsum dolor\",\"type\":\"VOD\",\"duration\":11213,\"publish_to_cdn\":\"queue\"}'
```
{% endcode %}

