# Phiếu QC 1 — Road v1.0

Lô được kiểm (học viên): nguyenkhanhtrinh        Người kiểm (học viên): NguyenThienPhuc  
Ngày: 2026-11-20                                 Phiên bản guideline: Road v1.0  
File được kiểm (tên + `revision` trong manifest): nguyenkhanhtrinh-front.zip, nguyenkhanhtrinh-fisheye.zip (rev 1)  
Số ảnh kiểm: 6 (A01, A02, A04, A09, B01, B08)   Số nhãn đã kiểm (shape + tag): 72  

## Tổng hợp theo mã
| Mã | Loại lỗi | Số mục kiểm | Số lỗi | Mức |
| --- | --- | ---: | ---: | --- |
| QC1-01 tag camera | sai thuộc tính / bỏ sót | 24 | 0 | nặng |
| QC1-02 đủ L1, R1 | bỏ sót | 9 | 0 | nặng |
| QC1-03 position | sai thuộc tính / thừa | 15 | 0 | nặng |
| QC1-04 tâm vạch, chiều, điểm dừng | sai phạm vi / bỏ sót | 15 | 0 | chính |
| QC1-05 vạch đứt, che | sai phạm vi / sai thuộc tính | 15 | 2 | chính |
| QC1-06 style, color, kind | sai thuộc tính | 15 | 0 | chính |
| QC1-07 vùng lái | sai phạm vi / bỏ sót / thừa | 22 | 0 | chính |
| QC1-08 đèn, màu | bỏ sót / sai phạm vi / sai thuộc tính | 6 | 0 | nặng / chính |
| QC1-09 facing, type, group, biển phụ | sai thuộc tính | 11 | 0 | chính |
| QC1-10 hình in, đủ biển | bỏ sót / sai phạm vi | 5 | 0 | chính |
| QC1-11 fisheye | sai phạm vi / sai thuộc tính | 12 | 3 | chính |
| QC1-12 file | lỗi file | 72 | 0 | nhẹ / nặng |

## Danh sách lỗi (mỗi lỗi một dòng)
| # | Mã | Ảnh | Nhãn (label, id) | Mức | Mô tả ngắn |
| --- | --- | --- | --- | --- | --- |
| 1 | QC1-05 | A04 | lane (L1) | chính | 2 polyline cùng position L1: vạch đứt bị tách thành 2 đường riêng |
| 2 | QC1-08 | A04 | traffic_light#3@(552,272) | nhẹ | box thấp hơn 8 px: không bắt buộc gán |
| 3 | QC1-05 | A09 | lane (L2) | chính | 2 polyline cùng position L2: vạch đứt bị tách thành 2 đường riêng |
| 4 | QC1-11 | B01 | road_curb#5@(572,364) | chính | polyline chỉ có 2 điểm: trên fisheye phải vẽ theo cung cong |
| 5 | QC1-11 | B01 | road_curb#6@(1200,640) | chính | polyline chỉ có 3 điểm: trên fisheye phải vẽ theo cung cong |
| 6 | QC1-11 | B08 | lane#4@(213,624) | chính | polyline chỉ có 2 điểm: trên fisheye phải vẽ theo cung cong |
| - | - | A01 | - | - | Ảnh A01 gán đầy đủ, không phát hiện lỗi |
| - | - | A02 | - | - | Ảnh A02 gán đầy đủ, không phát hiện lỗi |

## Ca mơ hồ
| Ảnh | Câu hỏi cho lead | Lời đáp (nếu có) |
| --- | --- | --- |
| A06 | Ảnh A06 bên phải là vỉa hè (đã gán road_curb) không có vạch sơn kẻ đường thì có miễn trừ QC1-02 thiếu R1 không? | Được miễn nếu thực tế không có vạch sơn kẻ đường. |

## Quyết định
Lỗi nặng: 0   Lỗi chính: 5 / 72 nhãn = 6.94 %   Lỗi nhẹ: 1   Ca chờ lead: 0  
Quyết định (Release / Hold / Rework): Rework  
Lý do (theo luật của phiếu): Không có lỗi nặng nhưng tỉ lệ lỗi chính 6.94 % > 5 % → Rework.  

Loại lỗi: bỏ sót = thiếu nhãn phải có; thừa = gán cái không phải đối tượng; sai phạm vi = hình lệch, sai chiều, dừng sai chỗ, tràn vùng. Ba loại này theo cách chia lỗi gán nhãn của ISO/IEC 5259-4 (mục 8.4.2); "sai thuộc tính" và "lỗi file" là khóa học thêm. Cách xếp mức: [thang mức lỗi](../docs/qc_severity_road_v1.0.md).
