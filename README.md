# I_learn_api

HTML display
<!DOCTYPE html>
<html lang="vi">
  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tiêu đề trang</title>
  </head>
  <body>
    <h1>Nội dung hiển thị ở đây</h1>
    <p>Đây là một đoạn văn.</p>
  </body>
</html>

<!DOCTYPE html>              ← Khai báo chuẩn HTML5
<html>                       ← Gốc của toàn bộ trang
 ├── <head>                  ← Thông tin "hậu trường" (không hiển thị)
 │     ├── <meta charset>
 │     ├── <title>
 │     └── <link>/<script>
 │
 └── <body>                  ← Nội dung hiển thị cho người dùng
       ├── <header>          ← Phần đầu trang (logo, menu)
       ├── <main>             
       │     ├── <h1>, <p>   ← Nội dung chính
       │     └── <img>, <a>
       └── <footer>          ← Phần chân trang

## 1. Thẻ cấu trúc cơ bản (Document Structure)
Tạo khung xương nền tảng cho một trang HTML.

* `<html>`: Thẻ gốc bao bọc toàn bộ trang web.
* `<head>`: Chứa thông tin cấu hình, metadata, tiêu đề trang và liên kết file CSS/JS.
* `<title>`: Đặt tiêu đề hiển thị trên thanh tab của trình duyệt.
* `<body>`: Chứa toàn bộ nội dung hiển thị cho người dùng (văn bản, hình ảnh, video...).

---

## 2. Thẻ bố cục ngữ nghĩa (Semantic Layout)
Phân chia các phần chính của giao diện, giúp Google/SEO hiểu cấu trúc trang.

* `<header>`: Phần đầu trang (logo, menu chính, thanh tìm kiếm).
* `<nav>`: Chứa danh sách các liên kết điều hướng (Navigation menu).
* `<main>`: Chứa nội dung chính và duy nhất của trang.
* `<section>`: Đóng gói một phần nội dung độc lập có chủ đề chung.
* `<article>`: Định nghĩa bài viết, tin tức hoặc bình luận hoàn chỉnh.
* `<aside>`: Nội dung phụ bên cạnh (thanh Sidebar, quảng cáo).
* `<footer>`: Phần chân trang (bản quyền, liên hệ, chính sách).

---

## 3. Thẻ văn bản (Text Formatting)
Định dạng nội dung đoạn văn, tiêu đề và nhấn mạnh chữ.

* `<h1>` đến `<h6>`: Tiêu đề bài viết theo thứ tự từ lớn nhất (`h1`) đến nhỏ nhất (`h6`).
* `<p>`: Định nghĩa một đoạn văn bản (Paragraph).
* `<span>`: Thẻ gom nhóm văn bản dạng inline để đặt màu/style riêng cho từng chữ.
* `<strong>`: Làm đậm chữ (mang nghĩa nhấn mạnh nội dung quan trọng).
* `<em>`: In nghiêng chữ (mang nghĩa nhấn mạnh tone giọng).
* `<br>`: Xuống dòng đơn.

---

## 4. Thẻ danh sách (Lists)
Tạo các danh sách thông tin.

* `<ul>`: Danh sách không sắp xếp theo thứ tự (dùng dấu chấm tròn).
* `<ol>`: Danh sách có sắp xếp theo thứ tự (đánh số 1, 2, 3...).
* `<li>`: Mỗi item/dòng nằm trong danh sách `<ul>` hoặc `<ol>`.

---

## 5. Thẻ Liên kết & Đa phương tiện (Links & Media)
Chèn hình ảnh, đường dẫn và các loại tệp nghe/nhìn.

* `<a>`: Tạo đường dẫn (link) liên kết sang trang/file khác qua thuộc tính `href`.
* `<img>`: Chèn hình ảnh vào trang web qua thuộc tính `src`.
* `<audio>`: Chèn file phát âm thanh.
* `<video>`: Chèn file phát video.
* `<iframe>`: Nhúng một trang web khác vào trong trang hiện tại (ví dụ: Google Maps, video YouTube).

---

## 6. Thẻ Bảng (Tables)
Hiển thị dữ liệu theo dạng hàng và cột.

