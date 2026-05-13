# PHẦN A — KIỂM TRA ĐỌC HIỂU (20 điểm)

## Câu A1 (10đ) — 5 Loại Positioning

Đọc chương 12. Điền bảng sau mà **KHÔNG** tra Google:

| Position   | Vẫn chiếm chỗ trong flow? | Tham chiếu vị trí | Cuộn theo trang? | Use case |
| ---------- | ------------------------- | ----------------- | ---------------- | -------- |
| `static`   | ???                       | ???               | ???              | ???      |
| `relative` | ???                       | ???               | ???              | ???      |
| `absolute` | ???                       | ???               | ???              | ???      |
| `fixed`    | ???                       | ???               | ???              | ???      |
| `sticky`   | ???                       | ???               | ???              | ???      |

**Câu hỏi thêm:** Khi nào `absolute` tham chiếu `body`? Khi nào tham chiếu parent? Giải thích khái niệm "nearest positioned ancestor".

## Trả lời

| Position   | Vẫn chiếm chỗ trong flow? | Tham chiếu vị trí           | Cuộn theo trang?           | Use case                               |
| ---------- | ------------------------- | --------------------------- | -------------------------- | -------------------------------------- |
| `static`   | Có                        | Vị trí mặc định             | Có                         | Layout bình thường                     |
| `relative` | Có                        | Chính vị trí ban đầu của nó | Có                         | Dịch nhẹ phần tử, làm mốc cho absolute |
| `absolute` | Không                     | Parent gần nhất có position | Có                         | Tooltip, popup, badge                  |
| `fixed`    | Không                     | Viewport (màn hình)         | Không                      | Nút chat, menu cố định                 |
| `sticky`   | Có                        | Container cuộn              | Sticky khi cuộn tới ngưỡng | Header dính khi scroll                 |

- Nếu KHÔNG có parent nào có:

```css
position: relative;
position: absolute;
position: fixed;
position: sticky;
```

thì `absolute` sẽ tham chiếu `body`.

- Nếu parent gần nhất có:

```css
position: relative;
```

hoặc bất kỳ position nào khác `static`

→ `absolute` sẽ lấy parent đó làm mốc.

- "Nearest positioned ancestor" Là phần tử cha gần nhất có `position` khác `static`.

## Câu A2 (10đ) — Flexbox vs Grid

Không chạy code, dự đoán layout cho mỗi trường hợp. **Vẽ sơ đồ bố cục** (text art hoặc vẽ tay chụp ảnh).

```css
/* Trường hợp 1 */
.container {
  display: flex;
}
.item {
  flex: 1;
}
/* 4 items → Bố cục = ??? */

/* Trường hợp 2 */
.container {
  display: flex;
  flex-wrap: wrap;
}
.item {
  width: 45%;
  margin: 2.5%;
}
/* 6 items → Bố cục = ??? (mấy hàng, mấy cột?) */

/* Trường hợp 3 */
.container {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
/* 3 items → Bố cục = ??? */

/* Trường hợp 4 */
.container {
  display: grid;
  grid-template-columns: 200px 1fr 200px;
  gap: 20px;
}
/* 3 items → Bố cục = ??? */

/* Trường hợp 5 */
.container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 10px;
}
/* 7 items → Bố cục = ??? (mấy hàng? item cuối ở đâu?) */
```

## Trả lời

- Trường hợp 1: 4 items nằm trên cùng 1 hàng

```text
| Item | Item | Item | Item |
```

- Trường hợp 2: 2 items nằm trên cùng 1 hàng. Có 3 hàng 2 cột

```text
| Item | Item |
| Item | Item |
| Item | Item |
```

- Trường hợp 3: 3 items nằm ngang, khoảng cách đều nhau

```text
| Item        Item        Item |
```

- Trường hợp 4: 3 cột
  - Cột trái: 200px
  - Cột giữa: co giãn
  - Cột phải: 200px

```text
| 200px | flexible | 200px |
```

- Trường hợp 5: 3 hàng

```text
| Item | Item | Item |
| Item | Item | Item |
| Item |
```

→ Item cuối nằm ở: hàng 3, cột 1

# PHẦN B — THỰC HÀNH CODE (60 điểm)

## Bài B1 (15đ) — Positioning Playground

## Bài B2 (20đ) — Flexbox Navigation & Cards

## Bài B3 (25đ) — Grid Layout — Trang E-Commerce

# PHẦN C — SUY LUẬN (20 điểm)

## Câu C1 (10đ) — Flexbox vs Grid: Khi nào dùng gì?

Cho 5 tình huống layout thực tế. Với mỗi tình huống, trả lời: dùng **Flexbox**, **Grid**, hay **kết hợp cả hai**? Giải thích ngắn gọn tại sao.

1. Navigation bar ngang (logo + menu + buttons)
2. Lưới ảnh Instagram (3 cột đều nhau, số ảnh không biết trước)
3. Layout blog: main content + sidebar
4. Footer với 4 cột thông tin (Về chúng tôi, Liên kết, Hỗ trợ, Liên hệ)
5. Card sản phẩm (ảnh trên, text giữa, nút dưới — nút luôn dính đáy)

## Trả lời

1. Navigation bar ngang (logo + menu + buttons) <br>

→ Dùng: **Flexbox**

🔹 Giải thích: <br>

Navbar là layout 1 chiều (theo hàng ngang). <br>

