# Events

Uiza  creates **`event`** objects containing data of the events occurred in your Uiza account that your applications might be interested in, for instance, a `live_entity` is created, a `ingest.key` is reset or a `video_entity` is deleted, etc. 

While some API requests do not cause any `event` to be created such as _Retrieve a live entity_, other APIs may generate more than one `event`. For example, when you create a live entity, a `live_entity.created`, a `live_entity.resource.accepted` and a `live_entity.ready` events will be created consecutively.

Fundamentally, an `event` is created whenever there is a change in the state of an API resource. Therefore, there are `events` created without the trigger of any API request. A `live_entity.publish` created when Uiza receives your live feed signal is triggered by your broadcasting software, not as the result of an API request.

### The event object

#### Attributes

> **`id`** _string_
>
> The unique identifier for the event.

> **`object`** _string_
>
> The type of the object which is identified by the `id`. In this case, the value to the `object` is _"event"_.

> **`api_version`** _string_
>
> The version of the API that were used to trigger the `event`. Uiza uses this to ensure the backwards-compatibility of our APIs.

> **`created_at`** _string_
>
> The timestamp, at which the `event` is created, follows the [ISO 8601 standard](https://www.w3.org/TR/NOTE-datetime-970915).

> **`data`** _object_
>
> The object containing data of the states at the time of change of impacted resources.

> **`type`** _string_
>
> The string represents the type of the `event`. You could find the list of the event types [here](https://starboy.gitbook.io/uiza-doc/api-reference/events/types-of-event).

> **`request_id`** _string_
>
> The unique identifier for the API request triggered the event.