* `<table>`: Khung chứa toàn bộ bảng dữ liệu.
* `<tr>`: Định nghĩa một dòng (Row) trong bảng.
* `<th>`: Ô tiêu đề của cột/hàng (chữ đậm, căn giữa).
* `<td>`: Ô chứa dữ liệu thông thường trong dòng.

---

## 7. Thẻ Biểu mẫu & Tương tác (Forms & Inputs)
Thu thập dữ liệu do người dùng nhập (đăng nhập, đăng ký, tìm kiếm).

* `<form>`: Khung chứa biểu mẫu để gửi dữ liệu về Server.
* `<input>`: Ô nhập dữ liệu (text, password, email, checkbox, radio, file...).
* `<textarea>`: Ô nhập văn bản nhiều dòng (đánh giá, bình luận).
* `<button>`: Nút bấm (dùng để gửi form hoặc kích hoạt sự kiện JavaScript).
* `<select>` & `<option>`: Tạo danh sách lựa chọn thả xuống (Dropdown menu).

> 💡 **Thẻ bọc chung (Generic Container):**  
> Ngoài các nhóm trên, không thể không nhắc tới `<div>` — đây là thẻ khối (Block-level) phổ biến nhất dùng làm hộp chứa để gom nhóm các phần tử và dựng bố cục trang bằng CSS/JS.

---
# 🐍 Hướng Dẫn Cào Dữ Liệu Web Cơ Bản Với Python

Đoạn mã này hướng dẫn cách tải nội dung một trang web và trích xuất tất cả các đường liên kết (links) bằng hai thư viện phổ biến: **`requests`** và **`BeautifulSoup`**.

---

## 🛠️ Yêu cầu tiền đề (Prerequisites)

Trước khi chạy code, bạn cần cài đặt 2 thư viện này bằng lệnh Terminal / Command Prompt:

```bash
pip install requests bs4

# 1. Nhập (import) các thư viện cần thiết
import requests
from bs4 import BeautifulSoup

# 2. Khai báo URL của trang web bạn muốn cào dữ liệu text/ image
url = "[https://en.wikipedia.org/wiki/IBM](https://en.wikipedia.org/wiki/IBM)"

# 3. Gửi một yêu cầu HTTP GET đến trang web để lấy dữ liệu về
response = requests.get(url)
#3.1. Kiểm tra trạng thái của yêu cầu
response.status_code
#3.2. Xem request headers
print(response.request.headers)
print(response.headers) #This returns a python dictionary of HTTP response headers.
#3.3. Xem request body
print(response.request.body)
#3.4. Xem request date
header['Date']
#3.5. Xem request content-type
header['Content-Type']
#3.6. Kiểm tra request encoding
response.encoding

# 4. Lấy nội dung mã nguồn HTML thô (Raw HTML) từ phản hồi
html_content = response.text

# 5. Tạo một đối tượng BeautifulSoup để phân tích (parse) cú pháp HTML as a tree-like structure.
soup = BeautifulSoup(html_content, "html.parser")

# 6. In ra 500 ký tự đầu tiên của mã HTML để kiểm tra dữ liệu thô
print("--- 500 KÝ TỰ HTML ĐẦU TIÊN ---")
print(html_content[:500])
print("\n" + "=" * 50 + "\n")

# 7. CUSTOM DATA EXTRACTION Tìm tất cả các thẻ <a> (thẻ chứa đường dẫn/link) trong trang web
links = soup.find_all("a")

# 8. Duyệt qua từng thẻ <a> tìm được và in ra văn bản hiển thị (text) của link đó
print("--- DANH SÁCH VĂN BẢN TRONG CÁC THẺ LINK ---")
for link in links:
    # .strip() giúp loại bỏ các khoảng trắng thừa hoặc dòng trống
    # link.text : Chỉ lấy phần chữ hiển thị người dùng nhìn thấy trên màn hình, loại bỏ toàn bộ các thẻ tag HTML xung quanh.
    text = link.text.strip()

    # Chỉ in ra nếu thẻ link đó có chứa văn bản (tránh in ra các dòng trống)
    if text:
        print(text)
```
-------

# 📊 Trích Xuất Dữ Liệu Bảng (Table) Trên Web Bằng `pandas.read_html`

## 💡 Tổng quan & Tính ứng dụng

