# Các tut trước

- [Xây dựng môi trường và Hello World](https://github.com/midnighthack/react-native-tuts/blob/master/tut1/react-native-tut1.md)

Mẹo: Tutorial này tham khảo trang chủ React Native, click vào các link heading để xem chi tiết hơn.

# [Props](https://facebook.github.io/react-native/docs/props.html)

- Đóng vai trò là một attribute của Component.
- Dùng để truyền tải một **Object** hoặc **Function** cho giữa các Component với nhau.
- Hữu ích trong việc liên lạc giữa các Component với nhau theo mối quan hệ cha con (parent-children).

## 1. Props trong Component của React Native

- Các Component có thể được customize với các tham số khác nhau, gọi là `props`.
- Trong project **HelloWorld**, sửa nội dung bên trong file `index.ios.js` hoặc `index.android.js` và chạy thử.

```javascript
import React, { Component } from 'react';
import { AppRegistry, Image } from 'react-native';

class Bananas extends Component {
  render() {
    let pic = {
      uri: 'https://upload.wikimedia.org/wikipedia/commons/d/de/Bananavarieties.jpg'
    };
    return (
      <Image source={pic} style={{width: 193, height: 110}}/>
    );
  }
}

AppRegistry.registerComponent('Bananas', () => Bananas);
```

- Trong đó:
  + Component `Image` sử dụng props là `source` và `style`.
  + prop `source` được truyền biến `pic` để hiển thị ảnh.

- Lưu ý:
  + Việc implement hiển thị được Component `Image` trong React xử lý.
  + Các thư viện thường cung cấp sẵn các Component tương tự `Image` của React Native với cách sử dụng tương tự.

## 2. Tự viết Component sử dụng Props

Trong project **HelloWorld**, sửa nội dung bên trong file `index.ios.js` hoặc `index.android.js` và chạy thử.

```javascript
import React, { Component } from 'react';
import { AppRegistry, Text, View } from 'react-native';

class Greeting extends Component {
  render() {
    return (
      <Text>Hello {this.props.name}!</Text>
    );
  }
}

class LotsOfGreetings extends Component {
  render() {
    return (
      <View style={{alignItems: 'center'}}>
        <Greeting name='Rexxar' />
        <Greeting name='Jaina' />
        <Greeting name='Valeera' />
      </View>
    );
  }
}

AppRegistry.registerComponent('LotsOfGreetings', () => LotsOfGreetings);
```

- Trong đó:
  + `LotsOfGreetings` là Parent Component và gọi đến Child Component là `Greeting`.
  + Component `Greeting` dùng prop `name` để truyền các giá trị khác nhau.
  + Bên trong `Greeting` các giá trị props sẽ nằm trong `this.props` và ta chỉ việc lấy ra để sử dụng.

## 3. Kết luận

- Props giúp xử lý tốt việc giao tiếp giữa các Component theo tinh thần [Thinking in React](https://facebook.github.io/react/docs/thinking-in-react.html).
- Có thể dễ thấy việc này giúp cho việc tái sử dụng các Component rất mạnh mẽ.

# [State](https://facebook.github.io/react-native/docs/state.html)

- Để control một Component ngoài việc sử dụng `props`, ta còn có thể sử dụng `state`.
- `props` được truyền và thường sẽ fixed giá trị, còn những dữ liệu có thể thay đổi, ta dùng `state`.

```javascript
import React, { Component } from 'react';
import { AppRegistry, Text, View } from 'react-native';

class Blink extends Component {
  constructor(props) {
    super(props);
    this.state = {showText: true};

    // Toggle the state every second
    setInterval(() => {
      this.setState({ showText: !this.state.showText });
    }, 1000);
  }

  render() {
    let display = this.state.showText ? this.props.text : ' ';
    return (
      <Text>{display}</Text>
    );
  }
}

class BlinkApp extends Component {
  render() {
    return (
      <View>
        <Blink text='I love to blink' />
        <Blink text='Yes blinking is so great' />
        <Blink text='Why did they ever take this out of HTML' />
        <Blink text='Look at me look at me look at me' />
      </View>
    );
  }
}

AppRegistry.registerComponent('BlinkApp', () => BlinkApp);
```

- Trong đó:
  + Nên khởi tạo các state trong contructor, ở đây là `showText`.
  + Khi có sự thay đổi mà dùng đến `state`, sử dụng `setState()` để thiết lập giá trị mới.
  + Mỗi khi `state` thay đổi, Component sẽ được render lại để hiển thị nội dung mới tương ứng.

- Lưu ý:
  + `state` chỉ tồn tại trong Component đó, như là một biến private.
  + Nếu muốn truyền giá trị cho Component khác thì truyền `state` thông qua `props`.

## Kết luận

- `state` thích hợp lưu các giá trị trả về sau một thời gian làm thay đổi dữ liệu như API.

# Sự khác nhau giữa `props` và `state`

Đặc điểm | `props` | `state` |
-------- | ------- | ------- |
Can get initial value from parent Component? | Yes | Yes
Can be changed by parent Component? | Yes | No
Can set default values inside Component?* | Yes | Yes
Can change inside Component? | No | Yes
Can set initial value for child Components? | Yes | Yes
Can change in child Components? | Yes | No

## Good luck & Have fun
