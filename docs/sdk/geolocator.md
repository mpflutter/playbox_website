---
sidebar_position: 10
---

# geolocator

geolocator 是一个地理位置获取插件。

PlayBox SDK 已内置该库，你可以直接 import 使用。

## 简单用法

```dart
import 'package:playbox_sdk/playbox_sdk.dart';

/// Determine the current position of the device.
///
/// When the location services are not enabled or permissions
/// are denied the `Future` will return an error.
Future<Position> _determinePosition() async {
  bool serviceEnabled;
  LocationPermission permission;

  final GeoLocator = await PBGeolocator.getInstance();

  // Test if location services are enabled.
  serviceEnabled = await Geolocator.isLocationServiceEnabled();
  if (!serviceEnabled) {
    // Location services are not enabled don't continue
    // accessing the position and request users of the 
    // App to enable the location services.
    return Future.error('Location services are disabled.');
  }

  permission = await Geolocator.checkPermission();
  if (permission == LocationPermission.denied) {
    permission = await Geolocator.requestPermission();
    if (permission == LocationPermission.denied) {
      // Permissions are denied, next time you could try
      // requesting permissions again (this is also where
      // Android's shouldShowRequestPermissionRationale 
      // returned true. According to Android guidelines
      // your App should show an explanatory UI now.
      return Future.error('Location permissions are denied');
    }
  }
  
  if (permission == LocationPermission.deniedForever) {
    // Permissions are denied forever, handle appropriately. 
    return Future.error(
      'Location permissions are permanently denied, we cannot request permissions.');
  } 

  // When we reach here, permissions are granted and we can
  // continue accessing the position of the device.
  return await Geolocator.getCurrentPosition();
}

```

## 更多用法

你可以通过阅读 README 了解。

https://pub.dev/packages/geolocator

请注意 Geolocator 实例的获取必须通过以下方法。

```dart
import 'package:playbox_sdk/playbox_sdk.dart';

final GeoLocator = await PBGeolocator.getInstance();
```