# BÀI LÀM PHA 1 

- **Họ tên:**
- **Lớp:**
- **Link repository Pha1:**

> Pha 1 (70 phút đầu, KHÔNG dùng AI). Viết xong, kéo thả file này vào repository Pha1 trước mốc giờ giám thị công bố.

## 4.1. Bảo vệ dữ liệu và chống ảo giác

### a) Ghi chú đã ẩn danh hoá

**GHI CHU DA AN DANH**

```text
Khán giả [tên khán giả], số điện thoại [+84], số CCCD [số cccd], email [địa chỉ email], đặt 3  vé gói SVT trận bán kết Cúp Sao Vàng ngày 18/12/2026 cho 2 người lớn và 1 trẻ em 9 tuổi. Khán giả đã chuyển khoản đặt cọc 1.500.000 đồng. Khán giả yêu cầu 3 ghế ngồi cạnh nhau gần lối đi.
```

### b) Hai câu lệnh chống ảo giác

**CAU LENH**

```text
1. Câu lệnh 1: 
Bạn là nhân viên bán vé có kinh nghiệm lâu năm
Hãy soạn email xác nhận đặt vé dựa trên nội dung Khán giả [tên khán giả], số điện thoại [+84], số CCCD [số cccd], email [địa chỉ email], đặt 3  vé gói SVT trận bán kết Cúp Sao Vàng ngày 18/12/2026 cho 2 người lớn và 1 trẻ em 9 tuổi. Khán giả đã chuyển khoản đặt cọc 1.500.000 đồng. Khán giả yêu cầu 3 ghế ngồi cạnh nhau gần lối đi.
Lưu ý: 
- Chỉ trả lời dựa trên nội dung
- Nếu thiếu thông tin để soạn email, hãy ghi [không đủ thông tin để thực hiện]
- Không tự bịa đặt thông tin ngoài file
Các bước làm: 
- Bước 1: đọc và phân tích dữ liệu
- Bước 2: lấy dữ liệu và viết nội dung email xác nhận đặt vé
Sử dụng giọng điệu: chuyên nghiệp, tôn trọng khách hàng
Yêu cầu đầu ra: 
- Cấu trúc email hoàn chỉnh từ lời chào đến cảm ơn quý khách
- Không thêm lời chào hỏi xã giao của AI
- Không thêm nội dung như "tôi đã nhận được thông tin, tôi sẽ làm ngay"

2. Câu lệnh 2: 
Bạn là nhân viên bán vé có kinh nghiệm lâu năm
Dựa trên file chính sách hoàn/huỷ vé hãy cho tôi biết Khán giả huỷ vé trước sự kiện 4 ngày thì được hoàn bao nhiêu tiền?
Bước 1: đọc và phân tích file
Bước 2: lấy dữ liệu trong file đã đọc và trả lời câu hỏi Khán giả huỷ vé trước sự kiện 4 ngày thì được hoàn bao nhiêu tiền?
Yêu cầu đầu ra:
- Không thêm nội dung như "tôi đã nhận được thông tin, tôi sẽ làm ngay"
- Nếu thiếu thông tin, hãy ghi [không đủ thông tin để thực hiện]. Không tự bịa đặt thông tin ngoài file.
- Khi trả lời, hãy ghi rõ câu trả lời lấy từ mục hoặc điều khoản nào trong file.

```

## 4.2. Trích xuất tin nhắn đặt vé ra JSON

**PROMPT**

