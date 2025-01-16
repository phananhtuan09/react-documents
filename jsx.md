# JSX

JSX cho phép chúng ta viết các element HTML bằng JavaScript và đặt chúng vào DOM mà không cần bất kỳ phương thức `createElement()` và/hoặc `appendChild()` nào.

JSX chuyển đổi các thẻ HTML thành các React Element

Không bắt buộc phải sử dụng JSX, nhưng JSX giúp viết code React dễ dàng hơn.

Ví dụ về sử dụng JSX:

```jsx
const myElement = <h1>I Love JSX!</h1>;

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(myElement);
```

Ví dụ về không sử dụng JSX:

```jsx
const myElement = React.createElement('h1', {}, 'I do not use JSX!');

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(myElement);
```

### Biểu thức trong JSX

Trong JSX, biểu thức được viết bên trong dấu ngoặc nhọn `{ }`.&#x20;

Biểu thức có thể là biến React, hoặc property, hoặc bất kỳ biểu thức JavaScript hợp lệ nào khác. JSX sẽ thực thi biểu thức và trả về kết quả

### Inserting a Large Block of HTML

Để viết HTML trên nhiều dòng, hãy đặt HTML trong dấu ngoặc đơn:

```jsx
const myElement = (
  <ul>
    <li>Apples</li>
    <li>Bananas</li>
    <li>Cherries</li>
  </ul>
);
```

### One Top Level Element&#x20;

Code HTML phải được wrap trong MỘT phần tử cấp cao nhất. Vì vậy, nếu bạn muốn viết hai đoạn, bạn phải đặt chúng bên trong một phần tử cha, như phần tử div.

Ví dụ:

```jsx
const myElement = (
  <div>
    <p>I am a paragraph.</p>
    <p>I am a paragraph too.</p>
  </div>
);
```

JSX sẽ báo lỗi nếu HTML không chính xác hoặc nếu HTML thiếu phần tử cha.

Ngoài ra, bạn có thể sử dụng "fragment" để wrap nhiều dòng. Điều này sẽ ngăn chặn việc thêm các node không cần thiết vào DOM. Một fragment trông giống như một thẻ HTML trống: `<></>`

Lý do tại sao JSX phải cần phần tử cha để wrap nhiều phần tử con thì khi sử dụng JSX trong React JSX sẽ được chuyển đổi cú pháp(ví dụ babel) thành React Element(tương tự object trong JS) mà trong JavaScript bạn không thể return hai đối tượng mà phải đặt chúng trong một mảng nên cần có thẻ cha để wrap chúng lai với nhau

### Attribute class = className

Thuộc tính class là một thuộc tính được sử dụng  trong HTML, nhưng vì JSX được hiển thị dưới dạng JavaScript và từ khóa class là một từ dành riêng trong JavaScript nên bạn không được phép sử dụng nó trong JSX.

JSX giải quyết vấn đề này bằng cách sử dụng `className` thay thế. Khi JSX được kết xuất, nó sẽ dịch các thuộc tính className thành các thuộc tính class.

### Conditions - if statements

React hỗ trợ các câu lệnh if, nhưng không hỗ trợ bên trong JSX. Để có thể sử dụng câu lệnh điều kiện trong JSX, bạn nên đặt câu lệnh if bên ngoài JSX, hoặc thay vào đó bạn có thể sử dụng biểu thức ba ngôi:&#x20;

Tùy chọn 1: Viết câu lệnh if bên ngoài mã JSX:

```jsx
const x = 5;
let text = "Goodbye";
if (x < 10) {
  text = "Hello";
}

const myElement = <h1>{text}</h1>;
```

Tùy chọn 2: Sử dụng biểu thức ba ngôi thay thế:

```jsx
const x = 5;

const myElement = <h1>{(x) < 10 ? "Hello" : "Goodbye"}</h1>;
```

### camelCase áp dụng cho hầu hết mọi thứ

JSX biến thành JavaScript và các thuộc tính được viết bằng JSX trở thành khóa của các đối tượng JavaScript. Trong các component, bạn thường muốn đọc các thuộc tính đó thành các biến. Nhưng JavaScript có những hạn chế về tên biến. Ví dụ: tên của họ không thể chứa dấu gạch ngang hoặc là những từ dành riêng như `class`. Đây là lý do tại sao trong React, nhiều thuộc tính HTML và SVG được viết bằng CamelCase.&#x20;

Ví dụ: thay vì `stroke-width` bạn dùng `strokeWidth`. Vì `class` là một từ dành riêng nên trong React bạn viết className, được đặt tên theo thuộc tính DOM tương ứng:

> Vì lý do lịch sử, các thuộc tính `aria-*` và `data-*` được viết như trong HTML với dấu gạch ngang.

#### Pro-tip: Use a JSX Converter  <a href="#pro-tip-use-a-jsx-converter" id="pro-tip-use-a-jsx-converter"></a>

Việc chuyển đổi tất cả các thuộc tính này trong markup hiện có có thể rất tẻ nhạt! Chúng tôi khuyên bạn nên sử dụng [trình chuyển đổi](https://transform.tools/html-to-jsx) để dịch HTML và SVG hiện có của mình sang JSX. Các trình chuyển đổi rất hữu ích trong thực tế, nhưng vẫn đáng để hiểu những gì đang diễn ra để bạn có thể thoải mái tự viết JSX.