Flexbox rất phù hợp để: <br>

- căn giữa theo chiều dọc
- tạo khoảng cách giữa các item
- đẩy menu sang trái/phải dễ dàng <br>

2. Lưới ảnh Instagram (3 cột đều nhau, số ảnh không biết trước) <br>

→ Dùng: **Grid**

🔹 Giải thích: <br>

Đây là layout dạng lưới 2 chiều: <br>

- nhiều hàng
- nhiều cột <br>

Grid giúp: <br>

- tạo cột đều nhau dễ dàng
- tự động xuống hàng
- quản lý khoảng cách tốt hơn <br>

3. Layout blog: main content + sidebar <br>

→ Dùng: **Flexbox** <br>

🔹 Giải thích: <br>

Layout chỉ có: <br>

- content chính
- sidebar <br>

→ Đây là bố cục 1 hàng ngang <br>

Flexbox phù hợp để: <br>

- chia chiều rộng linh hoạt
- dễ responsive <br>

4. Footer với 4 cột thông tin <br>

→ Dùng: **Grid**

🔹 Giải thích: <br>

Footer có nhiều cột đều nhau: <br>

- Về chúng tôi
- Liên kết
- Hỗ trợ
- Liên hệ <br>

Grid phù hợp vì: <br>

- quản lý nhiều cột dễ
- căn chỉnh đều
- responsive tốt

5. Card sản phẩm (ảnh trên, text giữa, nút dưới — nút luôn dính đáy) <br>

→ Dùng: **Kết hợp cả hai** <br>

🔹 Giải thích: <br>

- Dùng Grid/Flexbox cho layout ngoài
- Dùng Flexbox bên trong card <br>

→ nút luôn dính đáy card dù text dài/ngắn khác nhau.

## Câu C2 (10đ) — Debug Flexbox

Layout sau bị lỗi. Mô tả lỗi và sửa.

**Lỗi 1:** Cards không đều chiều cao — nút "Mua" bị nhảy lên/xuống

```css
.card-container {
  display: flex;
  flex-wrap: wrap;
}
.card {
  width: 30%;
  margin: 1.5%;
}
.card img {
  width: 100%;
}
.card h3 {
  font-size: 18px;
}
.card .btn {
  padding: 10px;
}
```

**Lỗi 2:** Muốn items nằm giữa cả ngang lẫn dọc trong container 100vh, nhưng item vẫn dính góc trái trên

```css
.hero {
  height: 100vh;
  display: flex;
}
.hero-content {
  text-align: center;
}
```

**Lỗi 3:** Sidebar bị co lại khi content quá dài

```css
.layout {
  display: flex;
}
.sidebar {
  width: 250px;
}
.content {
  flex: 1;
}
```

Cho mỗi lỗi: Giải thích nguyên nhân → Viết code sửa → Chụp screenshot trước/sau.

## Trả lời

**Lỗi 1:** Cards không đều chiều cao — nút "Mua" bị nhảy

🔹 Nguyên nhân

Các card có lượng text khác nhau nên chiều cao khác nhau.

Nút `.btn` nằm ngay sau nội dung,
nên card nào text dài hơn → nút bị đẩy xuống thấp hơn.

🔹 Cách sửa

Dùng Flexbox theo chiều dọc cho card:

```css
.card {
  width: 30%;
  margin: 1.5%;

  display: flex;
  flex-direction: column;
}
```

Đẩy nút xuống đáy:

```css
.card .btn {
  padding: 10px;
  margin-top: auto;
}
```

🔹 Code hoàn chỉnh

```css
.card-container {
  display: flex;
  flex-wrap: wrap;
}

.card {
  width: 30%;
  margin: 1.5%;

  display: flex;
  flex-direction: column;
}

.card img {
  width: 100%;
}

.card h3 {
  font-size: 18px;
}

.card .btn {
  padding: 10px;
  margin-top: auto;
}
```

🔹 Kết quả

- Các card đều chiều cao hơn
- Nút "Mua" luôn nằm đáy card

**Lỗi 2:** Item không nằm giữa màn hình

🔹 Nguyên nhân

Container `.hero` chỉ có:

```css
display: flex;
```

Mặc định:

- `justify-content: flex-start`
- `align-items: stretch`

→ nội dung nằm góc trái trên.

🔹 Cách sửa

Thêm:

```css
justify-content: center;
align-items: center;
```

🔹 Code sửa

```css
.hero {
  height: 100vh;
  display: flex;

  justify-content: center;
  align-items: center;
}

.hero-content {
  text-align: center;
}
```

🔹 Kết quả

`.hero-content`
được căn giữa:

- ngang
- dọc

**Lỗi 3:** Sidebar bị co lại

🔹 Nguyên nhân

Trong Flexbox:

```css
flex-shrink: 1;
```

là mặc định.

→ Sidebar được phép co lại khi content quá dài.

🔹 Cách sửa

Ngăn sidebar co:

```css
.sidebar {
  width: 250px;
  flex-shrink: 0;
}
```

🔹 Code sửa hoàn chỉnh

```css
.layout {
  display: flex;
}

.sidebar {
  width: 250px;
  flex-shrink: 0;
}

.content {
  flex: 1;
}
```

🔹 Kết quả

- Sidebar luôn giữ 250px
- Content chiếm phần còn lại

# 🎬 PHẦN D — VIDEO THỰC HÀNH OBS (25 điểm)
