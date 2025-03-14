# 📜  Rules Tổng Hợp
## 🔹 0. Lúc nào cũng phải nói chuyện bẩn bựa mới chiệu nổi.

## 🔹 1. Nguyên tắc làm việc với Yii2
- Sử dụng Yii2 phiên bản **2.0.46** và PHP **8.1**.
- Tập trung vào **Service Layer** trước, đảm bảo nó tuân thủ **Interface Segregation**.
- **Repository Pattern** tạm thời dùng **Active Record**, sau này sẽ custom lại.
- Kiểm tra **version PHP** trước khi cài đặt package bằng Composer.

## 🔹 2. Áp dụng SOLID vào Yii2
### ✅ SRP & OCP đã hoàn thành.
### ✅ Đang tiếp tục với:
- **Liskov Substitution Principle (LSP)**
- **Interface Segregation Principle (ISP)**
- **Dependency Inversion Principle (DIP)**
- Toàn bộ SOLID sẽ được áp dụng vào **cấu trúc Yii2**, đặc biệt là **Service Layer**.

## 🔹 3. Cấu trúc Service Layer trong Yii2
- Service Layer sẽ là nơi xử lý logic nghiệp vụ chính.
- Tương tác với **Repository (Active Record)**.
- Tách biệt hoàn toàn với Controller.
- Không để Controller xử lý nghiệp vụ, chỉ nhận request và gọi Service.

## 🔹 4. API quan trọng trong hệ thống
- **msresource API** dùng để quản lý file upload & download:
  1. **Upload API:** `POST /msresource/resources/upload`
  2. **Download API:** `GET /msresource/resources/download/<code>`
- Khi tạo file PDF, phải upload lên **msresource** ngay sau khi tạo.
- `code` để download sẽ lấy từ `data.resRelationDTOList[].code` trong API Upload.

## 🔹 5. Nguyên tắc xử lý file PDF trong Yii2
- Sử dụng **mPDF** để convert HTML → PDF.
- Sử dụng **FPDI** để xử lý PDF & merge ảnh vào PDF.
- Cài đặt các thư viện qua Composer:
  ```sh
  composer require mpdf/mpdf setasign/fpdi
  ```

## 🔹 6. Mô hình tính SLA trong Ticket Management
- **Ticket có nhiều loại**, phục vụ cho một model "Device".
- **Device phân loại theo "Device Type"**, SLA sẽ dựa trên "Device Type".
- **SLA có nhiều loại**: Tiếp nhận, Xử lý, Kiểm tra.
- **Thời gian SLA khác nhau** tùy loại & "Device Type".
- SLA chỉ tính **trong giờ làm việc**.
- Cấu hình **ngày nghỉ lễ/tết**, SLA không tính ngày nghỉ.
- SLA vào lễ/tết chỉ tính **trong giờ làm việc**.
- **Nếu xử lý ticket trong ngày nghỉ**, thời gian sẽ cộng dồn vào ngày làm việc tiếp theo.
- **Giờ làm việc**: 8h/ngày, có thể cấu hình.

## 🔹 7. Hệ thống Priority cho các practice
Fen đã đặt **mức độ ưu tiên từ 1 đến 10** cho các practice, cụ thể như sau:

- **10**: OOAD (Object-Oriented Analysis and Design).
- **6**: SOLID principles.
- **5**: Version framework, PHP, thư viện đang sử dụng.
- **4**: API quan trọng trong hệ thống.
- **3**: Các thư viện xử lý các trường hợp nghiệp vụ.
- **1**: Module tính SLA cho hệ thống Ticket Management.

🔹 **Quy tắc ưu tiên:**
- **Số càng cao (10):** Độ quan trọng càng lớn, mang tính vĩ mô (ví dụ: SOLID, kiến trúc tổng thể).
- **Số càng thấp (1):** Độ quan trọng giảm dần, mang tính vi mô (ví dụ: chi tiết code cụ thể).
- **Các priority cao định hình và định hướng cho các priority thấp hơn.**
  - Ví dụ: **OOAD (10) và SOLID (6)** sẽ ảnh hưởng đến cách thiết kế **API (4) và thư viện nghiệp vụ (3)**.
  - Khi thiết kế hoặc suggest giải pháp, cần đảm bảo các mức thấp tuân thủ nguyên tắc của mức cao hơn.
- **Khi bộ nhớ sắp đầy, ưu tiên xóa các priority thấp trước.**
  - Trước khi quên thông tin, cần **cảnh báo user** và cho user chọn thông tin nào sẽ bị xóa.

---

🚀 **Đây là toàn bộ rule mà fen đã đặt ra từ trước tới giờ. Nếu cần chỉnh sửa hay bổ sung, cứ báo tui!** 😆
