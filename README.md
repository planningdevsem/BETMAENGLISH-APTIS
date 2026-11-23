# BETMA ENGLISH — Website, Luyện APTIS, Thi thử APTIS (bản demo)

Ứng dụng web một trang (SPA) gồm 3 khu vực trong cùng một khung giao diện:

- **TRANG CHỦ**: trang giới thiệu thương hiệu BETMA ENGLISH.
- **LUYỆN APTIS**: ngân hàng đề Listening Part 1–4 và Reading Part 1–4, có kiểm tra đáp án, giải thích, làm lại, tra từ, theo dõi tiến độ.
- **THI THỬ**: phòng thi CBT đủ 5 phần (Grammar & Vocabulary, Listening, Reading, Writing, Speaking), đồng hồ tổng, ghi âm Speaking bằng microphone, nộp bài và xem kết quả.

> Đây là **bản demo chạy hoàn toàn trên trình duyệt** (HTML + JavaScript thuần, không cần build).
> Dữ liệu (tiến độ luyện tập, phiên thi, bản ghi âm) lưu trong `localStorage` của từng trình duyệt,
> **chưa có backend, chưa có đăng nhập thật, chưa có trang Admin**.

## Cấu trúc thư mục

```
index.html          Giao diện + logic toàn bộ ứng dụng
js/bank.js          Ngân hàng đề Luyện APTIS (BANK, DICT, RVOC, STRAT)
assets/audio/       Audio Listening câu 1–13 của đề thi thử (q1.mp3 … q13.mp3)
assets/img/         Logo, ảnh lớp học, ảnh đề Speaking
.nojekyll           Báo GitHub Pages không xử lý bằng Jekyll
```

## Chạy trên máy

Cần mở bằng một máy chủ tĩnh (micro và audio hoạt động ổn định hơn so với mở trực tiếp file):

```bash
python3 -m http.server 8000
# rồi mở http://localhost:8000
```

Ghi âm Speaking cần **HTTPS hoặc localhost** (GitHub Pages có HTTPS).

## Đăng lên GitHub Pages

1. Tạo repository mới trên GitHub, tải toàn bộ file trong thư mục này lên (giữ nguyên cấu trúc).
2. Vào **Settings → Pages**.
3. Ở **Build and deployment**, chọn **Deploy from a branch**, nhánh `main`, thư mục `/ (root)`, bấm **Save**.
4. Sau 1–2 phút, trang chạy tại `https://<tên-tài-khoản>.github.io/<tên-repo>/`.

## Chỉnh sửa nội dung

| Muốn đổi | Sửa ở đâu |
| --- | --- |
| Chữ, số liệu, chương trình đào tạo ở trang chủ | `index.html`, hàm `home()` |
| Ảnh hero trang chủ | thay file `assets/img/class-*.jpg` (giữ tên) |
| Logo | thay `assets/img/logo.png` |
| Đề Luyện APTIS | `js/bank.js` |
| Đề thi thử (tên, câu hỏi, đáp án) | `index.html`, tìm `DB.tests.push(` |
| Thời lượng đề thi thử | trường `minutes` của đề |
| Audio Listening câu 1–13 | thay `assets/audio/q*.mp3`, các đoạn được gán trong biến `CLIPS` |

Đề thi thử hiện có: **MOCKTEST X iHUTECH 27/11** (mã `APTIS-PT-V1`) và một đề demo **BETMA-FT-01**.

## Hạn chế hiện tại

- Chưa có trang Admin, chưa có backend/cơ sở dữ liệu; Writing và Speaking chỉ lưu trong trình duyệt, chưa có chấm điểm.
- Listening câu 14–17 của đề thi thử chưa có audio thật nên dùng giọng đọc của trình duyệt (script do BETMA soạn lại).
- Tra từ, từ điển và giọng nghe phụ thuộc trình duyệt; khuyến nghị dùng Chrome hoặc Edge trên máy tính.

## Lưu ý bản quyền

Nội dung đề **Aptis General Practice Test** (Grammar, Vocabulary, Reading, Writing, Speaking, ảnh Speaking) thuộc **© British Council 2020**.
Audio Listening và ngân hàng đề Luyện APTIS là tài liệu do BETMA cung cấp. Hãy chắc chắn bạn có quyền sử dụng và phát hành các tài liệu này trước khi đặt repository ở chế độ **public**; nếu chưa chắc, hãy để repository ở chế độ **private**.
Logo và ảnh lớp học thuộc quyền của BETMA ENGLISH.
