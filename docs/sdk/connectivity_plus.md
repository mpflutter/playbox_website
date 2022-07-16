---
sidebar_position: 5
---

# connectivity_plus

connectivity_plus 是一个网络连接监测库，可用于监测网络当前是否可用以及当前网络类型。

PlayBox SDK 已内置该库，你可以直接 import 使用。

## 用法

```dart
import 'package:connectivity_plus/connectivity_plus.dart';

var connectivityResult = await (Connectivity().checkConnectivity());
if (connectivityResult == ConnectivityResult.mobile) {
  // I am connected to a mobile network.
} else if (connectivityResult == ConnectivityResult.wifi) {
  // I am connected to a wifi network.
}
```

监听网络可用状态。

```dart
import 'package:connectivity_plus/connectivity_plus.dart';

@override
initState() {
  super.initState();

  subscription = Connectivity().onConnectivityChanged.listen((ConnectivityResult result) {
    // Got a new connectivity status!
  })
}

// Be sure to cancel subscription after you are done
@override
dispose() {
  super.dispose();

  subscription.cancel();
}
```
