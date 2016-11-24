# Các tut trước

- [Xây dựng môi trường và Hello World](https://github.com/midnighthack/react-native-tuts/blob/master/tut1/react-native-tut1.md)
- [Cơ bản về Props và State, ví dụ TextInput](https://github.com/midnighthack/react-native-tuts/blob/master/tut2/react-native-tut2.md)

Mẹo: Tutorial này tham khảo trang chủ React Native, click vào các link heading để xem chi tiết hơn.

# [Styles](https://facebook.github.io/react-native/docs/style.html)

- Dùng để xây dựng giao diện cho ứng dụng.
- Có syntax gần tương tự với CSS (nhưng không phải CSS).
- Khai báo biến là camelCase khi chuyển từ CSS sang, ví dụ `backgroundColor` thay vì `background-color`.

```javascript
import React, { Component } from 'react';
import { AppRegistry, StyleSheet, Text, View } from 'react-native';

class LotsOfStyles extends Component {
  render() {
    return (
      <View>
        <Text style={styles.red}>just red</Text>
        <Text style={styles.bigblue}>just bigblue</Text>
        <Text style={[styles.bigblue, styles.red]}>bigblue, then red</Text>
        <Text style={[styles.red, styles.bigblue]}>red, then bigblue</Text>
      </View>
    );
  }
}

const styles = StyleSheet.create({
  bigblue: {
    color: 'blue',
    fontWeight: 'bold',
    fontSize: 30,
  },
  red: {
    color: 'red',
  },
});

AppRegistry.registerComponent('LotsOfStyles', () => LotsOfStyles);
```

- Trong đó:
  + Sử dụng Component `StyleSheet` để define các thông số cho giao diện.
  + Ở các Component muốn hiển thị ta truyền tham số qua props `style`.

# [Height and Width](https://facebook.github.io/react-native/docs/height-and-width.html)

Xác định kích cỡ các thành phần component trên màn hình

## Fixed Dimensions (Cố định)

```javascript
import React, { Component } from 'react';
import { AppRegistry, View } from 'react-native';

class FixedDimensionsBasics extends Component {
  render() {
    return (
      <View>
        <View style={{width: 50, height: 50, backgroundColor: 'powderblue'}} />
        <View style={{width: 100, height: 100, backgroundColor: 'skyblue'}} />
        <View style={{width: 150, height: 150, backgroundColor: 'steelblue'}} />
      </View>
    );
  }
};

AppRegistry.registerComponent('AwesomeProject', () => FixedDimensionsBasics);
```

- Sử dụng với các Component, hoặc các thành phần cần cố định.
- Kích thước sẽ được cố định theo số pixels nên sẽ có khác biệt giữa các loại máy có kích cỡ màn hình khác nhau.

## Flex Dimensions (Linh hoạt theo tỉ lệ)

- Sử dụng khai báo `flex` sẽ làm kích cỡ co giãn tương ứng theo tỉ lệ kích cỡ màn hình.
- `flex: 1` thường sử dụng do sẽ fill toàn bộ kích cỡ screen, dùng ở `View` cao nhất. Ví dụ:

```javascript
import React, { Component } from 'react';
import { AppRegistry, View } from 'react-native';

class FlexDimensionsBasics extends Component {
  render() {
    return (
      // Try removing the `flex: 1` on the parent View.
      // The parent will not have dimensions, so the children can't expand.
      // What if you add `height: 300` instead of `flex: 1`?
      <View style={{flex: 1}}>
        <View style={{flex: 1, backgroundColor: 'powderblue'}} />
        <View style={{flex: 2, backgroundColor: 'skyblue'}} />
        <View style={{flex: 3, backgroundColor: 'steelblue'}} />
      </View>
    );
  }
};

AppRegistry.registerComponent('AwesomeProject', () => FlexDimensionsBasics);
```

- Trong đó:
  + `<View style={{flex: 1}}>` sẽ fill toàn bộ khoảng trống trên màn hình và co giãn theo tỉ lệ.
  + Các Component `View` bên trong sẽ bắt đầu chia nhỏ hơn nữa các phần sử dụng.
  + Tổng số `flex` ở `View` đó sẽ là tổng số phần màn hình muốn chia, ở đây là 6.

- Mẹo: Hãy nghĩ tổng phần muốn chia trước rồi xác định `flex` sau. Giả sử:
  + Bạn muốn chia làm 12 phần, phần đầu bạn muốn lấy 1/2 màn, vậy đơn giản set `flex: 6`.
  + Đối với các phần lẻ như 13, bạn chia 3 nhưng bị lẻ thì set `flex: 13/3`, tỉ lệ sẽ vẫn chuẩn xác.
  ```javascript
  <View style={{flex: 1}}>
    <View style={{flex: 13/3, backgroundColor: 'powderblue'}} />
    <View style={{flex: 13/3, backgroundColor: 'skyblue'}} />
    <View style={{flex: 13/7, backgroundColor: 'steelblue'}} />
  </View>
  ```

Flex giúp hiển thị linh hoạt với tất cả các loại màn hình, điều khá khó khăn khi native app.

# [Layout with Flexbox](https://facebook.github.io/react-native/docs/flexbox.html)

- Click vào link trên heading để có hình dung rõ ràng với các example cụ thể.
- Giúp điều hướng các Component theo các vị trí màn hình mong muốn.
- Tham khảo thêm tài liệu [Layout Props](https://facebook.github.io/react-native/docs/layout-props.html) với các props hữu ích.

---

[*] [Một số UI Framework hỗ trợ làm giao diện](https://github.com/petehouston/react-ui-framework)

## Good luck & Have fun
