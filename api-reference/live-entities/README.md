# Live entities

A **`live_entity`** contains the information required for Uiza to successfully allocate resources to power the `live_entity`'s live broadcasting sessions. You can reuse a `live_entity` and broadcast multiple live sessions sequentially. 

The API allows you to create, delete, reset your `ingest.key`, and update the `name` and `description` of the `live_entity`. Individual entities and a list of all your entities are retrievable via these APIs too.

### The live entity object

#### Attributes

> **`id`** _string_
>
> The unique identifier for the live entity.

> **`name`** _string_
>
> The name of your live entity. \(limit 100 characters\)

> **`description`** _string_
>
> Describes the content of the live entity. Often useful for displaying to viewers. You could update this accordingly to suit different sessions of a single live entity.

> **`ingest`** _object_
>
> Contains the information required to access to Uiza's ingest servers. Use the `key` and `url` to configure your broadcasting software.

> **`playback`** _list_
>
> Contains the playback URL for different streaming protocols including HLS fMP4 \(`hls`\) and MPEG-dash \(`mpd`\). Use this URL to configure your player to play the live stream.

> **`region`** _string_
>
> The geographical region where your live streams are broadcasted from. In case your region is not yet supported, try the nearest available one. Here are the regions that Uiza currently supports:
>
> `in-bangalore-1` Bangalore, India.
>
> `in-mumbai-1` Mumbai, India.

> **`status`** _string_
>
> Once the request to create a `live_entity` is received, Uiza will allocate resources in the requested `region`. While the process may take up to 1 minute, the `status` of the `live_entity` is `init`. This will be updated to `ready` once resources are successfully allocated and to `broadcasting` during a broadcasting session.

> **`dvr`** _string_
>
> Indicates whether Digital Video Record \(DVR\) is enabled for the `live_entity`. Set to `true` to enable and to `false` to disable this feature.

> **`created_at`** _string_
>
> The timestamp, at which the `live_entity` is created, follows the [ISO 8601 standard](https://www.w3.org/TR/NOTE-datetime-970915).

> **`updated_at`** _string_
>
> The timestamp, at which the most recent update to the `live_entity` occurred, follows the [ISO 8601 standard](https://www.w3.org/TR/NOTE-datetime-970915).

