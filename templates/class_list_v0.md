# Danh sách lớp v0 — <Lê Duy Bảo> · <G04>

## DMS (ít nhất 6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng DMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | face_box | Mỗi khung hình mặt người lái | Xác định vùng cần phân tích mắt, đầu, kính và các hành vi liên quan | Có, nhưng có thể mất/nhạt khi mặt bị che hoặc môi trường tối |
| 2 | eye_left / eye_right | open / closed / unknown | Phát hiện nhắm mắt kéo dài, buồn ngủ hoặc mất cảnh giác | Có, trừ khi mắt bị che, kính phản xạ hoặc độ phân giải thấp |
| 3 | gaze_zone | road / mirror_l / mirror_r / mirror_c / cluster / center / lap / other | Phát hiện tài xế mất tập trung, nhìn lệch đường hoặc dùng thiết bị | Khó; có thể suy ra hướng đầu nhưng trạng thái mắt trên IR chưa chắc |
| 4 | glasses | none / clear / sun | Hiệu chỉnh tầm nhìn mắt; đánh dấu trường hợp phát hiện mắt có thể bị ảnh hưởng | Có, nhưng kính râm và phản xạ có thể che/giả mắt |
| 5 | hand | box | Nhận dạng tay để liên kết với thiết bị, vô-lăng hoặc vùng đầu | Có; khả năng phân biệt bị giảm khi tay mặc trang phục tối |
| 6 | phone | held / mounted / lap | Phát hiện tài xế dùng điện thoại, soạn tin hoặc trò chuyện trên máy | Có với kích thước và góc nhìn đủ tốt; màn hình IR có thể khó phân biệt |
| 7 | camera_blocked | yes / no | Cảnh báo hệ thống không còn quan sát đáng tin cậy và tạm ngừng kết luận DMS | Không trực tiếp; suy ra gián tiếp từ mặt/ảnh bị che hoặc số lượng phát hiện sụt |

## OMS (ít nhất 6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng OMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | person_box | seat: seatbelt | Xác định từng người và ghế đang liên kết để đánh giá trạng thái người | Có, nhưng vị trí ghế có thể bị che bởi người hoặc đồ vật |
| 2 | seat | driver / front_passenger / rear_left / rear_middle / rear_right | Gán người hoặc đồ vật vào vị trí ghế phù hợp và áp dụng quy tắc an toàn | Có gián tiếp qua bố trí khoang xe; ghế sau có thể bị che |
| 3 | seatbelt | worn / not_worn / unknown | Phát hiện người chưa thắt dây an toàn để cảnh báo và kích hoạt quy tắc ghế | Có một phần: dây và khóa có thể thấy, nhưng thắt nếp ghế và góc nhìn có thể làm sai |
| 4 | child_seat | seat / occupied (yes / no / unknown) | Nhận biết ghế trẻ em và có người ngồi trên ghế để cảnh báo/quản lý túi khí | Có nếu khung, quai và hình dáng ghế trẻ em nhìn rõ |
| 5 | infant_seat | seat / facing (rear / front) | Xác định ghế trẻ sơ sinh và hướng; hỗ trợ quy tắc không đặt ghế quay về phía trước | Có qua hình dáng ghế và hướng quay, nhưng góc nhìn IR có thể khó |
| 6 | object_box | seat / type (bag / box / cup / other) | Phân biệt đồ vật với người, tránh báo nhầm và hỗ trợ kiểm tra ghế trống | Có, tùy kích thước, bề mặt và độ che khuất |
| 7 | metadata khung hình | modality / light / camera_id | Chọn xử lý phù hợp với cảm biến, ánh sáng và camera; ghi nhận nguồn dữ liệu | Không phải đối tượng nhìn thấy; là thông tin khai thác từ hệ thống |

## 2 câu hỏi leo thang

Câu hỏi bạn muốn hỏi người viết guideline (hoặc khách hàng) vì guideline v1.0 chưa trả lời. Mỗi câu kèm **tên khung** làm ví dụ.

1. Câu hỏi: Khi ánh sáng IR yếu hoặc người lái đeo kính phản quang, gaze_zone là unknown hay dự đoán theo hướng đầu?
   Khung ví dụ: gaze_zone
   Bạn tạm gán thế nào và vì sao: Tạm gán unknown vì guideline v1.0 chưa quy định ngưỡng tin cậy; chỉ gán hướng cụ thể khi mắt/hướng đầu nhìn được rõ.
2. Câu hỏi: seatbelt chỉ được gán worn khi thấy khóa và toàn bộ dây, hay dây qua vai hoặc khóa là đủ?
   Khung ví dụ: seatbelt
   Bạn tạm gán thế nào và vì sao: Tạm gán worn chỉ khi thấy khóa và ít nhất một phần dây qua vai; nếu bị che chỉ gán unknown để tránh bỏ sót cảnh báo sai.
