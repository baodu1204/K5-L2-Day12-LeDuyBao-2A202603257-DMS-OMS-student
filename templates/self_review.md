# Tự đánh giá — Lê Duy Bảo · G04

## 1. Tự rà soát 4 cảnh

Nghỉ tay 1 phút, mở lại bài của mình, chọn 4 ảnh (2 S##, 2 D##), đọc như người lạ.

Loại lỗi: `seat_flip`, `wrong_class`, `guess`, `box`, `missing`, `extra`, `lr_flip` (trái/phải mặt), `flag` (thiếu cờ điểm), `ok`.

| Ảnh | Đối tượng | Loại lỗi | Ghi chú | Đã sửa? |
|---|---|---|---|---|
| S01_rgb.png | child_seat | ok | Ghế trẻ em trống nên occupied=no; không nên đổi thành yes chỉ vì có hình khối ghế. Giữ nguyên theo guideline 4.8. | Có |
| S02_ir.png | person / seatbelt | guess | Trong ảnh có thể thấy rõ không có dây an toàn trên người; mine trước đó gán unknown là thận trọng chưa đủ. Peer gán not_worn và được giữ theo guideline 4.7. | Có |
| D01.png | face13 / lip_lower | box | Điểm lip_lower của mình đặt ở vùng ngoài mép môi dưới thay vì mép môi thực. Không có ngoài khung, ngoài mặt hay che khuất thì không bật outside. | Có |
| D02.png | face / gaze_zone | guess | Khác mine giữa road và peer mirror_c; chưa có quy tắc chắc để suy ra hướng nhìn vì hai nhãn đều có thể phù hợp. Mở lại cùng bạn và giữ unknown nếu không xác định được. | Chưa chắc |

## 2. Lỗi mình lặp lại nhiều nhất hôm nay

Lỗi: guess hoặc unknown không nhất quán ở các thuộc tính khó quan sát, nhất là seatbelt và gaze_zone.

Vì sao mình mắc: Dễ đoán theo hình dáng tổng quát hoặc quá thận trọng khi chi tiết IR nhỏ, tối hoặc bị che.

Lần sau tránh bằng cách: Tra guideline trước, dùng tên ảnh và so IR/RGB cùng cảnh khi có; chỉ gán trạng thái rõ ràng, còn lại dùng unknown thay vì suy đoán.

## 3. Ghi chú về disagreement_log

Một dòng bạn của mình đúng và mình sai. Mình học được gì từ dòng đó: Với S02_ir, peer gán person/seatbelt=not_worn trong khi mình gán unknown. Mình học rằng không nhìn thấy dây an toàn trên người trong ảnh IR đủ rõ thì có thể gán not_worn thay vì unknown; đối với trường hợp dây bị che hoặc không nhìn rõ mới giữ unknown.
