# PHẦN A — KIỂM TRA ĐỌC HIỂU (20 điểm)

## Câu A1 (5đ) — Input Types

Liệt kê **10 input types** khác nhau trong HTML5, cho mỗi type:

- Giao diện hiển thị (mô tả bằng lời)
- Validation tự động (nếu có)
- Use case cụ thể trong trang E-Commerce

Format trả lời:

```
1. type="email" → Ô nhập text, tự kiểm tra có @ → Dùng cho form đăng ký
2. type="..." → ...
```

## Trả lời

1. type="text" → Ô nhập văn bản 1 dòng → Dùng nhập tên sản phẩm, tên khách hàng

2. type="email" → Ô nhập text, kiểm tra có dấu @ và định dạng email → Dùng cho đăng ký / đăng nhập

3. type="password" → Ô nhập bị ẩn ký tự (••••) → Dùng nhập mật khẩu

4. type="number" → Ô nhập số, có nút tăng/giảm → Chỉ cho nhập số → Dùng nhập số lượng sản phẩm

5. type="tel" → Ô nhập số điện thoại → Dùng nhập số điện thoại

6. type="url" → Ô nhập link, kiểm tra định dạng URL → Dùng nhập link website

7. type="date" → Hiển thị bộ chọn ngày → Dùng chọn ngày

8. type="radio" → Nút chọn 1 trong nhiều lựa chọn → Chỉ chọn được 1 → Dùng chọn phương thức thanh toán

9. type="checkbox" → Ô tick chọn nhiều lựa chọn → Dùng chọn nhiều sản phẩm hoặc đồng ý điều khoản

10. type="file" → Nút upload file → Dùng upload ảnh đánh giá sản phẩm

## Câu A2 (5đ) — Validation Attributes

Đọc chương 07. Không chạy code, hãy **dự đoán** điều gì xảy ra khi user bấm Submit cho mỗi trường hợp sau. Giải thích TẠI SAO.

```html
<!-- Trường hợp 1 -->
<input type="text" required value="" />
<!-- User để trống -->

<!-- Trường hợp 2 -->
<input type="email" value="abc" />
<!-- User gõ "abc" -->

<!-- Trường hợp 3 -->
<input type="number" min="1" max="10" value="15" />
<!-- User gõ 15 -->

<!-- Trường hợp 4 -->
<input type="text" pattern="[0-9]{10}" value="abc123" />
<!-- User gõ "abc123" -->

<!-- Trường hợp 5 -->
<input type="password" minlength="8" value="123" />
<!-- User gõ "123" -->
```

**Sau khi trả lời**, tạo file `validation_test.html`, đặt 5 trường hợp trên vào 1 form, bấm Submit và **chụp screenshot** kết quả validation thực tế. So sánh với dự đoán.

## Trả lời

- Trường hợp 1: Không Submit được. Vì "required" là thuộc tính bắt buộc nhập, nhưng giá trị đang rỗng.
- Trường hợp 2: Không Submit được. Vì type="email" yêu cầu định dạng phải có "@", "abc" không hợp lệ.
- Trường hợp 3: Không submit được. Vì giá trị 15 vượt quá max="10".
- Trường hợp 4: Không submit được. Vì pattern yêu cầu đúng 10 chữ số, "abc123" không khớp regex.
- Trường hợp 5: Submit được. Vì không bắt buộc "required".

## Câu A3 (5đ) — Accessibility

Đọc phần Accessibility trong chương 07. Giải thích:

1. Tại sao `<label for="email">` quan trọng cho người dùng screen reader?
2. Khi nào dùng `<fieldset>` + `<legend>`? Cho ví dụ cụ thể.
3. `aria-label` dùng khi nào? Tại sao KHÔNG nên dùng `aria-label` khi đã có `<label>`?

## Trả lời

1. - `<label>` giúp liên kết mô tả với ô input thông qua thuộc tính "for"
   - Screen reader sẽ đọc: "Email, edit text" thay vì chỉ "edit text" <br>
     → Người dùng biết chính xác ô đó dùng để nhập gì

2. - Dùng khi có nhiều input liên quan cùng một nhóm <br>
     → Giúp screen reader hiểu đây là một nhóm thông tin
   - <fieldset>: bao nhóm
   - <legend>: tiêu đề nhóm

Ví dụ:

```
<fieldset>
    <legend>Phương thức thanh toán</legend>
    <input type="radio" name="pay"> Tiền mặt
    <input type="radio" name="pay"> Chuyển khoản
</fieldset>
```

