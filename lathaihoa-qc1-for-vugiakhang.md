# Phiếu QC 1 — Road v1.0

Lô được kiểm (học viên): Vũ Gia Khang (`vugiakhang`)        Người kiểm (học viên): La Thái Hòa (`lathaihoa`)  
Ngày: 2026-11-21                          Phiên bản guideline: Road v1.0  
File được kiểm (tên + `revision` trong manifest): `vugiakhang-front.zip`, `vugiakhang-fisheye.zip` (bản nộp 1 — chưa kèm manifest)  
Số ảnh kiểm: 6 (`A01`, `A04`, `A10`, `B01`, `B02`, `B08`; + 0 ảnh thêm, ghi riêng)   Số nhãn đã kiểm (shape + tag): 68 (44 shape + 24 tag)  

*(Ghi chú chọn mẫu kiểm: 3 ảnh camera trước `A01`, `A04`, `A10` và 3 ảnh fisheye `B01`, `B02`, `B08` — trong đó **`B01` là ảnh không có lỗi**. Toàn bộ 24 ảnh trong 2 file zip đều mở lại được bằng `road_check lint`, không kèm ảnh gốc `contains_images: false`.)*

## Tổng hợp theo mã
| Mã | Loại lỗi | Số mục kiểm | Số lỗi | Mức |
| --- | --- | ---: | ---: | --- |
| QC1-01 tag camera | sai thuộc tính / bỏ sót | 24 | 1 | nặng *(1 nhẹ: tag `weather`)* |
| QC1-02 đủ L1, R1 | bỏ sót | 6 | 0 | nặng |
| QC1-03 position | sai thuộc tính / thừa | 11 | 3 | nặng |
| QC1-04 tâm vạch, chiều, điểm dừng | sai phạm vi / bỏ sót | 11 | 0 | chính |
| QC1-05 vạch đứt, che | sai phạm vi / sai thuộc tính | 11 | 0 | chính |
| QC1-06 style, color, kind | sai thuộc tính | 11 | 3 | chính |
| QC1-07 vùng lái | sai phạm vi / bỏ sót / thừa | 26 | 2 | chính |
| QC1-08 đèn, màu | bỏ sót / sai phạm vi / sai thuộc tính | 5 | 5 | nặng / chính *(4 nặng, 1 chính)* |
| QC1-09 facing, type, group, biển phụ | sai thuộc tính | 7 | 2 | chính |
| QC1-10 hình in, đủ biển | bỏ sót / sai phạm vi | 2 | 1 | chính |
| QC1-11 fisheye | sai phạm vi / sai thuộc tính | 18 | 0 | chính |
| QC1-12 file | lỗi file | 68 | 0 | nhẹ / nặng |

