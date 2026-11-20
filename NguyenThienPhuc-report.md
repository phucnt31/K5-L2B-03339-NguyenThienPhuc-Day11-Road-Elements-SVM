# Báo cáo cá nhân — Ngày 11
Họ tên: Nguyễn Thiện Phúc          Mã học viên: K5-L2B-03339  
Phiên bản CVAT (Help → About): v2.82.0  
Guideline: Road v1.0    Lần nộp (`revision` trong manifest): 1  
Thời điểm export (ngày giờ trên CVAT): 2026-11-20 13:20:55 UTC    Số lần nộp lại sau Rework: 1  

## 1. Kiểm project
| Mục | Đúng như guideline Road v1.0? | Ghi chú |
| --- | --- | --- |
| 6 label, đúng kiểu | Đúng | Đủ 6 label: lane (polyline), road_curb (polyline), crosswalk (polygon), drivable (polygon), traffic_light (rectangle), traffic_sign (rectangle) |
| Thuộc tính và giá trị | Đúng | Khớp 100% taxonomy Road v1.0 (position, style, color, kind, area_type, facing, group, edge_zone...) |
| 4 tag ảnh | Đúng | Đủ 4 tag: camera, timeofday, weather, source kiểu Tag có thuộc tính select `value` |
Cách kết thúc polyline trên bản CVAT này: Bấm phím **N** (hoặc click chuột vào điểm kết thúc).  
Cách đặt tag ảnh trên bản CVAT này: Chọn công cụ **Tag** ở thanh công cụ bên trái, chọn label tag tương ứng và chọn giá trị trong thuộc tính `value` ở mục Details.  

## 2. Số lượng đã gán
| Task | Ảnh | lane | road_curb | crosswalk | drivable | traffic_light | traffic_sign |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| front | 12 | 29 | 8 | 3 | 26 | 25 | 25 |
| front-extra (đã làm 0 / 4) | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| fisheye | 8 | 6 | 10 | 7 | 8 | 5 | 2 |
| fisheye-extra (đã làm 0 / 4) | 0 | 0 | 0 | 0 | 0 | 0 | 0 |

## 3. Bảng ca khó
| Ảnh | Nhãn | Phân vân giữa | Đã chọn | Lý do |
| --- | --- | --- | --- | --- |
| A05 | lane / road_curb | Vẽ L1, R1 hay vẽ road_curb | Chỉ vẽ `road_curb` và `drivable`, không vẽ lane | Đường thực tế không có vạch sơn kẻ làn, hai bên mép là lề vỉa hè; theo guideline không thấy vạch thì không vẽ bừa (được miễn QC1-02 theo Checkpoints) |
| A06 | lane / road_curb | Vẽ vạch R1 bên phải hay road_curb | Gán `road_curb` mép phải | Mép đường bên phải là vỉa hè sát chân cột, không có vạch kẻ làn sơn trắng/vàng |
| A08 | traffic_sign | Gộp chung biển phụ vào biển chính hay tách box riêng | Tách riêng box phụ group = supplementary | Theo guideline Road v1.0 mục 3: Biển phụ (tấm chữ nhật nhỏ "PASSENGER CARS ONLY") phải có box riêng |
| B01 | road_curb | Vẽ nét thẳng 2 điểm hay uốn cong | Uốn cong theo cung tròn mép ảnh | Quy tắc fisheye yêu cầu vẽ theo cung cong, đặt nhiều điểm ở rìa ngoài |

## 4. Phiếu QC 1 nhận được
Bạn kiểm lô của tôi: Hoàng Hải Đăng    Quyết định nhận được: Rework  
| Mã lỗi | Số lỗi | Đồng ý? | Đã sửa? |
| --- | ---: | --- | --- |
| QC1-03 | 1 | Đồng ý | Đã sửa (kiểm tra lại ảnh A04, xóa/chỉnh lại vạch trùng position R2 để không bị thừa vạch làn) |
| QC1-10 | 5 | Đồng ý | Đã sửa (bổ sung các biển báo còn thiếu: biển chỉ dẫn xanh ở xa A01, 2 biển cảnh báo ở A03, biển cam dưới gầm cầu ở A06, và biển phụ PASSENGER CARS ONLY ở A08) |

