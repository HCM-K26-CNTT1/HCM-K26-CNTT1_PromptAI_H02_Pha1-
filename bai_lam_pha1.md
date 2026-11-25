# BÀI LÀM PHA 1 

- **Họ tên:** Nguyễn Trần Đan Linh
- **Lớp:** CNTT1
- **Link repository Pha1:** https://github.com/HCM-K26-CNTT1/HCM-K26-CNTT1_PromptAI_H02_Pha1-.git

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
Bạn là một Kế toán viên có kinh nghiệm 10 năm
Hãy tính tổng tiền cho yêu cầu báo giá dựa trên những thông tin trong <bang_gia></bang_gia>; <quy_tac_tinh_gia></quy_tac_tinh_gia>; <yeu_cau_bao_gia></yeu_cau_bao_gia>
<bang_gia>BẢNG GIÁ VÉ (đồng/người lớn)
SVT – Sân Vận Động: 1.200.000
FZ – Fan Zone: 800.000
VIP – Khán đài VIP: 2.500.000</bang_gia>
<quy_tac_tinh_gia>1. Trẻ em từ 5 đến 11 tuổi tính 70% giá người lớn. Trẻ dưới 5 tuổi miễn phí.
2. Nhóm từ 5 người lớn trở lên được giảm 5% trên tiền vé (tiền người lớn + tiền trẻ em).
3. Phụ thu khu ghế ưu tiên: 300.000 đồng/người. Phụ thu không được giảm giá.
4. Tổng tiền = tiền vé sau giảm + phụ thu.</>quy_tac_tinh_gia>
<yeu_cau_bao_gia>Nhóm cổ động viên đi xem trận bán kết, mua gói SVT, gồm 5 người lớn, 2 trẻ em (8 tuổi và 10 tuổi) và 1 bé 3 tuổi. Có 1 người lớn chọn khu ghế ưu tiên.</yeu_cau_bao_gia>
Các bước thực hiện
Bước 1: đọc thông tin trong <bang_gia></bang_gia>; <quy_tac_tinh_gia></quy_tac_tinh_gia>; <yeu_cau_bao_gia></yeu_cau_bao_gia>
Bước 2: hãy suy nghĩ theo từng bước theo thứ tự tiền người lớn → tiền trẻ em → tiền vé → giảm giá nhóm → phụ thu → tổng tiền; mỗi bước ghi phép tính
Bước 3: Tính ra kết quả: <tổng tiền> đồng
Sử dụng giọng điệu chính xác, minh bạch, chuyên nghiệp
Yêu cầu đầu ra: 
- Có các bước tính toán, mỗi bước ghi phép tính
- Kết quả cuối cùng có dạng: <tổng tiền> đồng

```

## 4.4. Dây chuyền xử lý khiếu nại (Prompt Chaining)

### a) Prompt Trạm 1

**PROMPT**

```text
Đây là EMAIL KHIẾU NẠI CỦA KHÁN GIẢ:
<email>Tôi là khán giả mua vé gói SVT trận Cúp Sao Vàng ngày 02/11/2026, đi 2 người lớn. Ban tổ chức cam kết khu khán đài có mái che nhưng trong 2 hiệp đầu chúng tôi bị xếp sang khu không mái, trời mưa và ghế ướt. Nhân viên soát vé rất nhiệt tình, tôi không có gì phàn nàn về nhân viên. Tôi đề nghị ban tổ chức giải quyết thỏa đáng.</email>

Bạn là một nhân viên xử lý yêu cầu khiếu nại 
Hãy đọc email, trả về chỉ một đối tượng JSON gồm đúng 4 trường:
{"loai_su_co": một trong "tran_gio" | "sai_khu_vuc" | "nhan_vien" | "khac", "so_khach": số nguyên, "so_hiep_bi_anh_huong": số nguyên hoặc null, "tom_tat": "không quá 20 từ"}
Giọng điệu chính xác, minh bạch, rõ ràng
Định dạng đầu ra: 
- Không thêm lời chào xã giao và nội dung như "tôi đã nhận được thông tin, tôi sẽ làm ngay"
- chỉ trả về một đối tượng JSON gồm đúng 4 trường như yêu cầu
- hãy trả về bản tom_tat không quá 20 từ
```

### b) Hai điều cần kiểm tra ở JSON đầu ra của Trạm 1

1. Câu trả lời có trả về một đối tượng JSON gồm đúng 4 trường như yêu cầu không giải thích hay không

2. Phạm vi, độ dài đầu ra có đúng với yêu cầu trả về bản tom_tat không quá 20 từ và nội dung output có đúng với nội dung input không

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