Hàm **`pd.read_html()`** trong thư viện **Pandas** cho phép bạn tự động cào (scrape) tất cả các bảng dữ liệu (`<table>`) từ một trang web và chuyển đổi chúng thành các **DataFrame**. 

> **Hình dung thực tế:** Nó giống như việc bạn copy một bảng dữ liệu từ trang web rồi dán trực tiếp vào **Excel / Google Sheets** chỉ bằng 1 dòng lệnh Python, sẵn sàng cho việc phân tích dữ liệu ngay lập tức!

---

## 🔑 Kiến thức & Hàm cốt lõi (Core Functions)

### 1. Hàm chính: `pd.read_html()`
* **`pd.read_html(url_hoac_html)`**: Đọc file HTML hoặc đường dẫn URL, tự động tìm các thẻ `<table>` và trả về **một danh sách các DataFrames** (`List[DataFrame]`).

### 2. Các tham số thực hành quan trọng (Parameters):
| Tham số | Ý nghĩa & Cách dùng thực tế |
| :--- | :--- |
| **`match`** | Lọc bảng cần lấy dựa trên chữ/chuỗi có chứa trong bảng đó (VD: `match="Doanh thu"`). |
| **`header`** | Chỉ định dòng nào trong bảng làm tiêu đề cột (thường là `header=0`). |
| **`index_col`** | Chọn cột làm chỉ số (Index) cho DataFrame. |
| **`flavor`** | Động cơ phân tích HTML (mặc định dùng `lxml` hoặc `bs4`). |

### 3. Lưu ý:
Kết quả trả về luôn là List: Đừng quên pd.read_html() luôn trả về danh sách các bảng. Bạn cần dùng chỉ số index như tables[0], tables[1] để truy cập từng bảng cụ thể.

Không cào được web có JavaScript động: read_html chỉ đọc được mã HTML tĩnh gửi về từ server. Nếu bảng dữ liệu được tạo ra bằng JavaScript (React, Vue, AJAX...), bạn nên dùng Selenium hoặc Playwright để tải trang trước khi dùng read_html.

Tránh bị chặn IP: Nếu gặp lỗi HTTP Error 403: Forbidden, bạn cần kết hợp thêm thư viện requests để giả lập trình duyệt (thêm Headers):

---

## 🛠️ Yêu cầu cài đặt (Prerequisites)

Để `read_html` hoạt động tốt, bạn cần cài đặt `pandas` cùng với thư viện hỗ trợ đọc HTML (`lxml` hoặc `html5lib` + `BeautifulSoup4`):

```bash
pip install pandas lxml html5lib bs4

import pandas as pd

# 1. Đường dẫn trang Wikipedia về mùa giải Ngoại hạng Anh
url = "https://en.wikipedia.org/wiki/2023%E2%80%9324_Premier_League"

# 2. Dùng pandas đọc bảng có chứa chữ "Tottenham" hoặc "Arsenal" để lọc đúng bảng xếp hạng
tables = pd.read_html(url, match="Arsenal")

# 3. Lấy bảng xếp hạng
df_bxh = tables[0]

# 4. Hiển thị 5 đội dẫn đầu
print("🏆 TOP 5 ĐỘI DẪN ĐẦU BẢNG XẾP HẠNG:")
print(df_bxh.head())

# 5. Lọc ra các cột quan trọng (Vị trí, Đội bóng, Số trận, Thắng, Hòa, Thua, Điểm)
# Dùng iloc để chọn cột theo thứ tự index
df_sach = df_bxh.iloc[:, [0, 1, 2, 3, 4, 5, 9]] 

# Đổi tên cột sang tiếng Việt cho dễ đọc
df_sach.columns = ["Hạng", "Đội bóng", "ST", "Thắng", "Hòa", "Thua", "Điểm"]

print("\n📊 BẢNG XẾP HẠNG ĐÃ ĐƯỢC LÀM SẠCH:")
print(df_sach.head(10))

# 6. Lưu kết quả ra file Excel hoặc CSV
df_sach.to_csv("bxh_ngoai_hang_anh.csv", index=False, encoding="utf-8-sig")
print("\n🎉 Đã xuất thành công file 'bxh_ngoai_hang_anh.csv'!")

```
# 🌐 Xử Lý HTTP Requests Trong Python: GET vs POST

