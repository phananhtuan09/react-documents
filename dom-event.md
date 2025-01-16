# DOM Event

```jsx
function Button({ onClick, children }) {
  return (
    <button onClick={onClick}>
      {children}
    </button>
  );
}

function PlayButton({ movieName }) {
  function handlePlayClick() {
    alert(`Playing ${movieName}!`);
  }

  return (
    <Button onClick={handlePlayClick}>
      Play "{movieName}"
    </Button>
  );
}

function UploadButton() {
  return (
    <Button onClick={() => alert('Uploading!')}>
      Upload Image
    </Button>
  );
}

export default function Toolbar() {
  return (
    <div>
      <PlayButton movieName="Kiki's Delivery Service" />
      <UploadButton />
    </div>
  );
}
```

Dưới đây, component `Toolbar` hiển thị một `PlayButton` và một `UploadButton`:

* `PlayButton` truyền `handlePlayClick` làm prop `onClick` cho component `Button` bên trong.
* `UploadButton` truyền `() => alert('Uploading!')` làm prop `onClick` cho component `Button` bên trong.

Cuối cùng, component `Button` của bạn nhận một prop gọi là `onClick`. Component này truyền trực tiếp prop đó cho thẻ `<button>` tích hợp sẵn của trình duyệt bằng `onClick={onClick}`. Điều này yêu cầu React gọi hàm được truyền vào khi có sự kiện nhấp chuột.

### Event propagation <a href="#event-propagation" id="event-propagation"></a>

Event handlers cũng sẽ bắt các sự kiện từ bất kỳ component con nào mà component của bạn có thể có. Chúng ta nói rằng một sự kiện "bubbles" hoặc "propagates" lên tree: nó bắt đầu từ nơi sự kiện xảy ra, sau đó đi lên tree.

```jsx
export default function Toolbar() {
  return (
    <div className="Toolbar" onClick={() => {
      alert('You clicked on the toolbar!');
    }}>
      <button onClick={() => alert('Playing!')}>
        Play Movie
      </button>
      <button onClick={() => alert('Uploading!')}>
        Upload Image
      </button>
    </div>
  );
}
```

Nếu bạn nhấp vào bất kỳ button nào, onClick của button đó sẽ chạy trước, tiếp theo là onClick của parent. Vì vậy, hai thông báo sẽ xuất hiện. Nếu bạn nhấp vào chính toolbar, chỉ có onClick của parent sẽ chạy.

> Tất cả các event đều lan truyền trong React ngoại trừ `onScroll`, chỉ hoạt động trên thẻ JSX mà bạn gắn vào

### Stopping Propagation

Đối tượng event cho phép bạn dừng sự "lan truyền". Nếu bạn muốn ngăn chặn sự kiện đến các thành phần cha, bạn cần gọi `e.stopPropagation()` như thành phần Button này thực hiện:

```jsx
function Button({ onClick, children }) {
  return (
    <button onClick={e => {
      e.stopPropagation();
      onClick();
    }}>
      {children}
    </button>
  );
}

export default function Toolbar() {
  return (
    <div className="Toolbar" onClick={() => {
      alert('You clicked on the toolbar!');
    }}>
      <Button onClick={() => alert('Playing!')}>
        Play Movie
      </Button>
      <Button onClick={() => alert('Uploading!')}>
        Upload Image
      </Button>
    </div>
  );
}
```

### Preventing default behavior

Một số sự kiện trình duyệt có hành vi mặc định liên quan đến chúng. Ví dụ, sự kiện

`submit`, xảy ra khi một nút bên trong nó được nhấp vào, sẽ tải lại toàn bộ trang theo mặc định:

Bạn có thể gọi `e.preventDefault()` trên đối tượng sự kiện để ngăn chặn điều này xảy ra:

```jsx
export default function Signup() {
  return (
    <form onSubmit={e => {
      e.preventDefault();
      alert('Submitting!');
    }}>
      <input />
      <button>Send</button>
    </form>
  );
}
```
