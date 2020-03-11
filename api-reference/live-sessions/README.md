# Live sessions

A **`live_session`** is the event where a live signal is ingested and broadcasted uninterruptedly. An individual `live_entity` could contain multiple live sessions. 

The API allows you to list all sessions that belong to a `live_entity` which is identified by its `id`, or retrieve a specific `live_session`.

### The session object

#### Attributes

> **`id`** _string_
>
> The unique identifier for the live session.

> **`entity_id`** _string_
>
> The unique identifier for the `live_entity` whose sessions are going to be retrieved.

> **`key`** _string_
>
> The stream key of the `live_entity` that is requested.

> **`duration`** _number_
>
> The `duration` of one `live_session` is counted from the moment Uiza receives the first signal of the live feed until the last signal of that live feed. Broadcasting sessions do not contain any `duration`.

> **`created_at`** _string_
>
> The timestamp, at which a `live_session` is created automatically when Uiza receives a live signal, follows the [ISO 8601 standard](https://www.w3.org/TR/NOTE-datetime-970915).

> **`updated_at`** _string_
>
> The timestamp, at which the most recent update to the `live_session` occurred, follows the [ISO 8601 standard](https://www.w3.org/TR/NOTE-datetime-970915).