## Danh sách lỗi (mỗi lỗi một dòng)
| # | Mã | Ảnh | Nhãn (label, id) | Mức | Mô tả ngắn |
| --- | --- | --- | --- | --- | --- |
| 1 | QC1-06 | A01 | `lane#1@(0,600)` | chính | Vạch trắng đôi bên trái (`L2`) nhưng gán `kind=single` (đúng là `double`). |
| 2 | QC1-06 | A01 | `lane#2@(1279,708)` | chính | Vạch liền mép phải (`R2`) thực tế màu vàng nhưng gán `color=white` (đúng là `yellow`). |
| 3 | QC1-09 | A01 | `traffic_sign#3@(551,408)` | chính | Biển chỉ dẫn cao tốc nền xanh lá nhưng gán `group=prohibitory` (đúng là `information`). |
| 4 | QC1-07 | A04 | `drivable#3@(1278,554)` | chính | Làn song song bên phải làn đang đi nhưng vẫn để `area_type=direct` (đúng là `alternative`). |
| 5 | QC1-08 | A04 | `traffic_light#7@(552,267)` | nặng | Đèn `facing=front` đang sáng màu xanh lá (`green`) nhưng gán nhầm `color=red`. |
| 6 | QC1-08 | A04 | `traffic_light#8@(599,272)` | nặng | Đèn `facing=front` đang sáng màu xanh lá (`green`) nhưng gán nhầm `color=red`. |
| 7 | QC1-01 | A10 | `tag:weather` | nhẹ | Mặt đường ướt rõ và có giọt nước mưa trên kính lái nhưng để `weather=clear` (đúng là `rain`). |
| 8 | QC1-03 | A10 | `lane#0@(437,604)` | nặng | Vạch sát bên trái làn xe đang đi nhưng gán ngược `position=R1` (đúng là `L1`). |
| 9 | QC1-03 | A10 | `lane#1@(86,654)` | nặng | Vạch ngoài cùng bên trái nhưng gán ngược `position=R2` (đúng là `L2`). |
| 10 | QC1-03 | A10 | `lane#2@(1186,665)` | nặng | Vạch sát bên phải làn xe đang đi nhưng gán ngược `position=L1` (đúng là `R1`). |
| 11 | QC1-10 | A10 | `traffic_sign` (cột bên trái ảnh) | chính | Bỏ sót cụm biển cấm đỗ (`NO PARKING / NO STANDING`) kích thước lớn ở cột bên trái (cao > 100 px ≥ 8 px). |
| 12 | QC1-08 | B02 | `traffic_light#6@(105,113)` | nặng | Đèn `facing=front` góc trên-trái đang tắt (`off`) nhưng để mặc định `color=red`. |
| 13 | QC1-08 | B02 | `traffic_light#7@(1077,72)` | nặng | Đèn `facing=front` góc trên-phải đang sáng biểu tượng người đi bộ màu xanh lá (`green`) nhưng gán nhầm `color=red`. |
| 14 | QC1-09 | B02 | `traffic_light#7@(1077,72)` | chính | Cụm đèn góc trên-phải là đèn người đi bộ (`type=pedestrian`) nhưng gán `type=vehicle`. |
| 15 | QC1-08 | B02 | `traffic_light` (cột giữa-phải `(878,285)`) | chính | Bỏ sót cụm đèn giao thông xe cơ giới đang sáng đỏ phía trước (cao ~29 px ≥ 8 px). |
| 16 | QC1-07 | B08 | `drivable` (toàn ảnh) | chính | Bỏ sót hoàn toàn polygon `drivable` trên ảnh `B08` (bảng kế hoạch ảnh `B08` yêu cầu `drivable + lane`). |
| 17 | QC1-06 | B08 | `lane#2@(215,616)` | chính | Vạch trắng phân làn thực tế là vạch đứt (`style=dashed`) nhưng gán `style=solid`. |

*(Ảnh **`B01`** (`B01_02688_FV.png`, 5 shape + 4 tag = 9 nhãn): **Không có lỗi** — đủ 4 tag đúng `camera=fisheye_front`, `crosswalk#0`, `drivable#3`, `road_curb#1/#2/#4` bám sát cung fisheye và cắt gọn sát thân xe.)*

## Ca mơ hồ
| Ảnh | Câu hỏi cho lead | Lời đáp (nếu có) |
| --- | --- | --- |
| A04 | Trời có mây sáng phủ rộng nhưng mặt đường khô: `weather=clear` có chấp nhận được không hay bắt buộc `overcast`? *(Không tính lỗi và không ảnh hưởng quyết định Rework.)* | |

## Quyết định
Lỗi nặng: 7   Lỗi chính: 9 / 68 nhãn = 13,2 %   Lỗi nhẹ: 1   Ca chờ lead: 0  
Quyết định (Release / Hold / Rework): **Rework**  
Lý do (theo luật của phiếu): Có **7 lỗi nặng** (`≥ 1` lỗi nặng là đủ `Rework`: đảo ngược `position` L/R trên `A10` và gán nhầm màu đèn `facing=front` thành `red` trên `A04`, `B02`), đồng thời tỉ lệ lỗi chính đạt **13,2 %** (`9 / 68` nhãn đã kiểm, vượt ngưỡng `5 %`) → **Rework**.

Loại lỗi: bỏ sót = thiếu nhãn phải có; thừa = gán cái không phải đối tượng; sai phạm vi = hình lệch, sai chiều, dừng sai chỗ, tràn vùng. Ba loại này theo cách chia lỗi gán nhãn của ISO/IEC 5259-4 (mục 8.4.2); "sai thuộc tính" và "lỗi file" là khóa học thêm. Cách xếp mức: [thang mức lỗi](docs/qc_severity_road_v1.0.md).
