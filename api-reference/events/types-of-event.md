# Types of event

Our event types are designed following the `resource.event` and `resource.subresource.event` format for your intuitive coding. As new event types will be added as we roll out more features or make updates to existing ones, we recommend you to revisit this list whenever you receive a new event type.

#### Live entity and session related

> **`live_entities.created`**    _`data.object`_ _is a_ [_`live_entity`_](https://docs.uiza.io/api-reference/live-entities)_._
>
> Occurs whenever a live entity is created.

> **`live_entities.updated`**    _`data.object`_ _is a_ [_`live_entity`_](https://docs.uiza.io/api-reference/live-entities)_._
>
> Occurs whenever a live entity is updated.

> **`live_entities.deleted`**    _`data.object` is a_ [_`live_entity`_](https://docs.uiza.io/api-reference/live-entities)_._
>
> Occurs whenever a live entity is deleted.

> **`live_entities.ready`**    _`data.object`_ _is a_ [_`live_entity`_](https://docs.uiza.io/api-reference/live-entities)_._
>
> Occurs whenever the `status` of a live entity is changed to `ready`. This event indicates that the live entity you created is ready to ingest and broadcast.

> **`live_entities.publish`**    _`data.object`_ _contains a_ [_`live_entity`_](https://docs.uiza.io/api-reference/live-entities) _and its_ [_`live_session`_](https://docs.uiza.io/api-reference/live-sessions)_._
>
> Occurs whenever a live entity receives the first live signal of a live session.

> **`video_entities.created`**    _`data.object`_ is a [`video_entity`](https://docs.uiza.io/api-reference/video-entities)\`\`
>
> Occurs when a user sends a signal with DVR set to `true` . This event happens after **`live_entities.publish`** and indicates the creation of a new live record from the user's live feed. Uiza creates a record as **video entity.**

> **`live_entities.publish_done`**    _`data.object`_ _contains a_ [_`live_entity`_](https://docs.uiza.io/api-reference/live-entities) _and its_ [_`live_session`_](https://docs.uiza.io/api-reference/live-sessions)_._
>
> Occurs whenever a live session ends.

> **`live_entities.resource.accepted`**    _`data.object`_ _is a_ [_`live_entity`_](https://docs.uiza.io/api-reference/live-entities)_._
>
> Occurs whenever Uiza has successfully allocated resources for your live entity following its creation.

> **`live_entities.resource.denied`**    _`data.object`_ _contains a_ [_`live_entity`_](https://docs.uiza.io/api-reference/live-entities) _and its_ [_`live_session`_](https://docs.uiza.io/api-reference/live-sessions)_._
>
> Occurs whenever Uiza could not allocate resources for your live entity. Uiza typically retries several times before creating this type of event. The `retry` attribute indicates the retry count.

> **`live_entities.key.reset`**     _`data.object`_ _is a_ [_`live_entity`_](https://docs.uiza.io/api-reference/live-entities)_._
>
> Occurs whenever the `ingest.key` of a live entity is reset.

> **`live_entities.on_rebalance`**     _`data.object`_ _is a_ [_`live_entity`_](https://docs.uiza.io/api-reference/live-entities)_._
>
> Occurs when the current streaming serve reaches the usage threshold. Uiza will rebalance the additional workload to another server.

> **`live_entities.on_fail_over`**     _`data.object`_ _is a_ [_`live_entity`_](https://docs.uiza.io/api-reference/live-entities)_._
>
> Occurs when something goes wrong with the current streaming server. Uiza will allocate a new server to resume your streaming. Your live session will be interrupted during this process.

