# Video entities

A **`video_entity`** is created every time a video is uploaded to Uiza via a URL which redirects Uiza to your video storage to retrieve the video file. This URL could be either a _direct HTTP/HTTPS_ link or a URL that leads to your _FTP or S3 storage_. 

Once the video has been successfully retrieved, Uiza transcodes the file into several renditions that have different resolutions and are compatible to different streaming protocol such as _HLS, fMP4_... These renditions are made available to your viewers by you publishing them to Uiza's _Content Delivery Network \(CDN\)_ via Uiza APIs.

The APIs allow you to create, delete, publish, update the information of the video\_entities and retrieve your entities individually or collectively.

### The video entity object

#### Attributes

> **`id`** _string_
>
> The unique identifier for the video entity.

> **`name`** _string_
>
> The name of your video entity.

> **`description`** _string_
>
> Describes the content of the video entity. Often useful for displaying to viewers.

> **`short_description`** _string_
>
> A shortened version of your `description`.

> **`view`** _number_
>
> The number of times that the video has been viewed.

> **`poster`** _string_
>
> The URL of the video entity's poster image.

> **`thumbnail`** _string_
>
> The URL of the video entity's thumbnail image.

> **`type`** _string_
>
> Could be either `VOD` or `AOD`. `AOD` indicates that your `video_entity` contains an audio file only, and `VOD` indicates it contains a video file.

> **`input_type`** string
>
> It could be either `dvr` or `s3-uiza`. `dvr` indicates that your `video_entity` was created from a live record, and `s3-uiza` indicates it was created by a user uploading a VOD through the Uiza dashboard.

> **`duration`** _number_
>
> The duration of your video entity in seconds. It is measured up to one millionth of a second.

> **`publish_to_cdn`** _string_
>
> The status indicates whether your video entity had been published to Uiza's CDN or not. There are 4 possible statuses:
>
> > **`not-ready`** is returned when Uiza receives no request to publish the video entity yet.
> >
> > **`queue`** is returned when your video entity is in the queue to be published.
> >
> > **`success`** is returned when your video entity has been successfully published and your viewers are able to watch the video.
> >
> > **`failed`** is returned when something goes wrong during the publishing process of your video entity.

> **`playback`** _object_
>
> Contains the playback URL for different streaming protocols including HLS fMP4 \(`hls`\), HLS ts \(`hls_ts`\) and MPEG-dash \(`mpd`\). Use this URL to configure your player to play the video.

> **`created_at`** _string_
>
> The timestamp, at which the `video_entity` is created, follows the [ISO 8601 standard](https://www.w3.org/TR/NOTE-datetime-970915).

> **`updated_at`** _string_
>
> The timestamp, at which the most recent update to the `video_entity` occurred, follows the [ISO 8601 standard](https://www.w3.org/TR/NOTE-datetime-970915).

