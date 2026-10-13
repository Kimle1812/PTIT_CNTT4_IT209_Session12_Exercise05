# IT209 - Session 12 - Bài 5: Chẩn Đoán & Khắc Phục 3 Sự Cố Đứt Gãy Pipeline CI/CD

## 1. Giới Thiệu Dự Án
Kho lưu trữ này chứa bài giải hoàn chỉnh cho **Bài 5 - Session 12**:
- Chẩn đoán, cô lập và khắc phục 3 lỗi nghiêm trọng làm đứt gãy luồng Pipeline CI/CD trên GitHub Actions.
- Tự động hóa kiểm thử mã nguồn Java Spring Boot với Gradle và đóng gói, phát hành Docker Image lên GitHub Container Registry (GHCR).

## 2. Danh Mục Các Lỗi Đã Khắc Phục
1. **Lỗi 1 (Permission Denied)**: Khắc phục lỗi Gradle Wrapper thiếu cờ thực thi trên Runner Ubuntu bằng lệnh `chmod +x gradlew`.
2. **Lỗi 2 (Authentication Failed)**: Khắc phục lỗi sai chính tả biến Secret (`REGISTRY_TOKNE`) bằng cách chuẩn hóa `${{ secrets.REGISTRY_TOKEN || secrets.GITHUB_TOKEN }}`.
3. **Lỗi 3 (Build Context Error)**: Khắc phục lỗi không tìm thấy `Dockerfile` bằng cách cấu hình `context: .` và `file: ./Dockerfile` cho `docker/build-push-action@v5`.

## 3. Cấu Trúc Thư Mục
```plaintext
d:/IT209/SS12/Ex5/
├── .github/
│   └── workflows/
│       └── broken-pipeline.yml    # Kịch bản GitHub Actions đã sửa hoàn chỉnh
├── homework/
│   └── session_12/
│       └── ex5/
│           ├── .github/
│           │   └── workflows/
│           │       └── broken-pipeline.yml
│           └── troubleshooting.md # Báo cáo kỹ thuật chi tiết
├── gradle/
│   └── wrapper/
│       ├── gradle-wrapper.jar
│       └── gradle-wrapper.properties
├── src/
│   ├── main/java/com/example/caching/
│   └── test/java/com/example/caching/
├── build.gradle
├── Dockerfile
├── gradlew
├── gradlew.bat
├── settings.gradle
├── troubleshooting.md             # Báo cáo kỹ thuật chẩn đoán và khắc phục
└── README.md
```

## 4. Báo Cáo Kỹ Thuật
Xem chi tiết toàn bộ phân tích nguyên nhân, log lỗi mẫu, so sánh Git Diff và hướng dẫn kiểm thử tại:
- [troubleshooting.md](file:///d:/IT209/SS12/Ex5/troubleshooting.md)
- [broken-pipeline.yml](file:///d:/IT209/SS12/Ex5/.github/workflows/broken-pipeline.yml)
