# PHẦN A — KIỂM TRA ĐỌC HIỂU (20 điểm)

## Câu A1 (5đ) — HTTP & Browser

Đọc chương 01 (01_introduction_html_universe.md), trả lời:

A11. Khi bạn gõ https://shopee.vn vào trình duyệt và nhấn Enter, hãy liệt kê đúng thứ tự ít nhất 5 bước xảy ra (từ DNS lookup đến render).

A12. Trong DevTools của Chrome, tab Network cho thấy thông tin gì? Hãy mở một trang web bất kỳ, chụp screenshot tab Network và đánh dấu (vẽ mũi tên/khoanh tròn) vào:

- Status Code của request đầu tiên
- Tổng thời gian load trang
- Một request trả về file CSS

## Trả lời

A11. Khi nhập https://shopee.vn, các bước xảy ra:

DNS → TCP/TLS → gửi request → server xử lý → trả response → tải tài nguyên → render → hiển thị

A12. Khoanh thông tin (/screenshots/baitapA12)

## Câu A2 (5đ) — Semantic HTML

Đọc chương 04, trả lời: Tại sao trang web dưới đây bị Google đánh giá SEO thấp? Liệt kê ít nhất 4 lỗi semantic và sửa lại.

```html
<div class="header">
  <div class="logo">ShopTLU</div>
  <div class="menu">
    <div><a href="/">Trang chủ</a></div>
    <div><a href="/products">Sản phẩm</a></div>
  </div>
</div>
<div class="main">
  <div class="product">
    <div class="title">iPhone 16 Pro</div>
    <div class="price">25.990.000đ</div>
    <div class="image"><img src="iphone.jpg" /></div>
  </div>
</div>
<div class="footer">© 2026 ShopTLU</div>
```

## Trả lời

Vì code trên dùng toàn <div> → Google không hiểu cấu trúc → bị đánh giá SEO thấp.

- Lỗi 1: Không dùng `<header>` <br>
  Sửa: `<div class="header">` -> `<header>` <br>
- Lỗi 2: Menu không dùng `<nav>` <br>
  Sửa: `<div class="menu">` -> `<nav>` <br>
- Lỗi 3: Không dùng `<main>` <br>
  Sửa: `<div class="main">` -> `<main>` <br>
- Lỗi 4: Footer không semantic <br>
  Sửa: `<div class="footer">` -> `<footer>` <br>

## Câu A3 (5đ) — Block vs Inline

Không chạy code, hãy vẽ tay (hoặc mô tả bằng text art) kết quả hiển thị của đoạn HTML sau. Giải thích tại sao.

```
<div>Hộp 1</div>
<span>Text A</span>
<span>Text B</span>
<div>Hộp 2</div>
<span>Text C</span>
<strong>Text D</strong>
<div>Hộp 3</div>
```

## Trả lời

Kết quả hiển thị: <br>
Hộp 1 <br>
Text A Text B <br>
Hộp 2 <br>
Text C **Text D** <br>
Hộp 3 <br>

Giải thích: <br>
🔹`<div>` là block

- Chiếm cả dòng
- Tự xuống dòng

🔹`<span>`, `<strong>` là inline

- Nằm cùng dòng
- Không xuống dòng

## Câu A4 (5đ) — Table

Đọc chương 05. Giải thích sự khác nhau giữa `<thead>`, `<tbody>`, `<tfoot>`. Tại sao KHÔNG NÊN dùng table để tạo layout trang web? (Ghi rõ ít nhất 3 lý do)

## Trả lời

`<thead>`, `<tbody>`, `<tfoot>` khác nhau: <br>
🔹`<thead>`: Phần tiêu đề bảng <br>
🔹`<tbody>`: Nội dung chính <br>
🔹`<tfoot>`: Phần cuối (tổng, ghi chú) <br>

Vì sao KHÔNG nên dùng table để layout:

- Lý do 1: Không semantic <br>
  Table dùng cho dữ liệu, không phải layout <br>
- Lý do 2: Khó responsive <br>
  Table không linh hoạt trên mobile <br>
