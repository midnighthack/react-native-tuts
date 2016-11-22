
# Cài đặt môi trường

### [Chọn Mobile OS và OS hiện tại đang dùng và làm theo hướng dẫn.](https://facebook.github.io/react-native/docs/getting-started.html)

## Lưu ý
### Vấn đề chung
* **NodeJS v7.1** đang gặp vấn đề với React Native và nhiều module khác (webpack, react...), bạn nên sử dụng version 6.9.x
* Các bạn sử dụng Mac, Linux có thể sử dụng **nvm** để quản lý phiên bản **NodeJS** dễ dàng hơn, với windows thì sài **nvm-windows**
  * [nvm](https://github.com/creationix/nvm)
  * [nvm-window](https://github.com/coreybutler/nvm-windows)
* Bạn nên cài **yarn** để cài các module cho **React-Native** (react-native-cli version 1.2 đang sử dụng **yarn** để cài đặt packages)
```sh
  npm install -g yarn
```

### iOS
* Phải sử dụng máy Mac ( máy chạy hackintosh cũng được, nếu gặp vấn đề thì bạn tự giải quyết)
* Gói **homebrew** để cài **NodeJS, Watchman** có thể xảy ra vấn đề, các bạn có thể sử dụng lệnh `brew doctor` để chuẩn đoán lỗi xảy ra khi cài đặt gói nhé!
### Android
* Trên Windows, nếu việc sử dụng **Choco** không được tiện dụng bạn có thể tải và cài đặt trực tiếp **NodeJS và Python** từ trên trang chủ:
  * [NodeJS](https://nodejs.org/en/download/)
  * [Python](https://www.python.org/downloads/) (chọn version 2.x.x)
* Trong hướng dẫn có một bước quan trọng là thiết lập biến môi trường **ANDROID_HOME**, nếu quên bạn sẽ không chạy được máy ảo, đây là bước mọi người rất dễ bỏ sót.

# Xây dựng ứng dụng Hello World

Sau khi làm theo các hướng dẫn trên, hãy mở **Terminal** (macos, linux) hoặc **Command** (windows)

```sh
react-native init HelloWorld
cd HelloWorld
```

Với iOS (chỉ dành cho macOS or hackintosh)

```sh
react-native run-ios
```

Với Android

```sh
react-native run-android
```

### Lưu ý
Với Android, bạn phải edit `host` và `port` của app

* Với device, hãy lắc lắc máy cho tới khi xuất hiện một Menu -> chọn `Dev Setting` -> `Debug server host & port for device` -> nhập theo format `{ip}:{port}`.
* Với máy ảo, run `adb shell input keyevent 82`

## Good luck & Have fun
