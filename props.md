# Props

### React Props

React Props giống như các đối số hàm trong JavaScript và các thuộc tính trong HTML. Để gửi props vào một component, hãy sử dụng cú pháp giống như các thuộc tính HTML:

```jsx
const myElement = <Car brand="Ford" />;
```

### Pass Data

Props cũng là cách bạn truyền dữ liệu từ component này sang component khác dưới dạng tham số.

```jsx
function Car(props) {
  return <h2>I am a { props.brand }!</h2>;
}

function Garage() {
  return (
    <>
      <h1>Who lives in my garage?</h1>
      <Car brand="Ford" />
    </>
  );
}
```

> Lưu ý: React Props là readonly! Bạn sẽ nhận được lỗi nếu bạn cố gắng thay đổi giá trị của chúng.
>
> React coi props là "[immutable](https://en.wikipedia.org/wiki/Immutable_object)" để tránh các lỗi xảy ra do dữ liệu bị "mutable" không kiểm soát và bởi vì React không thể biết được khi nào cần re-render component nếu bạn thay đổi giá trị của props nên cách đúng đắn để update props là sử dụng `useState`

### Sử dụng Props trong React Element

* Sử dụng props giống như attribute của thẻ html
* 2 props class, for  ⇒ className, htmlFor
* Phải tuân theo quy ước có sẵn

Ví dụ:

```jsx
<div className"title">Heading</div>
```

### Sử dụng Props trong React Component

* Sử dụng props như đối số component
* Tư do đặt tên props
  * Đặt tên theo camelCase
  * Có thể bao gồm dấu gạch ngang(không khuyến nghị)

### Chú ý khi sử dụng Props

* Props `key` là props đặc biệt
* Props cơ bản là đối số của Component
* Props có thể là bất kì kiểu dữ liệu nào
* Sử dụng destructuring để code ngắn gọn hơn
