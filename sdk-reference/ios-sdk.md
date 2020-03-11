---
description: Uiza SDK for iOS
---

# iOS SDK

## UizaSDK

UizaSDK is a framework to connect to Uiza system

## Compatibility

UizaSDK requires Swift 4.0+ and iOS 8+

Installation

#### CocoaPods

To integrate UizaSDK into your Xcode project using [CocoaPods](http://cocoapods.org/), specify it in your `Podfile`:

Then run the following command:

## Usage

### Framework Init

Always initialize the framework by the following line before calling any API functions:

```swift
import UizaSDK

UizaSDK.initWith(appId: YOUR_APP_ID, token: TOKEN, api: YOUR_DOMAIN, version: API_VERSION)
```

YOUR\_APP\_ID and YOUR\_DOMAIN : get from registration email

TOKEN: generate from [https://docs.uiza.io/\#get-api-key](https://docs.uiza.io/#get-api-key)

API\_VERSION: version of target API, set .v3 or .v4 \(default is .v3\)

### Call API

```swift
UZContentServices().loadDetail(entityId: ENTITY_ID, completionBlock: { (videoItem, error) in
  if error != nil {
    print("Error: \(error)")
  }
  else {
    print("Video: \(videoItem)")
  }
})
```

### How to play video

```swift
let playerViewController = UZPlayerViewController()
playerViewController.player.loadVideo(entityId: ENTITY_ID)
present(playerViewController, animated: true, completion: nil)
```

You might have to add these lines to `Info.plist` to disable App Transport Security \(ATS\) to be able to play video:

```swift
<key>NSAppTransportSecurity</key>  
<dict>  
  <key>NSAllowsArbitraryLoads</key><true/>  
</dict>
```

### How to broadcast livestream

```swift
let viewController = UZLiveStreamViewController()
viewController.liveEventId = ENTITY_ID
self.present(viewController, animated: true, completion: nil)
```

Remember to add these usage description keys into `Info.plist` file:

```swift
<key>NSCameraUsageDescription</key>
<string>App needs access to camera for livestream</string>
<key>NSMicrophoneUsageDescription</key>
<string>App needs access to microphone for livestream</string>
```

### Change Player Themes

```swift
let playerViewController = UZPlayerViewController()
playerViewController.player.theme = UZTheme1()
```

UizaPlayer currently has 7 built-in themes:

[UZTheme1](https://github.com/uizaio/uiza-sdk-player-ios/blob/master/themes/theme1.jpg)

[UZTheme2](https://github.com/uizaio/uiza-sdk-player-ios/blob/master/themes/theme2.jpg)

[UZTheme3](https://github.com/uizaio/uiza-sdk-player-ios/blob/master/themes/theme3.jpg)

[UZTheme4](https://github.com/uizaio/uiza-sdk-player-ios/blob/master/themes/theme4.jpg)

[UZTheme5](https://github.com/uizaio/uiza-sdk-player-ios/blob/master/themes/theme5.jpg)

[UZTheme6](https://github.com/uizaio/uiza-sdk-player-ios/blob/master/themes/theme6.jpg)

[UZTheme7](https://github.com/uizaio/uiza-sdk-player-ios/blob/master/themes/theme7.jpg)

### Create CustomTheme

You can create your own custom theme by creating a class inheriting from [UZPlayerTheme Protocol](https://uizaio.github.io/uiza-sdk-player-ios/Protocols/UZPlayerTheme.html) following this template: [UZCustomTheme](https://github.com/uizaio/uiza-sdk-player-ios/blob/master/themes/UZCustomTheme.swift)

You can also create your custom end screen by subclassing `UZEndscreenView`, then set an instance to `player.controlView.endscreenView`

```swift
self.playerViewController.player.controlView.endscreenView = MyCustomEndScreen()
```

### Create Player with Floating Mode

You can create player with "drag down to floating mode" like Facebook or Youtube, by subclassing [UZFloatingPlayerViewController](https://uizaio.github.io/uiza-sdk-player-ios/Classes/UZFloatingPlayerViewController.html), then you can add more UI for displaying video details and add them to `detailsContainerView`

Then present using this code:

```swift
UZFloatingPlayerViewController().present(with: videoItem, playlist: playlist)
```

See [Example](https://github.com/uizaio/uiza-sdk-player-ios/blob/master/Example/UizaSDKExample/FloatingPlayerViewController.swift)

For API details, check [API Document](https://uizaio.github.io/uiza-sdk-player-ios/)

### Google ChromeCast supports

If developing using Xcode 10 and targeting iOS devices running iOS 12 or higher, the "Access WiFi Information" capability is required in order to discover and connect to Cast devices 

![](https://camo.githubusercontent.com/2afb576154d43dfaa77113c9c6ed95a82a4aeea7/68747470733a2f2f646576656c6f706572732e676f6f676c652e636f6d2f636173742f696d616765732f78636f64655f776966695f6361706162696c6974795f6572726f722e706e67)

### Support

[namnh@uiza.io](mailto:namnh@uiza.io) or [developer@uiza.io](mailto:developer@uiza.io)

### License

UizaSDK is released under the BSD license. See [LICENSE](https://github.com/uizaio/uiza-sdk-player-ios/blob/master/LICENSE) for details.

