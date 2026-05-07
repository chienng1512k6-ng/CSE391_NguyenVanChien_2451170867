# PHẦN A — KIỂM TRA ĐỌC HIỂU (20 điểm)

## Câu A1 (5đ) — 3 Cách nhúng CSS

Đọc chương 08. Liệt kê 3 cách nhúng CSS vào HTML (inline, internal, external). Mỗi cách:

- Viết 1 ví dụ code
- Ưu điểm và nhược điểm
- Khi nào nên dùng

**Câu hỏi thêm:** Nếu cùng 1 element có cả 3 cách CSS đồng thời áp dụng, cách nào "thắng"? Giải thích tại sao.

## Trả lời

1. Inline CSS

Ví dụ: <br>

`<p style="color: red;">Xin chào</p>` <br>

Ưu điểm: <br>

- Nhanh, áp dụng trực tiếp cho 1 phần tử
- Không cần tạo file CSS riêng

Nhược điểm: <br>

- Khó bảo trì khi code lớn
- Lặp lại nhiều → code rối
- Không tái sử dụng được

Khi nên dùng: <br>

- Test nhanh
- Style nhỏ, tạm thời

2. Internal CSS

Ví dụ: <br>

```html
<head>
  <style>
    p {
      color: blue;
    }
  </style>
</head>
```

Ưu điểm: <br>

- Quản lý tập trung trong 1 file HTML
- Dễ hơn inline

Nhược điểm: <br>

- Chỉ dùng cho 1 trang
- Không tái sử dụng cho nhiều trang

Khi nên dùng: <br>

- Website nhỏ
- Trang đơn lẻ

3. External CSS

Ví dụ: <br>

```
<head>
    <link rel="stylesheet" href="style.css">
</head>

File style.css:
p {
color: green;
}
```

Ưu điểm: <br>

- Tái sử dụng nhiều trang
- Dễ bảo trì, sạch code
- Tăng hiệu năng (cache)

Nhược điểm: <br>

- Cần thêm file riêng
- Có thể tải chậm nếu mạng yếu

Khi nên dùng: <br>

- Website lớn
- Dự án thực tế

## Câu A2 (8đ) — CSS Selectors — Dự đoán kết quả

Cho HTML sau:

```html
<div id="app">
  <header class="top-bar dark">
    <h1>ShopTLU</h1>
    <nav>
      <a href="/" class="active">Home</a>
      <a href="/products">Products</a>
      <a href="/about">About</a>
    </nav>
  </header>
  <main>
    <article class="product">
      <h2>iPhone 16</h2>
      <p class="price">25.990.000đ</p>
      <p>Mô tả sản phẩm...</p>
    </article>
    <article class="product featured">
      <h2>MacBook Pro</h2>
      <p class="price">45.990.000đ</p>
      <p>Mô tả sản phẩm...</p>
    </article>
  </main>
</div>
```

**Không chạy code**, cho biết mỗi selector sau chọn được element nào? (Ghi cụ thể text content)

```css
1. h1                           → Chọn: ???
2. .price                       → Chọn: ???
3. #app header                  → Chọn: ???
4. nav a:first-child             → Chọn: ???
5. .product.featured h2         → Chọn: ???
6. article > p                  → Chọn: ???
7. a[href="/"]                  → Chọn: ???
8. .top-bar.dark h1              → Chọn: ???
```

**Sau khi trả lời**, tạo file `selectors_test.html` để kiểm chứng đáp án. Chụp screenshot.

## Trả lời

1. h1  
   → Chọn: "ShopTLU"  
   → Vì chỉ có 1 thẻ `<h1>`

2. .price  
   → Chọn:

- "25.990.000đ"
- "45.990.000đ"  
  → Vì cả 2 `<p>` đều có class="price"

3. #app header  
   → Chọn: toàn bộ phần header chứa:

- "ShopTLU"
- "Home"
- "Products"
- "About"

