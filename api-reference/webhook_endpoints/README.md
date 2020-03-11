# Webhook endpoints

**Webhook** provides a mechanism for Uiza to notifies you about the `events` that happen in your Uiza account. When something interesting happens \(a `live_entity` is created, a `ingest.key` is reset, a `video_entity` is deleted, etc.\) Uiza creates an `event` object which contains the details of what just occurred. This `event` will then be sent to the webhook endpoint, a pre-configured URL where Uiza makes HTTP POST requests to.

A single `event` could be be sent to multiple webhook endpoints. You could generate endpoint URLs for your tests [here](https://webhook.site/).

### The webhook endpoint object

#### Attributes

> **`id`** _string_
>
> The unique identifier for the object.

> **`url`** _string_
>
> The URL of the `webhook_endpoint`.

> **`status`** _string_
>
> Indicates the current status of the `webhook_endpoint`, which is either `disabled` or `enabled`.

> **`secret`** _string_
>
> Setting a webhook **secret** helps you verify if the requests sent to your webhook endpoint is from Uiza. We highly recommend following [JSON Web Token](https://jwt.io/) format. ****

> **`created_at`** _string_
>
> The timestamp, at which the `webhook_endpoint`is created, follows the [ISO 8601 standard](https://www.w3.org/TR/NOTE-datetime-970915).

> **`updated_at`** _string_
>
> The timestamp, at which the most recent update to the `webhook_endpoint` occurred, follows the [ISO 8601 standard](https://www.w3.org/TR/NOTE-datetime-970915).

