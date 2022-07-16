---
sidebar_position: 2
---

# dio

dio 是一个 HTTP 网络库，PlayBox SDK 已内置，可直接使用。

关于 dio 的使用方法，可以参考[dio 官方文档](https://github.com/flutterchina/dio/blob/master/README-ZH.md)。

我们在这里摘录了一部分用法。

## 一个极简的示例

```dart 
import 'package:dio/dio.dart';
void getHttp() async {
  try {
    var response = await Dio().get('http://www.google.com');
    print(response);
  } catch (e) {
    print(e);
  }
}
```

## 示例

发起一个 `GET` 请求 :

```dart
Response response;
var dio = Dio();
response = await dio.get('/test?id=12&name=wendu');
print(response.data.toString());
// Optionally the request above could also be done as
response = await dio.get('/test', queryParameters: {'id': 12, 'name': 'wendu'});
print(response.data.toString());
```

发起一个 `POST` 请求:

```dart
response = await dio.post('/test', data: {'id': 12, 'name': 'wendu'});
```

发起多个并发请求:

```dart
response = await Future.wait([dio.post('/info'), dio.get('/token')]);
```

下载文件:

```dart
response = await dio.download('https://www.google.com/', './xx.html');
```

以流的方式接收响应数据：

```dart
Response<ResponseBody> rs;
rs = await Dio().get<ResponseBody>(url,
  options: Options(responseType: ResponseType.stream),  //设置接收类型为stream
);
print(rs.data.stream); //响应流
```

以二进制数组的方式接收响应数据：

```dart
Response<List<int>> rs 
rs = await Dio().get<List<int>>(url,
 options: Options(responseType: ResponseType.bytes), //设置接收类型为二进制数组
);
print(rs.data); // 二进制数组
```

发送 FormData:

```dart
var formData = FormData.fromMap({
  'name': 'wendux',
  'age': 25,
});
var response = await dio.post('/info', data: formData);
```

通过FormData上传多个文件:

```dart
var formData = FormData.fromMap({
  'name': 'wendux',
  'age': 25,
  'file': await MultipartFile.fromFile('./text.txt', filename: 'upload.txt'),
  'files': [
    await MultipartFile.fromFile('./text1.txt', filename: 'text1.txt'),
    await MultipartFile.fromFile('./text2.txt', filename: 'text2.txt'),
  ]
});
var response = await dio.post('/info', data: formData);
```

监听发送(上传)数据进度:

```dart
response = await dio.post(
  'http://www.dtworkroom.com/doris/1/2.0.0/test',
  data: {'aa': 'bb' * 22},
  onSendProgress: (int sent, int total) {
    print('$sent $total');
  },
);
```

以流的形式提交二进制数据：

```dart

List<int> postData = <int>[...];
await dio.post(
  url,
  data: Stream.fromIterable(postData.map((e) => [e])), //创建一个Stream<List<int>>
  options: Options(
    headers: {
      Headers.contentLengthHeader: postData.length, // 设置content-length
    },
  ),
);

// 二进制数据
List<int> postData = <int>[...];

await dio.post(
  url,
  data: Stream.fromIterable(postData.map((e) => [e])), //创建一个Stream<List<int>>
  options: Options(
    headers: {
      Headers.contentLengthHeader: postData.length, // 设置content-length
    },
  ),
);
```

注意：如果要监听提交进度，则必须设置content-length，否则是可选的。