- Lý do 3: Code khó bảo trì <br>
  Lồng nhiều `<tr>`, `<td>` → rất rối <br>
- Lý do 4: SEO kém <br>
  Google khó hiểu nội dung <br>

# PHẦN B — THỰC HÀNH CODE (60 điểm)

## Bài B1 (15đ) — Trang Profile cá nhân

## Bài B2 (15đ) — Trang Sản phẩm E-Commerce

## Bài B3 (15đ) — Debug HTML

- Lỗi 1: Dòng 1 — <!DOCTYPE> thiếu html — Sửa thành `<!DOCTYPE html>`

- Lỗi 2: Dòng 2 — Thiếu thuộc tính lang trong `<html>` — Thêm lang="vi"

- Lỗi 3: Dòng 4 — Thẻ `<title>` không đóng — Thêm `</title>`

- Lỗi 4: Dòng 5 — charset sai (utf8) — Sửa thành UTF-8

- Lỗi 5: Dòng 9 — Thẻ `<h1>` không đóng đúng — Sửa thành `</h1>`

- Lỗi 6: Dòng 13 — Thẻ `<a>` không đóng — Thêm `</a>`

- Lỗi 7: Dòng 20 — Thiếu dấu ngoặc kép src ảnh — Sửa thành src="iphone.jpg"

- Lỗi 8: Dòng 20 — Thiếu thuộc tính alt — Thêm alt="iPhone 16 Pro"

- Lỗi 9: Dòng 22 — Sai thứ tự đóng thẻ `<b>` — Sửa thành `<strong>`...`</strong>`

- Lỗi 10: Dòng 28 — Table thiếu `<thead>`, `<tbody>` — Thêm cấu trúc semantic

- Lỗi 11: Dòng 36 — Dùng `<main>` sai (2 lần) — Đổi cái thứ 2 thành `<aside>`

- Lỗi 12: Dòng 41 — Thẻ `<p>` trong footer không đóng — Thêm `</p>`

## Bài B4 (15đ) — Phân tích trang web thật

Trong trang shopee.vn có:

### 1. Sử dụng semantic

- Không tìm thấy rõ các thẻ semantic như `<header>`, `<nav>`, `<main>`
- Trang chủ yếu dùng `<div>` để xây dựng layout

### 2. Tìm table trên trang

- Trang Shopee không dùng table cho layout mà dùng `<div>` → không có `<thead>`, `<tbody>`

### 3. Tìm form trên trang

- Trang không có `action` và `method`
- Input types: <br>
  `<input>` (ô nhập tìm kiếm) → type mặc định là "text" <br>
  `<button type="button">` → dùng để kích hoạt tìm kiếm <br>

# PHẦN C — SUY LUẬN (20 điểm)

## Câu C1 (10đ) — Thiết kế cấu trúc

