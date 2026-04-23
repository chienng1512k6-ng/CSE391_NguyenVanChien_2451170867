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

## Câu A4 (5đ) — Media

1. Giải thích thuộc tính `loading="lazy"` trên thẻ `<img>`. Nó cải thiện gì? Khi nào KHÔNG nên dùng?
2. Tại sao nên cung cấp nhiều `<source>` trong thẻ `<video>`? Liệt kê ít nhất 3 format video web phổ biến.
3. Thuộc tính `alt` trên `<img>` dùng để làm gì? Viết `alt` tốt cho 3 trường hợp:
   - Ảnh sản phẩm iPhone 16
   - Ảnh trang trí (decorative)
   - Ảnh biểu đồ doanh thu Q1/2026

## Trả lời

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

---

## Trả lời

# PHẦN B — THỰC HÀNH CODE (55 điểm)

## Bài B1 (20đ) — Form Đăng ký Tài khoản

## Bài B2 (15đ) — Trang Multimedia

## Bài B3 (20đ) — Form Đặt hàng hoàn chỉnh

# PHẦN C — PHÂN TÍCH & SUY LUẬN (20 điểm)

## Câu C1 (10đ) — Debug Form

## Câu C2 (10đ) — Thiết kế chiến lược Validation

# PHẦN D — VIDEO THỰC HÀNH OBS (25 điểm)
