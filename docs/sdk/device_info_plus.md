---
sidebar_position: 7
---

# device_info_plus

device_info_plus 是一个设备信息获取插件。

PlayBox SDK 已内置该库，你可以直接 import 使用。

## 用法

```dart
import 'package:playbox_sdk/playbox_sdk.dart';

DeviceInfoPlugin deviceInfo = DeviceInfoPlugin();
AndroidDeviceInfo androidInfo = await deviceInfo.androidInfo;
print('Running on ${androidInfo.model}');  // e.g. "Moto G (4)"

IosDeviceInfo iosInfo = await deviceInfo.iosInfo;
print('Running on ${iosInfo.utsname.machine}');  // e.g. "iPod7,1"

```