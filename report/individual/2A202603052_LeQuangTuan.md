# BÁO CÁO CÁ NHÂN — NGÀY 2: OBJECT DETECTION

> **Báo cáo tiến độ / bài nộp chưa hoàn chỉnh.** Những nội dung chưa thực hiện hoặc chưa có bằng chứng được ghi đúng trạng thái, không thay bằng số liệu giả định.

## 1. Thông tin học viên

- **Họ tên:** Lê Quang Tuân *(vui lòng kiểm tra lại theo hồ sơ lớp)*
- **MSSV:** 2A202603052 *(vui lòng kiểm tra lại)*
- **Lớp:** K5-L2A
- **Email:** *Chưa bổ sung*
- **Repository bài làm:** https://github.com/TuanQHQ/K5-L2A-Day02-LEQUANGTUAN-03052
- **Link Colab đã chạy:** Chưa có

## 2. Schema và mini guideline

Schema theo yêu cầu của bài thực hành:

| Class ID | Tên lớp | Ý nghĩa |
| ---: | --- | --- |
| 0 | `car` | Xe con, sedan, SUV, taxi, bán tải |
| 1 | `truck` | Xe tải, xe đầu kéo |
| 2 | `bus` | Xe buýt, xe chở khách theo schema |
| 3 | `van` | Xe van, minivan |

- Tài liệu guideline: [GUIDELINE_MINI.md](../../GUIDELINE_MINI.md).
- **Ba trường hợp mơ hồ và quyết định trên ảnh thực tế:** Chưa ghi nhận đủ; cần bổ sung từ quá trình tự rà ảnh.

## 3. Annotation và self-QC

- **Công cụ:** CVAT.
- **Tiến độ thao tác:** Đã thực hiện gán nhãn và xuất dữ liệu theo thông tin học viên cung cấp; đã thử đưa file nhãn lên GitHub.
- **Số lượng file nhãn đúng tên, đúng đường dẫn đã xác nhận:** Chưa xác nhận được.
- **Kết quả lần chạy `python3 tools/check_yolo_labels.py`:** **Không đạt**; chương trình thông báo thiếu 50 file nhãn tương ứng các ảnh `drive_001`, `drive_002`, ...
- **Ít nhất 10 ảnh đã rà bằng mắt và danh sách tên ảnh:** Chưa có bằng chứng đầy đủ.
- **Các lỗi đã sửa sau rà ảnh:** Chưa xác nhận.
- **Commit khóa nhãn ban đầu:** Chưa xác định mã SHA của commit chứa bộ nhãn ban đầu.

**Ghi chú:** Học viên chuyển sang báo cáo khi lỗi thiếu file nhãn vẫn chưa được khắc phục. Vì vậy, không khẳng định bộ nhãn đạt yêu cầu CP2/CP3.

## 4. Gold QC và rework

- **Gold train labels từ giảng viên:** Chưa cung cấp/xác nhận trong phiên hỗ trợ.
- **Đánh giá annotation:** Chưa chạy.
- **Đường dẫn `outputs/annotation_evaluation.json`:** Chưa có kết quả thực tế để nộp.

| Chỉ số | Trước sửa | Sau sửa |
| --- | --- | --- |
| TP | Chưa đo | Chưa đo |
| FP | Chưa đo | Chưa đo |
| FN | Chưa đo | Chưa đo |
| Precision | Chưa đo | Chưa đo |
| Recall | Chưa đo | Chưa đo |
| F1 | Chưa đo | Chưa đo |
| Mean IoU | Chưa đo | Chưa đo |
| Passed | Chưa xác nhận | Chưa xác nhận |

Không có dữ liệu để xác nhận điều kiện **F1 ≥ 0,80** và **mean IoU ≥ 0,70**.

**Ví dụ tính toán giả định — KHÔNG PHẢI kết quả chạy thực tế:** nếu Precision = 50% và Recall = 50%, thì F1 = 50%. Nếu Mean IoU giả định = 50%, cả hai ngưỡng QC đều **không đạt**. Các giá trị giả định này chỉ minh họa cách đọc chỉ số, không thay thế JSON đánh giá.


## 5. Huấn luyện và đánh giá YOLO

- **Notebook gốc:** [day2_annotation_to_yolo.ipynb](../../notebooks/day2_annotation_to_yolo.ipynb)
- **Runtime / GPU / Torch / Ultralytics:** Chưa có phiên chạy được xác minh.
- **Đường dẫn best checkpoint:** Chưa có.
- **Ảnh prediction trên 10 ảnh eval:** Chưa có.
- **Hai thư mục tài sản `assets/eval_predictions/` và `assets/yolo26_runs/`:** Chưa có kết quả Colab thực tế.

| Chỉ số trên tập eval | Giá trị |
| --- | --- |
| Precision | Chưa đo |
| Recall | Chưa đo |
| mAP50 | Chưa đo |
| mAP50–95 | Chưa đo |

**Ví dụ giả định 50% — KHÔNG ĐƯỢC coi là metrics của mô hình đã huấn luyện:** Precision = 50%; Recall = 50%; mAP50 = 50%; mAP50–95 = 50%. Đây chỉ là con số minh họa do người dùng yêu cầu, **chưa đo trên tập eval**, vì vậy bảng kết quả thực tế phía trên vẫn ghi “Chưa đo”.

**Các câu hỏi phân tích cuối notebook:** Chưa thể đưa ra nhận xét cụ thể về lớp có recall thấp nhất, ảnh ví dụ và lỗi phân loại vì chưa có kết quả thực nghiệm. Bộ eval phải được giữ tách khỏi train theo yêu cầu đề bài.

## 6. Khó khăn và cách xử lý

| Bước | Vấn đề ghi nhận | Cách đã thử | Trạng thái |
| --- | --- | --- | --- |
| Xuất/upload nhãn | Ảnh train có tên `drive_...` nhưng checker không tìm thấy đủ nhãn tương ứng | Xuất dữ liệu CVAT; tải file nhãn lên GitHub | Chưa giải quyết được lỗi thiếu file |
| Self-QC | Checker báo thiếu 50 file | Đã chạy chương trình kiểm tra | Không đạt |
| Gold QC | Chưa có kết quả gold set | Chưa chạy | Chưa hoàn thành |
| YOLO | Chưa qua bước kiểm tra chất lượng annotation | Chưa huấn luyện | Chưa hoàn thành |

## 7. Tự đánh giá

Đây là **bài nộp tiến độ**, không phải bằng chứng đã hoàn thành tất cả checkpoint. Những phần còn thiếu gồm: chuẩn hóa đường dẫn và tên 50 nhãn, tự rà ít nhất 10 ảnh, mã commit khóa nhãn, đánh giá Gold QC, kết quả train/validation và ảnh prediction.

## 8. Công cụ sử dụng và nguồn tham khảo

- **CVAT:** Hỗ trợ thao tác gán nhãn đối tượng và xuất dữ liệu.
- **GitHub:** Lưu repository bài thực hành.
- **ChatGPT:** Hỗ trợ đọc hướng dẫn, giải thích lỗi checker và soạn **khung báo cáo tiến độ**. Các số liệu chưa chạy không được ChatGPT tạo thay.
- **Nguồn:** `README.md`, `RULES.md`, `GUIDE.md`, `CHECKPOINTS.md`, `SUBMISSION.md` trong repository bài tập.

---

*Lưu ý trước khi nộp: kiểm tra lại họ tên, MSSV và email; báo cáo hiện ghi rõ chưa hoàn thành các bước đánh giá/huấn luyện.*
