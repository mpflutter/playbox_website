---
sidebar_position: 8
---

# sensors_plus

sensors_plus 是一个可用于获取设备加速度、三向陀螺仪信息的插件。

PlayBox SDK 已内置该库，你可以直接 import 使用。

## 用法

```dart
import 'package:sensors_plus/sensors_plus.dart';

accelerometerEvents.listen((AccelerometerEvent event) {
  print(event);
});
// [AccelerometerEvent (x: 0.0, y: 9.8, z: 0.0)]

userAccelerometerEvents.listen((UserAccelerometerEvent event) {
  print(event);
});
// [UserAccelerometerEvent (x: 0.0, y: 0.0, z: 0.0)]

gyroscopeEvents.listen((GyroscopeEvent event) {
  print(event);
});
// [GyroscopeEvent (x: 0.0, y: 0.0, z: 0.0)]

magnetometerEvents.listen((MagnetometerEvent event) {
  print(event);
});
// [MagnetometerEvent (x: -23.6, y: 6.2, z: -34.9)]
```