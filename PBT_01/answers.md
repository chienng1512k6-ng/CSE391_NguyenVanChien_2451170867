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

❌ Lý do 1: Không semantic <br>
Table dùng cho dữ liệu, không phải layout <br>
❌ Lý do 2: Khó responsive <br>
Table không linh hoạt trên mobile <br>
❌ Lý do 3: Code khó bảo trì <br>
Lồng nhiều `<tr>`, `<td>` → rất rối <br>
❌ Lý do 4: SEO kém <br>
Google khó hiểu nội dung <br>

# PHẦN B — THỰC HÀNH CODE (60 điểm)

## Bài B1 (15đ) — Trang Profile cá nhân

## Bài B2 (15đ) — Trang Sản phẩm E-Commerce

## Bài B3 (15đ) — Debug HTML

- Lỗi 1: Dòng 1 — <!DOCTYPE> thiếu html — Sửa thành `<!DOCTYPE html>`

- Lỗi 2: Dòng 2 — Thiếu thuộc tính lang trong `<html>` — Thêm lang="vi"

- Lỗi 2: Dòng 4 — Thẻ `<title>` không đóng — Thêm `</title>`

- Lỗi 3: Dòng 5 — charset sai (utf8) — Sửa thành UTF-8

- Lỗi 4: Dòng 9 — Thẻ `<h1>` không đóng đúng — Sửa thành `</h1>`

- Lỗi 5: Dòng 13 — Thẻ `<a>` không đóng — Thêm `</a>`

- Lỗi 6: Dòng 20 — Thiếu dấu ngoặc kép src ảnh — Sửa thành src="iphone.jpg"

- Lỗi 7: Dòng 20 — Thiếu thuộc tính alt — Thêm alt="iPhone 16 Pro"

- Lỗi 8: Dòng 22 — Sai thứ tự đóng thẻ `<b>` — Sửa thành `<strong>`...`</strong>`

- Lỗi 9: Dòng 28 — Table thiếu `<thead>`, `<tbody>` — Thêm cấu trúc semantic

- Lỗi 10: Dòng 36 — Dùng `<main>` sai (2 lần) — Đổi cái thứ 2 thành `<aside>`

- Lỗi 11: Dòng 41 — Thẻ `<p>` trong footer không đóng — Thêm `</p>`

## Bài B4 (15đ) — Phân tích trang web thật

# PHẦN C — SUY LUẬN (20 điểm)

# PHẦN D — VIDEO THỰC HÀNH OBS (25 điểm)
