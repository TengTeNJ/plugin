
# tt_screen_record_plugin

Screen recording component supports Android and iOS. Android uses the device_screen_recorder plugin
The system capability used by iOS is ReplayKit. Only after iOS14 (including 14) can the screen recording be saved to a custom path, such as a sandbox.
Before iOS14, recorded videos will be saved in the photo album"

A new Flutter plugin for record the screen. This plug-in requires Android SDK 21+ and iOS 10+
## Getting Started
This plugin can be used for record the screen on Android and iOS devices.
### 1 Initialization
final _ttScreenRecordPlugin = TtScreenRecordPlugin();

### 2 For start the recording
bool result = await _ttScreenRecordPlugin.startRecording();

### 3 For stop the recording
Map result = await _ttScreenRecordPlugin.stopRecording();

### 4 Determine whether recording is taking place
bool recording = await _ttScreenRecordPlugin.recording();

### 5 Determine whether the device supports recording (only for iOS, Android returns true by default)
final _result = await _ttScreenRecordPlugin.isAvailable();

## Android

Flutter_Screen_Recorder do not request permissions necessary. You can use [Permission_handler](https://pub.dev/packages/permission_handler), a permissions plugin for Flutter.
Require and add the following permissions in your manifest:

```
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
<uses-permission android:name="android.permission.WRITE_INTERNAL_STORAGE" />
<uses-permission android:name="android.permission.RECORD_AUDIO" />
```

In the last Android version is requiered use a foreground service for record the screen, we added the [flutter foreground plugin](https://pub.dev/packages/flutter_foreground_plugin).

## iOS

You only need add the permission message on the Info.plist

    <key>NSPhotoLibraryUsageDescription</key>
    <string>Save video in gallery</string>
    <key>NSMicrophoneUsageDescription</key>
    <string>Save audio in video</string>