```text
C - Context: Bạn là một kỹ sư công nghệ thông tin có nhiều kinh nghiệm 
R - Request: Trích xuất tin nhắn đặt vé TN1, TN2, TN3 thành một mảng JSON 3 đối tượng, đúng thứ tự.
E - Explanation: Nêu đủ 5 quy tắc chuẩn hoá 
1. ma_goi lấy theo bảng mã gói.
2. ngay_su_kien dạng YYYY-MM-DD; tin nhắn không ghi năm thì lấy năm 2026; không có ngày cụ thể thì null.
3. Khách không nhắc trẻ em thì tre_em là 0 và mọi khách là người lớn.
4. loai_ve chỉ nhận "thuong", "vip" hoặc null.
5. ghi_chu chỉ ghi yêu cầu đặc biệt về chỗ ngồi, hỗ trợ di chuyển hoặc ăn uống; không có thì null.
A - Action: 
- Bước 1: Đọc thông tin ba tin nhắn sau 
<tin_nhan>TN1: Mình muốn đặt gói Sân Vận Động trận tứ kết ngày 20/12 nha, 2 người lớn với 1 bé 8 tuổi, vé thường.</tin_nhan>
<tin_nhan>TN2: Cho 3 người đi Fan Zone trận ngày 05/01/2027 ạ. Một người cần hỗ trợ xe lăn.
</tin_nhan>
<tin_nhan>TN3: Trận chung kết Cúp Sao Vàng tháng 12 còn vé không ạ? Nhà em 4 người lớn, có một người khiếm thị cần hỗ trợ tìm chỗ, lấy vé VIP.
</tin_nhan>
- Bước 2: Trích xuất tin nhắn đặt vé TN1, TN2, TN3 thành một mảng JSON 3 đối tượng, đúng thứ tự, đầy đủ 5 quy tắc chuẩn hóa
<vi_du>Tin nhắn mẫu 1:
Đặt giúp mình 2 vé VIP trận chung kết ngày 15/11/2026, 2 người lớn và 1 bé. Cần chỗ ngồi cạnh lối đi.
Kết quả đúng:
{"ma_goi": "VIP", "ngay_su_kien": "2026-11-15", "nguoi_lon": 2, "tre_em": 1, "loai_ve": "vip", "ghi_chu": "chỗ ngồi cạnh lối đi"}
</vi_du>
<vi_du>Tin nhắn mẫu 2:
Cho mình một vé Fan Zone, ngày nào cũng được, mình đi một mình.
Kết quả đúng:
{"ma_goi": "FZ", "ngay_su_kien": null, "nguoi_lon": 1, "tre_em": 0, "loai_ve": "thuong", "ghi_chu": null}
</vi_du>
T - Tone: Chuyên nghiệp, rõ ràng.
E - Extras:
- Chỉ trả về JSON, không chào hỏi, không giải thích khi trả lời
- Xuất tin nhắn đặt vé TN1, TN2, TN3 thành một mảng JSON 3 đối tượng, đúng thứ tự, đầy đủ 5 quy tắc chuẩn hóa

```

## 4.3. Báo giá vé bằng Chain-of-Thought

### a) Prompt

**PROMPT**

```text
(Viết prompt vào đây – xoá dòng này)
```

## 4.4. Dây chuyền xử lý khiếu nại (Prompt Chaining)

### a) Prompt Trạm 1

**PROMPT**

```text
(Viết prompt vào đây – xoá dòng này)
```

### b) Hai điều cần kiểm tra ở JSON đầu ra của Trạm 1

1. (Viết câu trả lời vào đây – xoá dòng này)

2.

### c) Câu lệnh viết tiếp

**CAU LENH**

```text
(Viết câu lệnh vào đây – xoá dòng này)
```

## 4.5. Prompt chấm bài theo Rubric

**PROMPT**

```text
(Viết prompt vào đây – xoá dòng này)
```

## 4.6. Hoàn thiện System Prompt

> Phần Vai trò và Chuẩn đầu ra đã cho sẵn. Viết tiếp phần Quy tắc ràng buộc và Xử lý ngoại lệ.

```text
[Vai trò]
Bạn là "Trợ lý Cúp Sao Vàng", nhân viên tư vấn vé và dịch vụ trên website của giải bóng đá Cúp Sao Vàng, giúp khán giả chọn và đặt một trong 3 gói: SVT (Sân Vận Động – vé trận đấu), FZ (Fan Zone – khu cổ vũ), VIP (Khán đài VIP).

[Quy tắc ràng buộc]
1. (Viết quy tắc 1 – xoá dòng này)
2.
3.

[Chuẩn đầu ra]
Trả lời bằng tiếng Việt, lịch sự, tối đa 120 từ. Giá vé trình bày dạng gạch đầu dòng. Kết thúc bằng một câu hỏi về nhu cầu tiếp theo của khách.

[Xử lý ngoại lệ]
- Khách hỏi ngoài phạm vi: (Viết cách trả lời – xoá dòng này)
- Khách cung cấp thiếu thông tin:
```
