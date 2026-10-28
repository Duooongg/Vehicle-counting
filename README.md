Hệ Thống Đếm Phương Tiện Giao Thông (Vehicle Counting System)
Hệ thống đếm phương tiện giao thông sử dụng mô hình YOLOv8 để nhận diện và thuật toán DeepSORT để theo dõi (tracking) đối tượng.

 Tính năng chính
Nhận diện phương tiện theo thời gian thực: Phát hiện các loại xe (ô tô, xe tải, xe xít, xe máy).

Theo dõi đa đối tượng: Sử dụng thuật toán DeepSORT để theo dõi hành trình phương tiện qua các khung hình.

Đếm phương tiện thông minh: Đếm xe dựa trên các đường ranh giới (counting lines) do người dùng tùy chỉnh.

Phân tích vùng vào/ra: Xác định hướng di chuyển và phân tích vùng lưu thông của phương tiện.

Bảng thống kê trực quan (Dashboard): Cập nhật số liệu thống kê xe chạy liên tục theo thời gian thực.

Giám sát trực tiếp qua WebSocket: Hỗ trợ truyền dòng dữ liệu (stream) video và dữ liệu đếm mượt mà.

Xử lý file video: Hỗ trợ tải lên video, xử lý đếm xe và tải xuống video kết quả.

Backend REST API mạnh mẽ: Xây dựng trên nền tảng FastAPI.

Kiến trúc mã nguồn sạch (Clean Architecture): Code được đóng gói chuẩn chỉnh, hỗ trợ Type Hints và Docstrings rõ ràng.

🛠️ Các sửa lỗi gần đây (Recent Fixes)
Kiểm tra & Xử lý giá trị Confidence trong DeepSORT
Khắc phục lỗi các vết theo dõi (tracks) của DeepSORT đôi khi trả về giá trị độ tin cậy (confidence) bằng None, gây ra lỗi xác thực dữ liệu.

Bổ sung cơ chế xử lý trong tracking service để gán giá trị độ tin cậy mặc định khi phát hiện giá trị None.

Cải thiện khả năng bắt lỗi và ghi log báo cáo cho các thao tác theo dõi.

Bổ sung các bài kiểm thử (unit tests) toàn diện cho hệ thống tracking để đảm bảo ổn định.

🚀 Cài đặt
Bash
# Di chuyển vào thư mục dự án
cd vehicle-counting

# Tạo môi trường ảo và cài đặt các thư viện cần thiết
python -m venv .env
source .env/bin/activate        # On Linux/macOS
# .env\Scripts\activate          # On Windows Command Prompt

pip install -r requirements.txt
⚡ Khởi chạy nhanh
Bash
# Khởi chạy hệ thống bằng 1 lệnh duy nhất
./start.sh

# Mở giao diện Web trên trình duyệt tại địa chỉ:
# http://localhost:8000/static/index.html
📡 Danh sách API (API Endpoints)
REST API
GET /api/v1/health: Kiểm tra trạng thái hoạt động của hệ thống (Health check).

GET /api/v1/model-info: Lấy thông tin về mô hình AI đang được nạp.

GET /api/v1/stats: Lấy dữ liệu thống kê số lượng xe hiện tại.

POST /api/v1/reset-counts: Đặt lại (reset) toàn bộ số liệu đếm.

POST /api/v1/counting-lines: Thiết lập vạch ranh giới để đếm phương tiện.

POST /api/v1/process-video: Tải lên và xử lý file video.

GET /api/v1/job-status/{job_id}: Kiểm tra tiến độ xử lý của video.

GET /api/v1/download-result/{job_id}: Tải về video kết quả sau khi xử lý xong.

POST /api/v1/camera/start: Bắt đầu xử lý luồng camera trực tiếp.

POST /api/v1/camera/stop: Dừng luồng camera.

GET /api/v1/test-detection: Endpoint thử nghiệm để kiểm tra dịch vụ nhận diện.

WebSocket Endpoints
/api/v1/webcam-stream: Kết nối WebSocket phục vụ nhận diện trực tiếp từ Webcam.

/api/v1/live-stats: Kết nối WebSocket cập nhật biến động số liệu đếm theo thời gian thực.

🧩 Các thành phần chính (Components)
Detection Service: Sử dụng YOLOv8 để phát hiện các phương tiện trong từng khung hình.

Tracking Service: Sử dụng DeepSORT để định danh và theo dõi hành trình xe qua các khung hình liên tiếp.

Counting Service: Phân tích hành trình của xe để thực hiện đếm khi xe vượt qua các đường ranh giới đã thiết lập.

Video Processing Service: Tích hợp các dịch vụ Nhận diện, Theo dõi và Đếm vào quy trình xử lý video hoàn chỉnh.

📁 Cấu trúc thư mục dự án
Plaintext
vehicle_counting/
├── app/                  # Mã nguồn chính của ứng dụng
│   ├── api/              # Định nghĩa các tuyến đường (routes) và endpoints API
│   ├── core/             # Cấu hình cốt lõi của ứng dụng
│   ├── models/           # Định nghĩa các mô hình dữ liệu và schemas
│   ├── services/         # Chứa logic xử lý nghiệp vụ (Business logic)
│   └── utils/            # Các hàm tiện ích hỗ trợ
├── configs/              # Các file cấu hình hệ thống
├── data/                 # Thư mục lưu trữ dữ liệu
│   ├── outputs/          # Video kết quả sau khi xử lý
│   ├── uploads/          # Thư mục tạm chứa video người dùng tải lên
│   └── videos/           # Các video mẫu phục vụ thử nghiệm
├── logs/                 # Nhật ký hoạt động của ứng dụng (System logs)
├── scripts/              # Các kịch bản/script tiện ích
├── static/               # Các file giao diện web tĩnh
│   └── index.html        # Giao diện người dùng trên web
├── tests/                # Các bài kiểm thử tự động (Test cases)
├── requirements.txt      # Danh sách các thư viện phụ thuộc
└── start.sh              # Script khởi chạy ứng dụng nhanh
📜 Giấy phép (License)
Dự án được phân phối theo giấy phép MIT License.

🙏 Tham khảo (Acknowledgements)
YOLOv8 — Mô hình nhận diện đối tượng.

DeepSORT — Thuật toán theo dõi đối tượng theo thời gian thực.

FastAPI — Framework web server hiệu năng cao cho Python.