# Phiếu QC 1 — Road v1.0

Lô được kiểm (học viên): Nguyễn Tiến Thịnh (2A202603354, thinhnt)        Người kiểm (học viên): Nguyễn Đức Hạnh (2A202603344)
Ngày: 2026-11-21                          Phiên bản guideline: Road v1.0
File được kiểm (tên + `revision` trong manifest): `NguyenTienThinh-front.zip`, `NguyenTienThinh-fisheye.zip` (không kèm manifest; revision không có)
Số ảnh kiểm: 6 (A01, A04, A05, A08, B02, B05) (+ 0 ảnh thêm; file không có A13–A16, B09–B12)   Số nhãn đã kiểm (shape + tag): 74

Mẫu 6 ảnh. Không chấm các ảnh ngoài mẫu. Mẫu số 74 = 50 shape trong mẫu + 24 tag (4 tag × 6 ảnh). Bản front kiểm lại là file 11:06. File fisheye không đổi.

## Tổng hợp theo mã
| Mã | Loại lỗi | Số mục kiểm | Số lỗi | Mức |
| --- | --- | ---: | ---: | --- |
| QC1-01 tag camera | sai thuộc tính / bỏ sót | 24 | 0 | nặng |
| QC1-02 đủ L1, R1 | bỏ sót | 8 | 0 | nặng |
| QC1-03 position | sai thuộc tính / thừa | 13 | 0 | nặng |
| QC1-04 tâm vạch, chiều, điểm dừng | sai phạm vi / bỏ sót | 13 | 0 | chính |
| QC1-05 vạch đứt, che | sai phạm vi / sai thuộc tính | 13 | 0 | chính |
| QC1-06 style, color, kind | sai thuộc tính | 13 | 0 | chính |
| QC1-07 vùng lái | sai phạm vi / bỏ sót / thừa | 15 | 3 | chính |
| QC1-08 đèn, màu | bỏ sót / sai phạm vi / sai thuộc tính | 8 | 1 | chính |
| QC1-09 facing, type, group, biển phụ | sai thuộc tính | 21 | 0 | chính |
| QC1-10 hình in, đủ biển | bỏ sót / sai phạm vi | 14 | 1 | chính |
| QC1-11 fisheye | sai phạm vi / sai thuộc tính | 7 | 0 | chính |
| QC1-12 file | lỗi file | 50 | 0 | nhẹ |

Sáu ảnh trong mẫu đều đủ bốn tag. Camera front là `front`; B02 là `fisheye_front`; B05 là `fisheye_left`. QC1-02: A01, A04, A08 có L1 và R1. A05 không có vạch sơn nên không tính thiếu L1/R1. QC1-03 đến QC1-06: 13 lane trong mẫu. A04 còn một polyline L1, `color=yellow`, `kind=double`. A08 còn một L1; vạch xa hơn là L2 và `other`. QC1-07: 13 polygon drivable cộng 2 mép lề đã nhìn (A05, B05). QC1-08: 7 box đèn trong mẫu cộng cụm đèn phải của B02. Hai đèn A04 hướng về xe đã là `color=green`. QC1-12: 50 shape, không còn điểm click trùng trong mẫu; hai file đều mở được.

## Danh sách lỗi (mỗi lỗi một dòng)
| # | Mã | Ảnh | Nhãn (label, id) | Mức | Mô tả ngắn |
| --- | --- | --- | --- | --- | --- |
| 1 | QC1-07 | A05 | road_curb | chính | Mép vỉa phải nhìn thấy, không có polyline `road_curb`. |
| 2 | QC1-10 | A08 | traffic_sign | chính | Biển xanh Harlem River Dr đã có hộp information `(752,63)–(880,125)`. Thiếu tấm "PASSENGER CARS ONLY" phía trên, `group=supplementary`. |
| 3 | QC1-08 | B02 | traffic_light | chính | Chỉ box đèn trái. Cụm đèn góc trên bên phải không có box. |
| 4 | QC1-07 | B05 | drivable#2 alternative | chính | Vùng alternative phủ lên vỉa hè bên phải, không phải mặt đường. |
| 5 | QC1-07 | B05 | road_curb | chính | Mép đường và vỉa thấy được, chưa có polyline `road_curb`. |

## Ca mơ hồ
| Ảnh | Câu hỏi cho lead | Lời đáp (nếu có) |
| --- | --- | --- |
| A05 | Lint báo thiếu L1/R1. Trên ảnh chỉ thấy xe đỗ và lề, không thấy vạch sơn dọc. | Không tính QC1-02. |
| B05 | lane#3 màu vàng, `position=other`, nằm sát mép. Đó là vạch làn hay curb vẽ thành lane? | Chưa kết luận, không đưa vào bảng lỗi. Nếu bỏ lỗi 5 vì trùng câu này, còn 4 / 74 = 5.4 %, vẫn trên 5 %. |
| A08 | Nhiều box `group=prohibitory` rất nhỏ. Chưa tách được biển thật với đèn hoặc chữ trên nhà. | Không tính từng box. |

## Quyết định
Lỗi nặng: 0    Lỗi chính: 5 / 74 nhãn = 6.8 %    Lỗi nhẹ: 0    Ca chờ lead: 1
Quyết định (Release / Hold / Rework): Rework
Lý do (theo luật của phiếu): Không còn lỗi nặng. Tỉ lệ lỗi chính 6.8 % vẫn lớn hơn 5 %. Ca chờ lead ở B05 không kéo tỉ lệ xuống mức 5 % trở lại, nên không chọn Hold.

Loại lỗi: bỏ sót = thiếu nhãn phải có; thừa = gán cái không phải đối tượng; sai phạm vi = hình lệch, sai chiều, dừng sai chỗ, tràn vùng. Ba loại này theo cách chia lỗi gán nhãn của ISO/IEC 5259-4 (mục 8.4.2); "sai thuộc tính" và "lỗi file" là khóa học thêm. Cách xếp mức: [thang mức lỗi](docs/qc_severity_road_v1.0.md).