Hướng dẫn chi tiết về cách gửi **GET Request (với URL Parameters)** và **POST Request (với Data Body)** bằng thư viện `requests` trong Python, sử dụng dịch vụ thử nghiệm `httpbin.org`.

| Tiêu chí | HTTP GET | HTTP POST |
| :--- | :--- | :--- |
| **Vị trí chứa dữ liệu** | Đính trực tiếp trên **URL** dưới dạng Query String (`?key=value`). | Đóng gói bên trong **Request Body** (Ẩn khỏi thanh địa chỉ). |
| **Cấu trúc URL (`r.url`)** | Thay đổi theo dữ liệu gửi đi (Ví dụ: `http://example.com/api?id=123`). | Giữ nguyên đường dẫn gốc (Ví dụ: `http://example.com/api`). |
| **Thân yêu cầu (`r.request.body`)** | **`None`** (Không sử dụng body để truyền dữ liệu). | Chứa chuỗi dữ liệu gửi đi (Ví dụ: `id=123` hoặc chuỗi JSON). |
| **Giới hạn dung lượng** | Bị giới hạn bởi độ dài tối đa của URL (~2.048 ký tự). | **Không giới hạn** dung lượng truyền trong body. |
---

## 🔍 1. GET Request với URL Parameters (Query String)

Phương thức **GET** thường dùng để truy vấn hoặc lấy dữ liệu từ Server/API. Chúng ta có thể truyền tham số qua URL bằng một chuỗi **Query String** (bắt đầu bằng dấu `?`, các cặp `key=value` nối nhau bằng dấu `&`).

### 📜 GET - Mã nguồn thực hành:

```python
import requests

# 1. Khai báo URL gốc (Endpoint)
url_get = "[http://httpbin.org/get](http://httpbin.org/get)"

# 2. Tạo dictionary chứa các tham số (Query parameters)
payload = {"name": "Joseph", "ID": "123"}

# 3. Gửi GET Request truyền dictionary vào tham số `params`
r = requests.get(url_get, params=payload)

# 4. Kiểm tra URL thực tế được tạo ra
print("URL hoàn chỉnh:", r.url)
# Output: [http://httpbin.org/get?name=Joseph&ID=123](http://httpbin.org/get?name=Joseph&ID=123)

# 5. Kiểm tra Request Body (GET không có body)
print("Request body:", r.request.body)
# Output: None

# 6. Kiểm tra Mã trạng thái (Status Code)
print("Status code:", r.status_code)

# 7. Kiểm tra Định dạng dữ liệu trả về (Content-Type)
print("Content-Type:", r.headers["Content-Type"])

# 8. Giải mã dữ liệu JSON trả về thành Python Dictionary
data = r.json()

# Lấy các tham số đã gửi từ key 'args'
print("Dữ liệu args nhận được từ Server:", data["args"])
# Output: {'ID': '123', 'name': 'Joseph'}
```
## 📤 2. POST Request với Data Body (Form Data)

Phương thức **POST** thường dùng để gửi dữ liệu lên Server/API nhằm tạo mới, cập nhật dữ liệu hoặc thực hiện các tác vụ như đăng nhập, gửi biểu mẫu (Form). Khác với GET, dữ liệu gửi đi không nằm trên URL mà được đóng gói an toàn bên trong **Request Body** dưới dạng các cặp `key-value`.

```python
import requests

# 1. Khai báo URL Endpoint cho POST
url_post = "[http://httpbin.org/post](http://httpbin.org/post)"

# 2. Dữ liệu cần gửi
payload = {"name": "Joseph", "ID": "123"}

# 3. Gửi POST Request truyền dictionary vào tham số `data`
r_post = requests.post(url_post, data=payload)

# 4. Kiểm tra URL (URL giữ nguyên, không chứa query string)
print("POST request URL:", r_post.url)
# Output: [http://httpbin.org/post](http://httpbin.org/post)

# 5. Kiểm tra Request Body (Dữ liệu nằm ở đây)
print("POST request body:", r_post.request.body)
# Output: name=Joseph&ID=123

# 6. Kiểm tra dữ liệu Form được Server nhận diện
print("Form data nhận được:", r_post.json()["form"])
# Output: {'ID': '123', 'name': 'Joseph'}

