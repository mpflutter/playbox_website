---
sidebar_position: 12
---

# mp_file

mp_file 是 MPFlutter 专用的 File IO 库，因为 MPFlutter 不能直接使用 `dart:io` 库，故编写该兼容库供开发者使用。

## 用法

mp_file 的用法与 `dart:io` File API 保持一致，但需要注意，所有 sync 同步读写方法都不支持。

```dart
import 'package:mp_file/mp_file.dart';

final fooFile = File('${baseDir.path}/foo.txt');
fooFile.writeAsString('Hello, World!');

```