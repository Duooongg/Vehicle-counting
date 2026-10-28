# Vehicle Counting System

A professional vehicle counting system using YOLOv8 for detection and DeepSORT for tracking.

## Features

- Real-time vehicle detection (car, truck, bus, motorcycle)
- Multi-object tracking with DeepSORT
- Vehicle counting with customizable counting lines
- Entry/exit zone analysis
- Live statistics dashboard
- WebSocket-based real-time monitoring
- Video file processing with results download
- FastAPI REST API backend
- Clean architecture with type hints and docstrings

## Recent Fixes

### DeepSORT Confidence Value Validation
- Fixed an issue where DeepSORT tracks sometimes return None confidence values causing validation errors
- Added proper handling in the tracking service to assign default confidence values when None is returned
- Improved error handling and reporting for tracking operations
- Created comprehensive tracking system tests to verify the fix

## Installation

```bash
# Clone the repository

cd vehicle-counting

# Create virtual environment and install dependencies
python -m venv .env
source .env/bin/activate
pip install -r requirements.txt
```

## Quick Start

```bash
# Start the system with a single command
./start.sh

# Open the web interface in your browser
# http://localhost:8000/static/index.html
```

## API Endpoints

### REST API

- `GET /api/v1/health`: Health check endpoint
- `GET /api/v1/model-info`: Get information about the loaded model
- `GET /api/v1/stats`: Get current counting statistics
- `POST /api/v1/reset-counts`: Reset all counting statistics
- `POST /api/v1/counting-lines`: Set counting lines for vehicle counting
- `POST /api/v1/process-video`: Upload and process a video file
- `GET /api/v1/job-status/{job_id}`: Get status of a video processing job
- `GET /api/v1/download-result/{job_id}`: Download processed video result
- `POST /api/v1/camera/start`: Start camera processing
- `POST /api/v1/camera/stop`: Stop camera processing
- `GET /api/v1/test-detection`: Test endpoint to verify detection service

### WebSocket Endpoints

- `/api/v1/webcam-stream`: WebSocket endpoint for real-time webcam processing
- `/api/v1/live-stats`: WebSocket endpoint for live statistics updates

## Components

- **Detection Service**: Uses YOLOv8 to detect vehicles in frames
- **Tracking Service**: Uses DeepSORT to track vehicles across frames
- **Counting Service**: Analyzes tracks to count vehicles crossing defined lines
- **Video Processing Service**: Integrates detection, tracking, and counting

## Project Structure

<<<<<<< HEAD
```
vehicle_counting/
├── app/                  # Main application code
│   ├── api/              # API routes and endpoints
│   ├── core/             # Core configuration
│   ├── models/           # Data models and schemas
│   ├── services/         # Business logic services
│   └── utils/            # Utility functions
├── configs/              # Configuration files
├── data/                 # Data storage
│   ├── outputs/          # Processed video outputs
│   ├── uploads/          # Temporary video uploads
│   └── videos/           # Sample videos for testing
├── logs/                 # Application logs
├── scripts/              # Utility scripts
├── static/               # Static web files
│   └── index.html        # Web interface
├── tests/                # Test files
├── requirements.txt      # Dependencies
└── start.sh              # Startup script
```

## License
=======
POST /api/v1/camera/stop: Dừng luồng camera.

GET /api/v1/test-detection: Endpoint thử nghiệm để kiểm tra dịch vụ nhận diện.

WebSocket Endpoints
/api/v1/webcam-stream: Kết nối WebSocket phục vụ nhận diện trực tiếp từ Webcam.

/api/v1/live-stats: Kết nối WebSocket cập nhật biến động số liệu đếm theo thời gian thực.

🧩 Các thành phần chính 
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

🙏 Tham khảo 
YOLOv8 — Mô hình nhận diện đối tượng.
>>>>>>> 87f20c264a2610aff1ca3f8d56ce991ae6885a39

MIT

<<<<<<< HEAD
## Acknowledgements

- [YOLOv8](https://github.com/ultralytics/ultralytics) for object detection
- [DeepSORT](https://github.com/levan92/deep_sort_realtime) for object tracking
- [FastAPI](https://fastapi.tiangolo.com/) for the web server framework
=======
FastAPI — Framework web server hiệu năng cao cho Python.
>>>>>>> 87f20c264a2610aff1ca3f8d56ce991ae6885a39
