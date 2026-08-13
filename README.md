# Hướng Dẫn Gán Nhãn Bảng Báo Cáo Tài Chính Với PPOCRLabel

[Tiếng Việt](README.md)

---

##  Giới thiệu

Tài liệu này hướng dẫn chi tiết quy trình gán nhãn (annotation) cho các bảng báo cáo tài chính sử dụng công cụ PPOCRLabel. Kết quả đầu ra sẽ được sử dụng để huấn luyện mô hình nhận dạng bảng (table recognition) phục vụ bài toán trích xuất thông tin tài chính tự động.

---
<video src="./Huong_dan_gan_nhan_bang.mp4" controls width="100%"></video>
##  Chuẩn bị môi trường

### 1. Cài đặt PaddleOCR

PPOCRLabel được tích hợp sẵn mô hình PaddleOCR. Vui lòng tham khảo [tài liệu cài đặt PaddleOCR](https://github.com/PaddlePaddle/PaddleOCR/blob/develop/doc/doc_ch/installation.md) để chuẩn bị môi trường.

### 2. Cài đặt PPOCRLabel

**Windows**
```bash
pip install pyqt5
cd ./PPOCRLabel
python PPOCRLabel.py
<img src="./MoPhong.gif?raw=true" width="100%"/>

## Quy trình gán nhãn
Bước 1: Mở thư mục ảnh
Chạy lệnh python PPOCRLabel.py để khởi động công cụ.
Vào menu File → Open Dir, chọn thư mục chứa ảnh báo cáo tài chính.
Danh sách ảnh hiển thị bên phải, trạng thái mặc định là X (chưa xác nhận).

Bước 2: Nhận dạng bảng tự động
Nhấn nút Table Recognition trên thanh công cụ.
Hệ thống sẽ tự động tạo khung nhãn (bounding box) cho từng ô.

Bước 3: Sửa nội dung trong PPOCRLabel (Văn bản)
Nhấp chọn ô cần sửa (khung nhãn chuyển sang màu xanh).
Nhấn Ctrl + E để mở hộp thoại chỉnh sửa nội dung.
Nhập lại nội dung chính xác theo ảnh gốc, nhấn OK.
Các lỗi thường gặp:

Lỗi	Ví dụ (Sai → Đúng)-Cách sửa
Dấu * bị nhầm thành %, ?	
100% → 100*	Sửa lại thành *
Dấu - bị nhầm thành số, %, x
5% → -5	Sửa lại thành -
Thừa từ/cuối dòng:	Tổng tài sản 500 abc → Tổng tài sản 500 - Xóa phần thừa
Thừa số đầu/cuối:	123Tổng tài sản → Tổng tài sản - Xóa số thừa
Viết hoa sai:	Doanh Thu → Doanh thu	-Sửa đúng chính tả

Bước 4: Xác nhận và chuyển tiếp
Sau khi sửa xong, nhấn nút Check (hoặc Ctrl + V).
Trạng thái chuyển từ X → √, hệ thống tự chuyển sang ảnh tiếp theo.

## Các cách lưu file Label.txt:
Tự động lưu: Vào menu File → Auto Save Label Mode để bật chế độ tự động lưu.
Thủ công: Vào menu File → Save Label để lưu kết quả.
Đóng ứng dụng: Dữ liệu tự động được lưu khi đóng chương trình.