4. nav a:first-child  
   → Chọn: "Home"  
   → Vì là thẻ `<a>` đầu tiên trong `<nav>`

5. .product.featured h2  
   → Chọn: "MacBook Pro"  
   → Vì chỉ article thứ 2 có class "featured"

6. article > p  
   → Chọn:

- "25.990.000đ"
- "Mô tả sản phẩm..."
- "45.990.000đ"
- "Mô tả sản phẩm..."
  → Vì chọn tất cả `<p>` là con trực tiếp của `<article>`

7. a[href="/"]  
   → Chọn: "Home"  
   → Vì link có href="/"

8. .top-bar.dark h1  
   → Chọn: "ShopTLU"  
   → Vì h1 nằm trong header có class "top-bar dark"

## Câu A3 (7đ) — Box Model — Tính toán kích thước

Đọc chương 11 (Box Model). Tính **kích thước thực tế** (chiều rộng thực tế render trên browser) cho mỗi trường hợp sau:

```css
/* Trường hợp 1: content-box (mặc định) */
.box-1 {
    width: 400px;
    padding: 20px;
    border: 5px solid black;
    margin: 10px;
}
→ Chiều rộng hiển thị = ???
→ Không gian chiếm trên trang = ???

/* Trường hợp 2: border-box */
.box-2 {
    box-sizing: border-box;
    width: 400px;
    padding: 20px;
    border: 5px solid black;
    margin: 10px;
}
→ Chiều rộng hiển thị = ???
→ Kích thước content thực tế = ???
→ Không gian chiếm trên trang = ???

/* Trường hợp 3: Margin collapse */
.box-a { margin-bottom: 25px; }
.box-b { margin-top: 40px; }
→ Khoảng cách giữa box-a và box-b = ???
→ Giải thích tại sao KHÔNG PHẢI 65px
```

**Nâng cao:** Nếu `.box-a` có `margin-bottom: -10px` và `.box-b` có `margin-top: 40px`, khoảng cách = bao nhiêu?

## Trả lời

```css
Trường hợp 1: content-box

→ Chiều rộng hiển thị = 400 + 20*2 + 5*2 = 450px

→ Không gian chiếm trên trang = 450 + 10\*2 = 470px

Trường hợp 2: border-box

→ Chiều rộng hiển thị = 400px

→ Kích thước content thực tế = 400 - 20*2 - 5*2 = 350px

→ Không gian chiếm trên trang = 400 + 10\*2 = 420px

Trường hợp 3: Margin collapse

→ Khoảng cách giữa box-a và box-b = 40px

→ Giải thích:
Margin theo chiều dọc sẽ bị "collapse" (gộp lại)
→ Trình duyệt chỉ lấy giá trị lớn hơn (max)
→ Không cộng 25px + 40px

Nâng cao:

.box-a { margin-bottom: -10px; }
.box-b { margin-top: 40px; }

→ Khoảng cách = 40 + (-10) = 30px
```

## Câu A4 (5đ) — Specificity (Độ ưu tiên)

Cho các CSS rules sau cùng target 1 element `<p class="price" id="main-price">`:

```css
p {
  color: black;
} /* Rule A */
.price {
  color: blue;
} /* Rule B */
#main-price {
  color: red;
} /* Rule C */
p.price {
  color: green;
} /* Rule D */
```

1. Tính specificity score (a, b, c) cho mỗi rule
2. Element sẽ có màu gì? Giải thích
3. Nếu thêm `<p class="price" id="main-price" style="color: orange;">`, element có màu gì?
4. Nếu Rule A thêm `!important`, element có màu gì? Tại sao?

## Trả lời

1. Specificity:

Rule A: p
→ (0, 0, 1)

Rule B: .price
→ (0, 1, 0)

Rule C: #main-price
→ (1, 0, 0)

Rule D: p.price
→ (0, 1, 1)

2. Element sẽ có màu gì?