## 5. Kiểm file export
| File | Mở lại được? | Số shape ảnh 1 (job / file) | Số shape ảnh 2 (job / file) | Tag camera có trong XML? |
| --- | --- | --- | --- | --- |
| NguyenThienPhuc-front.zip | Có (road_check lint pass) | 8 / 8 (A01) | 8 / 8 (A02) | Có (`camera = front`) |
| NguyenThienPhuc-fisheye.zip | Có (road_check lint pass) | 3 / 3 (B01) | 6 / 6 (B02) | Có (`camera = fisheye_front`) |

## 6. Ảnh chụp màn hình
*(Dán ảnh chụp màn hình tương ứng vào đây trước khi nộp)*
1. Tab Labels của project (hiển thị đủ 6 label và 4 tag).
2. Một ảnh camera trước đã gán đủ (làn, vùng lái, đèn/biển, ví dụ A01 hoặc A04).
3. Một ảnh fisheye đã gán, phóng to đoạn polyline cong (ví dụ B01 hoặc B08).
4. Một đoạn XML mở từ annotations.xml có `<polyline label="lane">`.

## 7. Tự đánh giá
Lỗi bạn mắc nhiều nhất hôm nay (theo mã QC1-xx), và cách tránh ở Ngày 20:  
- Lỗi mắc nhiều nhất là **QC1-10 (bỏ sót biển báo nhỏ ở xa hoặc biển phụ)** và **QC1-02 (chưa bao quát đủ vạch L1/R1 khi gặp lề đường)**.
- Cách tránh ở Ngày 20: Quét ảnh kỹ hơn từ xa tới gần, chú ý các biển báo trên giá long môn / gầm cầu và luôn tách box cho biển phụ chữ nhật đi kèm biển chính; đối với làn đường, chủ động kiểm tra kỹ xem có vạch mờ hay mép lề curb để gán đúng thuộc tính ngay từ đầu.

Nhãn của bạn đi vào model ở đâu? Chọn một lỗi đã sửa và nói nó làm model học sai thế nào:  
- Lỗi **QC1-10 (bỏ sót biển phụ "PASSENGER CARS ONLY" ở ảnh A08)** đi vào mô hình phát hiện đối tượng (Object Detection / Traffic Sign Detection). Nếu bỏ sót, vùng ảnh chứa biển phụ sẽ bị coi là nền (background), khiến mô hình học tính năng sai, làm hệ thống tự hành bỏ qua biển quy định loại phương tiện được phép lưu thông, dẫn đến xe tự hành có nguy cơ đi vào làn cấm hoặc không tuân thủ biển hiệu lệnh.

## 8. (Tùy chọn, buffer) Từ polyline đến đích row-anchor
| y | 720 | 680 | 640 | 600 | 560 |
| --- | ---: | ---: | ---: | ---: | ---: |
| x của chúng tôi | 586 | 592 | 598 | 605 | 612 |
| x của bạn kia | 584 | 590 | 597 | 606 | 615 |

Trả lời 3 câu:

1. **Năm số x đó chính là đích mà một model row-anchor học cho vạch này. Nếu bạn dừng polyline sớm 40 px, hàng nào đổi thành "không có làn"?**  
   - Hàng `y = 560` (hàng xa xe nhất tương ứng với phần trên của ảnh) sẽ bị đổi thành "không có làn" (no lane), do polyline bị cắt ngắn không vươn tới tọa độ y đó.

2. **So với bạn được kiểm (cùng ảnh): ở hàng 720 và hàng 560, hai bạn lệch nhau bao nhiêu pixel? Lệch ở hàng nào ảnh hưởng LKA nhiều hơn (slide 25)?**  
   - Ở hàng 720 lệch $|586 - 584| = 2$ px; ở hàng 560 lệch $|612 - 615| = 3$ px.  
   - Lệch ở **hàng 720** (sát đầu xe) ảnh hưởng đến hệ thống giữ làn (LKA) nhiều hơn, vì vị trí sát xe quyết định trực tiếp sai số góc đánh lái và độ lệch làn tức thời (lateral offset), dễ gây giật vô lăng.

3. **Nếu polyline vẽ từ xa về gần (ngược quy tắc 2), cách tính trên có đổi không? Script nào sẽ gặp khó?**  
   - Bản chất tọa độ hình học cắt các hàng y không đổi, nhưng thứ tự mảng điểm bị đảo ngược.  
   - Các script nội suy điểm (interpolation), script tính hướng vector vạch làn, và mô hình row-anchor (vốn giả định điểm bắt đầu từ sát xe đi ra xa) sẽ gặp khó khăn hoặc nội suy sai thứ tự chỉ số điểm.
