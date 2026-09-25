# Hệ thống trắc nghiệm Quản trị học — 9 chương

## Thành phần
- 9 chương × 40 câu = **360 câu**.
- Trước khi làm: bắt buộc nhập **Họ và tên + Lớp**.
- Đáp án được tự động lưu vào Supabase.
- Chỉ khi trả lời đủ 40 câu và bấm **Nộp bài** mới hiển thị điểm, meme, đáp án đúng, giải thích và “Nội dung thuộc”.
- **Chương 1 không có “Nội dung thuộc”** nên phần kết quả tự động không hiển thị mục này.
- Từ **lượt 3 trở đi của cùng người + lớp + chương**: ghi nhận chuyển/ẩn tab, mất focus, thoát fullscreen, rời trang rồi quay lại, và phiên trình duyệt song song. Báo cáo chỉ hiện sau khi nộp.
- `admin.html` có đăng nhập giảng viên, thống kê, lọc, xem chi tiết và xuất CSV.

## Cài đặt lần đầu / cập nhật từ bản cũ
1. Trong Supabase mở **SQL Editor**.
2. Copy toàn bộ file `supabase_schema_9_chuong.sql` → **Run**. File này có thể chạy lại; dữ liệu câu hỏi được UPSERT, không xóa lịch sử bài làm cũ.
3. Mở `config.js`. Giữ Project URL và dán đúng **Publishable key** (`sb_publishable_...`) vào `SUPABASE_ANON_KEY`. Không dùng Secret/Service Role key.
4. Upload/commit toàn bộ file lên GitHub Pages (branch `main`, folder `/(root)`).
5. Mở trang chủ và nhấn `Ctrl + F5` để bỏ cache cũ.

## Tạo tài khoản quản trị
1. Supabase → Authentication → Users → Add user.
2. Tạo email/mật khẩu giảng viên.
3. Chạy câu SQL cuối file schema, thay `EMAIL_GIANG_VIEN` bằng email đã tạo.
4. Mở `admin.html` và đăng nhập.

## Lưu ý bảo mật
- Correct answer / explanation / topic **không được đưa vào file dữ liệu công khai**. Học sinh chỉ nhận các trường này từ RPC sau khi nộp bài.
- `config.js` chỉ chứa Publishable/Anon key, đây là key dành cho frontend. Không bao giờ đưa Service Role/Secret key lên GitHub.
