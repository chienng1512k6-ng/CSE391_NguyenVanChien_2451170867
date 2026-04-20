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

`<div>`Hộp 1`</div>` <br>
`<span>`Text A`</span>` <br>
`<span>`Text B`</span>` <br>
`<div>`Hộp 2`</div>` <br>
`<span>`Text C`</span>` <br>
`<strong>`Text D`</strong>` <br>
`<div>`Hộp 3`</div>` <br>

## Trả lời

Kết quả hiển thị:
`Hộp 1
Text A Text B
Hộp 2
Text C Text D
Hộp 3`

Giải thích:
🔹`<div>` là block

- Chiếm cả dòng
- Tự xuống dòng

🔹`<span>`, `<strong>` là inline

- Nằm cùng dòng
- Không xuống dòng

## Câu A4 (5đ) — Table

Đọc chương 05. Giải thích sự khác nhau giữa `<thead>`, `<tbody>`, `<tfoot>`. Tại sao KHÔNG NÊN dùng table để tạo layout trang web? (Ghi rõ ít nhất 3 lý do)

## Trả lời

`<thead>`, `<tbody>`, `<tfoot>` khác nhau:
`<thead>` Phần tiêu đề bảng
`<tbody>` Nội dung chính
`<tfoot>` Phần cuối (tổng, ghi chú)

Vì sao KHÔNG nên dùng table để layout:

❌ Lý do 1: Không semantic
Table dùng cho dữ liệu, không phải layout
❌ Lý do 2: Khó responsive
Table không linh hoạt trên mobile
❌ Lý do 3: Code khó bảo trì
Lồng nhiều `<tr>`, `<td>` → rất rối
❌ Lý do 4: SEO kém
Google khó hiểu nội dung

# PHẦN B — THỰC HÀNH CODE (60 điểm)

# PHẦN C — SUY LUẬN (20 điểm)

# PHẦN D — VIDEO THỰC HÀNH OBS (25 điểm)
