# &#x20;SPA and MPA

### SPA là gì ?

SPA(Single Page Applications) là các ứng dụng web tự động cập nhật nội dung của chúng khi người dùng tương tác với nó. Chúng không yêu cầu tải lại trang nhờ AJAX (JavaScript và XML không đồng bộ). Khi người dùng tương tác với SPA, chỉ thành phần được yêu cầu sẽ được sửa đổi chứ không phải toàn bộ trang/ứng dụng.&#x20;

### MPA là gì ?

MPA(Multi Page Applications) là ứng dụng web bao gồm nhiều trang HTML. Mỗi trang hiển thị nội dung khác nhau phải được làm mới mỗi khi người dùng tương tác với trang đó

### Sự khác biệt

#### SPA

* Được cho là cách tiếp cận hiện đại hơn
* Không yêu cầu tải lại trang khi sử dụng

#### MPA

* Là cách tiếp cận cổ điển
* Tải lại trang trong quá trình sử dụng (click vào đường link,...)

### So sánh

#### Tốc độ

* SPA nhanh hơn khi sử dụng
  * Phần lớn tài nguyên được tải trong lần đầu
  * Trang chỉ tải thêm dữ liệu mới khi cần
*   MPA chậm hơn khi sử dụng

    * Luôn tải lai trang khi truy cập và chuyển hướng



#### Bóc tách

* SPA có phần frontend riêng biệt
* MPA thì phần frontend và backend phụ thuộc nhau nhiều hơn, được đặt chung trong một dự án

#### SEO

* SPA không thân thiện với seo như MPA

#### UX

* SPA cho trải nghiệm tốt hơn, nhất là các thao tác chuyển trang
* Trải nghiệm trên thiết bị di động tốt hơn

#### Quá trình phát triển

* SPA dễ dàng tái sử dụng code(component)
* SPA bóc tách FE & BE
  * Chia team phát triển song song
  * Phát triển thêm mobile dễ dàng

#### Phụ thuộc vào javascript

* SPA phụ thuộc hoàn toàn vào Javascript
* MPA có thể không cần javascript
