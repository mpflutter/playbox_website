---
sidebar_position: 9
---

# battery_plus

battery_plus 是一个可获取当前设备电池状态信息的插件。

PlayBox SDK 已内置该库，你可以直接 import 使用。

## 用法

```dart
// Import package
import 'package:battery_plus/battery_plus.dart';

// Instantiate it
var battery = Battery();

// Access current battery level
print(await battery.batteryLevel);

// Be informed when the state (full, charging, discharging) changes
battery.onBatteryStateChanged.listen((BatteryState state) {
  // Do something with new state
});
```