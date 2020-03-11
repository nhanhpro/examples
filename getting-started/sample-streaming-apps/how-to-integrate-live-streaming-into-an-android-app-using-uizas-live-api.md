# How to integrate live streaming into an Android App using Uiza’s Live API

## Introduction

Uiza provides intuitive APIs, which simplifies the integration of live streaming functionality into your platform. This guide is a step-by-step tutorial on how to build your live streaming Android app with Uiza’s APIs. The full sample code can be downloaded at the end of the tutorial.

### Integrating live streaming into android application

For this tutorial, we build two separate apps: The streaming app, where a video is captured over the phone's camera and streamed; the viewer app, where all the live entities are listed and can be watched on mobile. Step 1 to Step 4 is for the Streaming App, and Step 5 to Step 7 is for the Viewer app.

### Uiza Terminologies

Throughout the tutorial we will be mentioning live entities, streamers and viewers.

`live entities` are basically live events, with or without a live feed. A live entity contains the information required for Uiza to allocate resources to power the live event, and direct your live feed toward these resources for ingestion and streaming.

`Streamer`: Streamers record the live events and are the source of the live signals that Uiza receives.

`Viewer`: Viewers are the users who watch the live stream on their devices. They are the destination of the delivery of the live stream.

## Prerequisite

* Android Studio 3.3 or above
* Min API 19 \(Android KitKat\)
* Real devices \(Nexus 5X or other devices\)

### Uiza Account