```html
<!DOCTYPE html>
<html lang="vi">
  <head>
    <meta charset="UTF-8" />
    <title>Nguyễn Văn Chiến</title>
  </head>

  <body>
    <header>
      <!-- HEADER: chứa logo + menu điều hướng -->
      <h1>Sản phẩm</h1>
      <!-- tiêu đề website -->

      <!-- NAV: menu điều hướng chính -->
      <nav>
        <a href="#">Trang chủ</a>
        <a href="#">Danh mục</a>
        <a href="#">Liên hệ</a>
      </nav>
    </header>

    <!-- MAIN: nội dung chính của trang -->
    <main>
      <!-- BREADCRUMB: điều hướng vị trí -->
      <nav aria-label="breadcrumb">
        <!-- dùng ol vì breadcrumb có thứ tự -->
        <ol>
          <li><a href="#">Trang chủ</a></li>
          <li><a href="#">Điện thoại</a></li>
          <li><a href="#">iPhone 16</a></li>
        </ol>
      </nav>

      <!-- SECTION: khối chi tiết sản phẩm -->
      <section>
        <!-- ARTICLE: 1 sản phẩm độc lập -->
        <article>
          <!-- FIGURE: chứa hình ảnh sản phẩm -->
          <figure>
            <img src="img1.jpg" alt="Ảnh sản phẩm 1" />
            <img src="img2.jpg" alt="Ảnh sản phẩm 2" />
            <img src="img3.jpg" alt="Ảnh sản phẩm 3" />
            <img src="img4.jpg" alt="Ảnh sản phẩm 4" />
            <img src="img5.jpg" alt="Ảnh sản phẩm 5" />
            <!-- figcaption: mô tả ảnh -->
            <figcaption>Hình ảnh sản phẩm</figcaption>
          </figure>

          <!-- SECTION: thông tin sản phẩm -->
          <section>
            <h2>iPhone 16</h2>
            <!-- tên sản phẩm -->

            <p>Giá: <strong>25.990.000đ</strong></p>
            <!-- giá -->

            <p>⭐⭐⭐⭐⭐</p>
            <!-- đánh giá sao -->

            <p>Mô tả sản phẩm...</p>
            <!-- mô tả -->
          </section>

          <!-- SECTION: bảng thông số kỹ thuật -->
          <section>
            <h2>Thông số kỹ thuật</h2>

            <table border="1">
              <!-- thead: tiêu đề bảng -->
              <thead>
                <tr>
                  <th>Thuộc tính</th>
                  <th>Giá trị</th>
                </tr>
              </thead>

              <!-- tbody: dữ liệu -->
              <tbody>
                <tr>
                  <td>Màn hình</td>
                  <td>6.7 inch</td>
                </tr>
              </tbody>
            </table>
          </section>

          <!-- SECTION: đánh giá / bình luận -->
          <section>
            <h2>Đánh giá</h2>
            <p>Người dùng bình luận...</p>
          </section>
        </article>
      </section>

      <!-- ASIDE: sản phẩm liên quan -->
      <aside>
        <h3>Sản phẩm tương tự</h3>
        <p>Danh sách sản phẩm...</p>
      </aside>
    </main>

    <!-- FOOTER: thông tin cuối trang -->
    <footer>
      <p>&copy; 2026 ShopTLU</p>
    </footer>
  </body>
</html>
```

## Câu C2 (10đ) — So sánh & Tranh luận

Việc sử dụng `<div>` cho mọi thứ và chỉ dựa vào class có thể nhanh lúc đầu, nhưng về lâu dài sẽ gây nhiều vấn đề:

- Thứ nhất, về SEO, các công cụ tìm kiếm như Google sử dụng cấu trúc semantic để hiểu nội dung trang. Khi dùng các thẻ như `<header>`, `<article>`, `<section>`, nội dung được phân loại rõ ràng, giúp tăng khả năng xếp hạng. Ngược lại, nếu toàn bộ là `<div>`, công cụ tìm kiếm khó xác định đâu là nội dung chính.

- Thứ hai, về accessibility, semantic HTML hỗ trợ các công cụ như screen reader đọc trang web hiệu quả hơn. Ví dụ, khi dùng `<nav>`, người dùng khiếm thị có thể nhanh chóng nhảy đến khu vực điều hướng mà không phải nghe toàn bộ nội dung. Nếu chỉ dùng `<div>`, trải nghiệm này sẽ kém hơn rất nhiều.

Một ví dụ cụ thể: trang blog sử dụng `<article>` cho từng bài viết sẽ giúp cả công cụ tìm kiếm và người dùng hiểu rằng mỗi khối là một nội dung độc lập. Điều này cải thiện SEO và khả năng truy cập rõ rệt so với việc dùng `<div>`.

Tuy nhiên, `<div>` vẫn phù hợp trong các trường hợp chỉ dùng để chia layout hoặc styling, ví dụ như wrapper hoặc grid container trong CSS. Vì vậy, cách tốt nhất không phải là bỏ semantic HTML, mà là kết hợp hợp lý giữa semantic và `<div>` để đạt hiệu quả tối ưu.

# PHẦN D — VIDEO THỰC HÀNH OBS (25 điểm)