3. - Dùng khi KHÔNG có label hiển thị
   - Ví dụ: icon button, input không có text <br>
     `<input type="text" aria-label="Tìm kiếm">`
   - Không nên dùng aria-label khi đã có `<label>` vì sẽ bị trùng thông tin
   - Screen reader có thể đọc 2 lần gây rối
   - `<label>` là semantic chuẩn, nên ưu tiên dùng

## Câu A4 (5đ) — Media

1. Giải thích thuộc tính `loading="lazy"` trên thẻ `<img>`. Nó cải thiện gì? Khi nào KHÔNG nên dùng?
2. Tại sao nên cung cấp nhiều `<source>` trong thẻ `<video>`? Liệt kê ít nhất 3 format video web phổ biến.
3. Thuộc tính `alt` trên `<img>` dùng để làm gì? Viết `alt` tốt cho 3 trường hợp:
   - Ảnh sản phẩm iPhone 16
   - Ảnh trang trí (decorative)
   - Ảnh biểu đồ doanh thu Q1/2026

## Trả lời

1. loading="lazy" trên `<img>`

- Là thuộc tính giúp trì hoãn việc tải ảnh cho đến khi ảnh gần xuất hiện trong viewport (màn hình) <br>
  → Trình duyệt chỉ tải khi cần

- Lợi ích:
  - Tăng tốc độ tải trang ban đầu
  - Giảm băng thông
  - Cải thiện hiệu năng (đặc biệt trang có nhiều ảnh như E-Commerce)

- Khi KHÔNG nên dùng:
  - Ảnh quan trọng ở trên cùng (above-the-fold)
  - Ảnh logo, banner chính <br>
    → Vì cần hiển thị ngay, nếu lazy sẽ gây chậm hiển thị

2. Tại sao nên dùng nhiều `<source>` trong `<video>`?

- Vì các trình duyệt hỗ trợ format khác nhau <br>
  → Đảm bảo video chạy được trên mọi trình duyệt

- Nếu 1 format không hỗ trợ → trình duyệt sẽ dùng source khác

- Các format video phổ biến:
  - MP4 (.mp4)
  - WebM (.webm)
  - Ogg (.ogv)

3. Thuộc tính alt trên <img>

- Dùng để:
  - Mô tả nội dung ảnh cho screen reader
  - Hiển thị khi ảnh bị lỗi
  - Hỗ trợ SEO

Ví dụ alt tốt: <br>

- Ảnh sản phẩm iPhone 16: <br>
  alt="iPhone 16 Pro màu titan, mặt trước và sau"

- Ảnh trang trí (decorative): <br>
  alt="" <br>
  → để trống để screen reader bỏ qua

- Ảnh biểu đồ doanh thu Q1/2026: <br>
  alt="Biểu đồ doanh thu quý 1 năm 2026 tăng 20% so với quý trước"

## Câu A5 (5đ) — So sánh `<figure>` vs `<img>`

```html
<!-- Cách 1 -->
<img src="product.jpg" alt="iPhone" />

<!-- Cách 2 -->
<figure>
  <img src="product.jpg" alt="iPhone 16 Pro Max 256GB Titan" />
  <figcaption>iPhone 16 Pro Max — 25.990.000đ</figcaption>
</figure>
```

Khi nào dùng Cách 1, khi nào dùng Cách 2? Cho 2 ví dụ thực tế cho mỗi cách.

## Trả lời

- Dùng `<img>`:
  - Ảnh nhỏ, icon, ảnh không cần mô tả thêm
    Ví dụ:
    ```
    <img src="iphone16.jpg" alt="iPhone">
    <p>iPhone 16 Pro Max — 25.990.000đ</p>
    ```

- Dùng `<figure>`:
  - Ảnh sản phẩm
  - Biểu đồ, hình minh họa có chú thích
  - Nội dung cần giải thích kèm the
    Ví dụ:
    ```
    <figure>
    <img src="product.jpg" alt="iPhone 16 Pro Max 256GB Titan">
    <figcaption>iPhone 16 Pro Max — 25.990.000đ</figcaption>
    </figure>
    ```

# PHẦN B — THỰC HÀNH CODE (55 điểm)

## Bài B1 (20đ) — Form Đăng ký Tài khoản

## Bài B2 (15đ) — Trang Multimedia

## Bài B3 (20đ) — Form Đặt hàng hoàn chỉnh

# PHẦN C — PHÂN TÍCH & SUY LUẬN (20 điểm)

## Câu C1 (10đ) — Debug Form

## Câu C2 (10đ) — Thiết kế chiến lược Validation

# PHẦN D — VIDEO THỰC HÀNH OBS (25 điểm)
