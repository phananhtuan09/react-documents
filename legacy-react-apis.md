# Legacy React APIs

```jsx
createElement(type, props, ...children)
```

#### Tham số:

* `type`: Đối số type phải là React  component type hợp lệ. Ví dụ, nó có thể là tag html(như 'div' hoặc 'span') hoặc  React component(hàm, lớp hoặc thành phần đặc biệt như `Fragment`).
* `props`: Đối số props phải là một object hoặc null. Nếu bạn truyền null, nó sẽ được coi như một object rỗng.React sẽ tạo ra một element có props khớp với props bạn đã truyền vào. Lưu ý rằng `ref` và `key` từ đối tượng props của bạn là đặc biệt và sẽ không có sẵn dưới dạng `element.props.ref` và `element.props.key` trên phần tử được trả về. Chúng sẽ có sẵn dưới dạng `element.ref` và `element.key`&#x20;
* &#x20;.`..children`(không bắt buộc): Không có hoặc nhiều node con. Chúng có thể là bất kỳ node React nào, bao gồm các  React element, chuỗi, số, cổng, nút trống `null`, `undefined`, `true`, and `false` ) và mảng các node React.

#### Giá trị trả về:

`createElement` trả về một đối tượng  React element có một số thuộc tính:

* `type`: Giá trị `type` truyền vào.
* `props`: Giá trị `props` truyền vào ngoại trừ `ref` và `key`.
* `ref`: Giá trị `ref` truyền vào. Nếu không truyền thì là  `null`.
* `key`: Giá trị `key` truyền vào, bị ép kiểu thành một chuỗi.Nếu không truyền thì là `null`.

#### Lưu ý:&#x20;

* Khi sử dụng JSX, bạn phải bắt đầu tag bằng chữ in hoa để hiển thị custom component của riêng bạn. Nói cách khác,  `<Something/>` tương đương với `createElement(Something)`, nhưng `<something/>` (chữ thường) tương đương với `createElement('something')` (lưu ý là một chuỗi nên sẽ được coi là HTML ).
  * Chính vì thế khi sử dụng custom component phải viết hoa chữ cái đầu để React nhận diện bạn đang dùng custom component.
*   Bạn chỉ nên truyền các đối số children dưới dạng nhiều đối số cho `createElement` nếu tất cả chúng đều được biết đến ở dạng tĩnh(không thay đổi), như `createElement('h1', {}, child1, child2, child3)`. Nếu child bạn là dynamic, hãy chuyển toàn bộ mảng làm đối số thứ ba: `createElement('ul', {}, listItems)`. Điều này đảm bảo rằng React sẽ cảnh báo bạn về việc thiếu `key` cho bất kỳ danh sách động nào. Đối với danh sách tĩnh, điều này không cần thiết vì chúng không bao giờ update lại.



#### Ví dụ:

```jsx
import { createElement } from 'react';

function Greeting({ name }) {
  return createElement(
    'h1',
    { className: 'greeting' },
    'Hello ',
    createElement('i', null, name),
    '. Welcome!'
  );
}
// output: <h1 class="greeting">Hello <i>Taylor</i>. Welcome!</h1>
```

#### Tại sao React component phải viết hoa chữ cái đầu?

Khi sử dụng React component ta phải viết in hoa như thế này: `<Header/>`. Khi ta sử dụng JSX để tạo React component thì React cần chuyển đổi đoạn JSX thành React component như sau:

```jsx
// Input
const element = <h1>Hello World</h1>
// Output
var element = React.createElement("h1", null, "Hello World");
```

Và bởi vì tham số type của phương thức createElement có thể là tag html hoặc React Component. Khi ta truyền type bắt đầu là chữ in hoa thì React sẽ coi nó là React Component ngược lai React coi nó là tag html. Nên khi ta gọi component mà không bắt đầu bằng in hoa thì React coi đó là render tag html nên sẽ lỗi(vì tag đó không hợp lệ)
