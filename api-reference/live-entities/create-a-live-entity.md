---
description: >-
  To start live streaming, you need to create an `Entity` object. Once the
  request is received, Uiza will allocate resources to serve your live stream.
---

# Create a live entity

{% api-method method="post" host="https://api.uiza.sh" path="/v1/live\_entities" %}
{% api-method-summary %}
/v1/live\_entities
{% endapi-method-summary %}

{% api-method-description %}

{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="name" type="string" required=true %}
The entity's name \(limit 100 characters\). 
{% endapi-method-parameter %}

{% api-method-parameter name="region" type="string" required=true %}
Choose the region closest to the location of your streamer.
{% endapi-method-parameter %}

{% api-method-parameter name="description" type="string" %}
An arbitrary string attached to the object. Often useful for displaying to users.
{% endapi-method-parameter %}

{% api-method-parameter name="dvr" type="boolean" required=false %}
Indicates whether Digital Video Record \(DVR\) is enabled for the live\_entity. Set as `true` to enable and as `false` to disable. The default value is false.
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
  "id": "2b970a39-874a-4d2a-be8a-fd445646d74c",
  "name": "Test Event",
  "description": "Event for Test",
  "region": "in-bangalore-1",
  "status": "init",
  "dvr": true,
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

{% tabs %}
{% tab title="Missing name" %}
```
{
 "message": "Your request is missing name parameter. Please, verify and resubmit.",
 "error_type": "invalid_request_error"
}
```
{% endtab %}

{% tab title="Missing region" %}
```
{
 "message": "Your request is missing region parameter. Please, verify and resubmit.",
 "error_type": "invalid_request_error"
}
```
{% endtab %}

{% tab title="Invalid region" %}
```
{
 "message": "The requested region is invalid. See the list of available regions here: docs.uiza.io/getting-started/regions.",
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
```text
curl -X POST https://api.uiza.sh/v1/live_entities 
     -H 'Authorization: uap-c1ffbff4db954ddcb050c6af0b43ba56-41193b64' 
     -H 'cache-control: no-cache' 
     -d '{"name": "Demo", "region": "asia-southeast-2", "description": "AFF CUP"}, "dvr":true'
```
{% endcode %}

{% hint style="info" %}
Defining your region helps Uiza allocate the resources that are closest to your streamers' locations. This will minimize the risks of network issues. While we are adding more and more regions to our network, here are the currently available regions. 

`in-bangalore-1` \(Bangalore - India\)

`in-mumbai-1` \(Mumbai - India\)
{% endhint %}