We need an API key to access Uiza’s services. To get your API key follow these steps: 1. create an account at Uiza here: [Sign Up Link](https://id.uiza.io/register). 2. In the developer console, go to your application 3. Save the API Key 4. Update API key at `samplelive/src/main/java/io/uiza/samplelive/SampleLiveApplication.java`

```java
private static final String API_TOKEN = <<API Key>>; // dynamic
```

## Step 1 - Streaming app - Dependencies and Permissions

We start with setting the permissions in the manifest file.

### Permissions

```java
    <uses-permission android:name="android.permission.INTERNET" />
    <uses-permission android:name="android.permission.RECORD_AUDIO" />
    <uses-permission android:name="android.permission.CAMERA" /> <!-- needed by background Rtp service to keep service alive -->
    <uses-permission android:name="android.permission.FOREGROUND_SERVICE" /> <!-- Optional for play store -->
    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" /> <!-- for record -->
```

### Dependencies

Add the `Jitpack` repository to your `build.gradle` file

```java
allprojects {
      repositories {
         maven { url 'https://jitpack.io' }
      }
}
```

Add the Uiza live streaming and playback SDK as follow:

```java
defaultConfig {  
    multiDexEnabled  true
}  
dependencies {  
    // for playing VOD, LIVE video  
    implementation 'com.github.uizaio.uiza-android-sdk-player:uizacoresdk:[latest-release-number]'        

    // for broadcasting / live streaming
    implementation 'com.github.uizaio.uiza-android-sdk-player:uizalivestream:[latest-release-number]'  
}
```

You can get the latest release number [HERE](https://github.com/uizaio/uiza-android-sdk-player/releases)

If you are using uiza\_android\_sdk\_player \(version 4.0.9 and above\), you will need to import following dependencies:

```java
// for playing VOD, LIVE video
implementation 'com.github.uizaio.uiza-android-sdk-player:uizacoresdk:4.0.9'
implementation 'com.google.android.exoplayer:exoplayer:2.10.8'
implementation 'com.google.android.exoplayer:exoplayer-dash:2.10.8'
implementation 'com.google.android.exoplayer:exoplayer-ui:2.10.8'
```

## Step 2 - Creating a live entity

We pass on the parameters to `createEntity`.

```java
        CreateLiveBody body = new CreateLiveBody(
                "<streamName>",
                "<Description>",
                "<region>"
        );
        UizaLiveService liveService = UizaClientFactory.getLiveService();
        RxBinder.bind(
                liveService.createEntity(body),
                liveEntity -> {
                    // onSuceess
                }, throwable -> {
                    // onError
                    Timber.e(throwable);
                }, () -> {
                    // onComple
                }
        )
```

This step returns us a live entity ID; the ID is used for the following step.

## Step 3 - Getting the live entity info

We will use the live entity ID to retrieve the key & URL.

```java
RxBinder.bind(UizaClientFactory.getLiveService().getEntity("<entityId>"), liveEntity -> {
        // onSuccess
    }, throwable -> {
        //onError
    }, () -> {
        // onComplete
    });
```

## Step 4 - Making a live stream

We capture the live stream using the Android camera In layout xml

```markup
    <io.uiza.live.UizaLiveView
        android:id="@+id/uiza_live_view"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        app:audioBitrate="64"
        app:audioSampleRate="32000"
        app:audioStereo="true"
        app:fps="24"
        app:frame_interval="2"
        app:videoSize="p720"
        app:useCamera2="true"
        app:AAEnabled="false"
        app:isFlipHorizontal="false"
        app:isFlipVertical="false"
        app:keepAspectRatio="true"
        app:numFilters="1"/>
```

In java code:

```java
    UizaLiveView liveView = findViewById(R.id.uiza_live_view);
```

To Start: We pass the URL and Key from the API call to `startStream`

```java
    if (liveView.isRecording() || liveView.prepareStream()) {
        liveView.startStream(liveStreamUrl);
    }
```

To Stop

```java
    liveView.stopStream();
```

To Switch Camera

```text
    try {
        liveView.switchCamera();
    } catch (UizaCameraOpenException e) {
        // error
    }
```

## Step 5 - Viewer app - listing he entities

### Viewer App - list out all entities

The viewer app will display all active live streams for the viewer.

```java
RxBinder.bind(
    UizaClientFactory.getLiveService()
        .getEntities()
        .map(ListWrap::getData),
    entities -> {
        //onSuccess
    }, throwable -> {
        // onError
    }
);
```

Currently a dummy thumbnail is in use. When the thumbnail API is added, this part of the code will be updated to include the thumbnail.

## Step 6 - playback a live stream

### Viewer App - playback feature

Using the Uiza player, we will playback the stream

In layout xml we set the video dimensions.

In Java code:

```java
    UZUtil.setCasty(activity);
    UZVideo uzVideo = findViewById(R.id.uiza_video);
    uzVideo.setResizeMode(AspectRatioFrameLayout.RESIZE_MODE_FIXED_HEIGHT);
    UZUtil.initLiveEntity(this, uzVideo, liveEntity.getPlaybackInfo());
            uzVideo.setFreeSize(true);
```

## Step 7 - adding chat functionality

To create a communication channel between viewer and streamer, we enable chat. We will use Google's Firebase for this sample code, as it is very well supported and intuitive.

### Google Firebase integration

```text
// authenticate to firebase
implementation 'com.google.firebase:firebase-auth:19.2.0'
implementation 'com.google.android.gms:play-services-auth:17.0.0'
// database to storage message
implementation 'com.google.firebase:firebase-database:19.2.0'
```

To detail: [https://firebase.google.com/docs/android/setup](https://firebase.google.com/docs/android/setup)

Following code shows the chat integration into our sample app.

```java
    private void setupChatConnection() {
        if (liveEntity != null) {
            FirebaseDatabase database = FirebaseDatabase.getInstance();
            DatabaseReference reference = database.getReference(liveEntity.getId());

            reference.addValueEventListener(new ValueEventListener() {
                @Override
                public void onDataChange(@NonNull DataSnapshot dataSnapshot) {
                    Timber.d("SUCCESS!");
                    handleReturn(dataSnapshot);
                }

                @Override
                public void onCancelled(@NonNull DatabaseError databaseError) {
                    Timber.e("ERROR: %s", databaseError.getDetails());
                }
            });
        }
    }
```

## Conclusion

Our API provides simple and intuitive integration into any Android app. You can focus on your application and let Uiza do the hard work. The source code to this tutorial can be found here: [Github](https://github.com/uizaio/uiza-android-sdk-player/tree/v5)

