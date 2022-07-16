---
sidebar_position: 9
---

# path_provider

path_provider 是一个路径获取库，通过该插件你可以获取设备上可用于读写的文件路径。

PlayBox SDK 已内置该库，你可以直接 import 使用。

## 用法

```dart
import 'package:playbox_sdk/playbox_sdk.dart';

Directory tempDir = await (await PBPathProvider.getInstance()).getTemporaryPath();
String tempPath = tempDir.path;

Directory appDocDir = await (await PBPathProvider.getInstance()).getApplicationDocumentsPath();
String appDocPath = appDocDir.path;
```