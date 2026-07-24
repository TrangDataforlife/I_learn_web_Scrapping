# I_learn_api

1. Thẻ cấu trúc cơ bản (Document Structure)
Tạo khung xương nền tảng cho một trang HTML.

<html>: Thẻ gốc bao bọc toàn bộ trang web.

<head>: Chứa thông tin cấu hình, metadata, tiêu đề trang và liên kết file CSS/JS.

<title>: Đặt tiêu đề hiển thị trên thanh tab của trình duyệt.

<body>: Chứa toàn bộ nội dung hiển thị cho người dùng (văn bản, hình ảnh, video...).

2. Thẻ bố cục ngữ nghĩa (Semantic Layout)
Phân chia các phần chính của giao diện, giúp Google/SEO hiểu cấu trúc trang.

<header>: Phần đầu trang (logo, menu chính, thanh tìm kiếm).

<nav>: Chứa danh sách các liên kết điều hướng (Navigation menu).

<main>: Chứa nội dung chính và duy nhất của trang.

<section>: Đóng gói một phần nội dung độc lập có chủ đề chung.

<article>: Định nghĩa bài viết, tin tức hoặc bình luận hoàn chỉnh.

<aside>: Nội dung phụ bên cạnh (thanh Sidebar, quảng cáo).

<footer>: Phần chân trang (bản quyền, liên hệ, chính sách).

3. Thẻ văn bản (Text Formatting)
Định dạng nội dung đoạn văn, tiêu đề và nhấn mạnh chữ.

<h1> đến <h6>: Tiêu đề bài viết theo thứ tự từ lớn nhất (h1) đến nhỏ nhất (h6).

<p>: Định nghĩa một đoạn văn bản (Paragraph).

<span>: Thẻ gom nhóm văn bản dạng inline để đặt màu/style riêng cho từng chữ.

<strong>: Làm đậm chữ (mang nghĩa nhấn mạnh nội dung quan trọng).

<em>: In nghiêng chữ (mang nghĩa nhấn mạnh tone giọng).

<br>: Xuống dòng đơn.

4. Thẻ danh sách (Lists)
Tạo các danh sách thông tin.

<ul>: Danh sách không sắp xếp theo thứ tự (dùng dấu chấm tròn).

<ol>: Danh sách có sắp xếp theo thứ tự (đánh số 1, 2, 3...).

<li>: Mỗi item/dòng nằm trong danh sách <ul> hoặc <ol>.

5. Thẻ Liên kết & Đa phương tiện (Links & Media)
Chèn hình ảnh, đường dẫn và các loại tệp nghe/nhìn.

<a>: Tạo đường dẫn (link) liên kết sang trang/file khác qua thuộc tính href.

<img>: Chèn hình ảnh vào trang web qua thuộc tính src.

<audio>: Chèn file phát âm thanh.

<video>: Chèn file phát video.

<iframe>: Nhúng một trang web khác vào trong trang hiện tại (ví dụ: Google Maps, video YouTube).

6. Thẻ Bảng (Tables)
Hiển thị dữ liệu theo dạng hàng và cột.

<table>: Khung chứa toàn bộ bảng dữ liệu.

<tr>: Định nghĩa một dòng (Row) trong bảng.

<th>: Ô tiêu đề của cột/hàng (chữ đậm, căn giữa).

<td>: Ô chứa dữ liệu thông thường trong dòng.

7. Thẻ Biểu mẫu & Tương tác (Forms & Inputs)
Thu thập dữ liệu do người dùng nhập (đăng nhập, đăng ký, tìm kiếm).

<form>: Khung chứa biểu mẫu để gửi dữ liệu về Server.

<input>: Ô nhập dữ liệu (text, password, email, checkbox, radio, file...).

<textarea>: Ô nhập văn bản nhiều dòng (đánh giá, bình luận).

<button>: Nút bấm (dùng để gửi form hoặc kích hoạt sự kiện JavaScript).

<select> & <option>: Tạo danh sách lựa chọn thả xuống (Dropdown menu).

💡 Thẻ bọc chung (Generic Container): Ngoài các nhóm trên, không thể không nhắc tới <div> — đây là thẻ khối (Block-level) phổ biến nhất dùng làm hộp chứa để gom nhóm các phần tử và dựng bố cục trang bằng CSS/JS.
