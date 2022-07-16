---
sidebar_position: 11
---

# file_picker

file_picker 是一个文件选择器插件，你可以使用该插件从设备的 iCloud 或相册胶卷中获取文件。

PlayBox SDK 已内置该库，你可以直接 import 使用。

## 用法

单个文件获取可

```dart
FilePickerResult? result = await FilePicker.platform.pickFiles();

if (result != null) {
  File file = File(result.files.single.path);
} else {
  // User canceled the picker
}
```

更多用法可参考 README 

https://pub.dev/packages/file_picker