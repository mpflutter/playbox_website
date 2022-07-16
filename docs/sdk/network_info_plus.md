---
sidebar_position: 4
---

# network_info_plus

network_info_plus 是一个网络信息插件库，开发者可以通过该库获取设备的 IP、网关、WIFI 等信息。

PlayBox SDK 已内置该库，你可以直接 import 使用。


```dart
import 'package:network_info_plus/network_info_plus.dart';

final info = NetworkInfo();

var wifiName = await info.getWifiName(); // FooNetwork
var wifiBSSID = await info.getWifiBSSID(); // 11:22:33:44:55:66
var wifiIP = await info.getWifiIP(); // 192.168.1.43
var wifiIPv6 = await info.getWifiIPv6(); // 2001:0db8:85a3:0000:0000:8a2e:0370:7334
var wifiSubmask = await info.getWifiSubmask(); // 255.255.255.0
var wifiBroadcast = await info.getWifiBroadcast(); // 192.168.1.255
var wifiGateway = await info.getWifiGatewayIP(); // 192.168.1.1
```