→ Màu đỏ. Vì Rule C (#main-price) có specificity cao nhất (1,0,0)

3. Nếu thêm style inline:

```
<p class="price" id="main-price" style="color: orange;">
```

→ Màu cam (orange). Vì Inline style có độ ưu tiên cao hơn tất cả selector thường

4. Nếu Rule A thêm !important:

```
p {
color: black !important;
}
```

→ Màu đen. Vì !important có ưu tiên cao hơn tất cả (kể cả id và inline style)

# PHẦN B — THỰC HÀNH CODE (55 điểm)

## Bài B1 (20đ) — Style trang Profile

## Bài B2 (20đ) — Box Model Lab

Phần 1:

Hộp 1 (content-box):
→ Chiều rộng thực tế = 350px

(300 + 20*2 + 5*2)

Hộp 2 (border-box):
→ Chiều rộng thực tế = 300px

Giải thích:

- content-box: width chỉ tính content → padding + border làm tăng kích thước
- border-box: width đã bao gồm padding + border → không bị phình ra

Phần 2:

Trường hợp content-box:

- Sidebar: 250 + padding
- Content: 500 + padding
- Ads: 250 + padding

→ Tổng > 1000px → bị vỡ layout

Trường hợp border-box:
→ Tổng đúng 1000px

Giải thích:

- border-box giúp giữ nguyên kích thước tổng
- content-box làm layout bị lệch nếu không tính toán kỹ

## Bài B3 (15đ) — Specificity Battle

## Specificity Battle

1. p → (0,0,1)
2. .text → (0,1,0)
3. .highlight → (0,1,0)
4. p.text → (0,1,1)
5. p.highlight → (0,1,1)
6. .text.highlight → (0,2,0)
7. p.text.highlight → (0,2,1)
8. #demo → (1,0,0)
9. #demo.text → (1,1,0)
10. #demo.text.highlight → (1,2,0)

---

Element cuối cùng hiển thị màu:

→ black

Giải thích:
Rule #10 có specificity cao nhất (1,2,0) nên ghi đè tất cả rule khác.

---

Nếu thay đổi thứ tự rules trong CSS:

→ KHÔNG đổi kết quả

Giải thích:
Trình duyệt ưu tiên specificity trước, không phải thứ tự.
Chỉ khi specificity bằng nhau thì mới xét thứ tự (rule viết sau thắng).

# PHẦN C — DEBUG & SUY LUẬN (20 điểm)

## Câu C1 (10đ) — Debug CSS Layout

Layout dưới đây bị vỡ. Container rộng `960px`, sidebar + content phải nằm **cạnh nhau**. Nhưng content bị đẩy xuống dòng mới.

```css
.container {
  width: 960px;
  margin: 0 auto;
}
.sidebar {
  width: 300px;
  padding: 20px;
  border: 1px solid #ccc;
  float: left;
}
.content {
  width: 660px;
  padding: 30px;
  border: 1px solid #ccc;
  float: left;
}
```

1. Tính chiều rộng **thực tế** của sidebar và content (content-box!)
2. Giải thích tại sao layout bị vỡ
3. Đưa ra **2 cách sửa** khác nhau (1 cách dùng border-box, 1 cách không dùng)
4. Tạo file `debug_layout.html` + `debug_layout.css` chứng minh cả 2 cách sửa hoạt đ

## Trả lời

1. Tính chiều rộng thực tế

Sidebar:

- width: 300px
- padding: 20px
- border: 1px

→ Chiều rộng thực tế:
300 + 20*2 + 1*2
= 342px

---

Content:

- width: 660px
- padding: 30px
- border: 1px

→ Chiều rộng thực tế:
660 + 30*2 + 1*2
= 722px

---

Tổng chiều rộng:

342 + 722
= 1064px

Trong khi container chỉ có 960px

→ Layout bị vỡ

2. Giải thích tại sao layout bị vỡ

CSS mặc định dùng box-sizing: content-box

→ width chỉ tính phần content
→ padding và border được cộng thêm bên ngoài

Tổng kích thước sidebar + content lớn hơn container
nên content bị đẩy xuống dòng mới.

3. Hai cách sửa

Cách 1 — Dùng border-box

box-sizing: border-box;

→ padding + border được tính bên trong width
→ tổng kích thước không vượt quá container

---

Cách 2 — Không dùng border-box

Giảm width thực tế:

.sidebar {
width: 258px;
}

.content {
width: 598px;
}

Tổng:
258 + 40 + 2 + 598 + 60 + 2
= 960px

→ Layout vừa container

## Câu C2 (10đ) — Cascade Puzzle

Cho CSS file:

```css
body {
  font-size: 16px;
  color: #333;
}
.container {
  font-size: 14px;
}
.card {
  color: blue;
}
.card .title {
  font-size: 20px;
}
.card p {
  color: inherit;
}
#featured .title {
  color: red;
}
.highlight {
  color: green !important;
}
```

Và HTML:

```html
<body>
  <div class="container">
    <div class="card" id="featured">
      <h2 class="title highlight">Sản phẩm A</h2>
      <p>Mô tả sản phẩm</p>
    </div>
    <div class="card">
      <h2 class="title">Sản phẩm B</h2>
      <p class="highlight">Mô tả sản phẩm B</p>
    </div>
  </div>
</body>
```

**Không chạy code**, trả lời:

1. "Sản phẩm A" (h2) có `font-size` = ? và `color` = ?
2. "Mô tả sản phẩm" (p trong card featured) có `color` = ?
3. "Sản phẩm B" (h2) có `font-size` = ? và `color` = ?
4. "Mô tả sản phẩm B" (p.highlight) có `color` = ?

Giải thích chi tiết quá trình cascade + inheritance cho mỗi câu.

Sau đó, tạo file HTML+CSS kiểm chứng và chụp screenshot.

---

## Trả lời

1. "Sản phẩm A" (h2)

- font-size = 20px

- Giải thích:
  Rule:

```css
.card .title {
  font-size: 20px;
}
```

→ h2 có class="title"
→ nằm trong .card
→ áp dụng font-size: 20px

---

color = green

- Giải thích:

Có các rule:

```css
.card {
  color: blue;
}

#featured .title {
  color: red;
}

.highlight {
  color: green !important;
}
```

---

Cascade:

- blue được inherit từ .card
- red áp dụng trực tiếp từ #featured .title
- green có !important

→ !important ưu tiên cao nhất

=> Màu cuối cùng = green

2. "Mô tả sản phẩm" (p trong featured)

HTML:

`<p>Mô tả sản phẩm</p>`

---

color = blue

- Giải thích:

Rule:

```css
.card {
  color: blue;
}

.card p {
  color: inherit;
}
```

---

p dùng:

color: inherit

→ kế thừa màu từ phần tử cha (.card)

.card có:
color: blue

=> p cũng có màu blue

3. "Sản phẩm B" (h2)

HTML:

`<h2 class="title">Sản phẩm B</h2>`

---

font-size = 20px

Giải thích:

Rule:

```css
.card .title {
  font-size: 20px;
}
```

→ áp dụng trực tiếp

---

color = blue

Giải thích:

Không có:

- #featured
- .highlight

nên h2 không có color riêng

→ kế thừa từ:

```css
.card {
  color: blue;
}
```

=> màu blue

4. "Mô tả sản phẩm B"

HTML:

`<p class="highlight">Mô tả sản phẩm B</p>`

---

color = green

Giải thích:

Rule:

```css
.highlight {
  color: green !important;
}
```

→ p có class="highlight"

!important ưu tiên cao nhất

=> màu cuối cùng = green

# 🎬 PHẦN D — VIDEO THỰC HÀNH OBS (25 điểm)
