# 🧪 HTML, BeautifulSoup & HTTP Requests với Python

## 📑 Mục lục

- [1. Cấu trúc cơ bản của HTML](#1-cấu-trúc-cơ-bản-của-html)
  - [1.1. HTML display](#11-html-display)
  - [1.2. Thẻ cấu trúc cơ bản (Document Structure)](#12-thẻ-cấu-trúc-cơ-bản-document-structure)
  - [1.3. Thẻ bố cục ngữ nghĩa (Semantic Layout)](#13-thẻ-bố-cục-ngữ-nghĩa-semantic-layout)
  - [1.4. Thẻ văn bản (Text Formatting)](#14-thẻ-văn-bản-text-formatting)
  - [1.5. Thẻ danh sách (Lists)](#15-thẻ-danh-sách-lists)
  - [1.6. Thẻ Liên kết và Đa phương tiện (Links & Media)](#16-thẻ-liên-kết-và-đa-phương-tiện-links--media)
  - [1.7. Thẻ Bảng (Tables)](#17-thẻ-bảng-tables)
  - [1.8. Thẻ Biểu mẫu và Tương tác (Forms & Inputs)](#18-thẻ-biểu-mẫu-và-tương-tác-forms--inputs)
  - [1.9. Thẻ bọc chung (Generic Container)](#19-thẻ-bọc-chung-generic-container)
- [2. Các Object trong BeautifulSoup](#2-các-object-trong-beautifulsoup)
  - [2.1. Các loại Object chính](#21-các-loại-object-chính)
  - [2.2. Thuộc tính quan trọng của Tag Object](#22-thuộc-tính-quan-trọng-của-tag-object)
  - [2.3. Phương thức tìm kiếm phổ biến](#23-phương-thức-tìm-kiếm-phổ-biến)
- [3. Hướng dẫn cào dữ liệu web cơ bản với Python](#3-hướng-dẫn-cào-dữ-liệu-web-cơ-bản-với-python)
- [4. Trích xuất dữ liệu bảng trên Web bằng pd.read_html](#4-trích-xuất-dữ-liệu-bảng-trên-web-bằng-pdread_html)
  - [4.1. Hàm chính — pd.read_html()](#41-hàm-chính--pdread_html)
  - [4.2. Các tham số thực hành quan trọng](#42-các-tham-số-thực-hành-quan-trọng)
  - [4.3. Lưu ý](#43-lưu-ý)
- [5. Xử lý HTTP Requests: GET vs POST](#5-xử-lý-http-requests-get-vs-post)
  - [5.1. GET Request với URL Parameters](#51-get-request-với-url-parameters)
  - [5.2. POST Request với Data Body](#52-post-request-với-data-body)
- [6. Danh sách HTML Attributes](#6-danh-sách-html-attributes)
  - [6.1. Global Attributes (dùng được cho mọi thẻ)](#6.1)
  - [6.2. Attributes cho Form & Input](#6.1)
  - [6.3. Attributes cho Link & Media](#6.1)
  - [6.4. Attributes cho Table](#6.1)
  - [6.5. Attributes cho Iframe & Script](#6.1)
  - [6.6. Event Handler Attributes (on*)](#6.1)
  - [6.7. Attributes cũ / không khuyến khích dùng (Deprecated)](#6.1)
- [7. Pagination (chia trang), Error handling, If __name__ = __main__](#section-7)

---
---
## **Web Scraping with Python**

## 1. BeautifulSoup:
> used for web scraping purposes to pull the data out of HTML and XML files. It creates a parse tree from page source code that can be used to extract data in a hierarchical and more readable manner.
```python
!pip install html5lib
!pip install bs4
! pip install lxml
from bs4 import BeautifulSoup
import requests
URL = "http://www.example.com"

page = requests.get(URL)
hoặc  page = requests.get(URL).text # lấy text content của webpage
hoặc page.json() # trả về dict outcome

soup = BeautifulSoup(page.content, "html.parser") # thư viện python
hoặc  soup = BeautifulSoup(page.content, "html5lib") # theo chuẩn html trình duyệt, chậm nhất
hoặc with open(file.html) as html_file:
        soup = BeautifulSoup(html_file, 'lxml')
print(soup.prettify())
```
## 2. Selenium:
> Selenium is a tool used for controlling web browsers through programs and automating browser tasks.
```python
from selenium import webdriver
driver = webdriver.Firefox()
driver.get("http://www.example.com")
```
### CSV, JSON, XML file formats
## 1. .csv (pandas)
## 2. .json
```python
import json
with open('file.json', 'r') as openfile:
  json_object = json.load(openfile)
print(json_object)
```
## 3. .xml
```python
import pandas as pd

import xml.etree.ElementTree as etree
tree = etree.parse('file.xml')
root = tree.getroot()
columns = ["Name", "Phone", "Birthday"]
df = pd.DataFrame(columns = columns)

for node in root:
    name = node.find("name").text
    phonenumber = node.find("phonenumber").text
    birthday = node.find("birthday").text
    df = df.append(pd.Series([name, phonenumber, birthday],
    index = columns)....., ignore_index = True)
```
## Working with files in python
### 1. Read
```python
with open(current_file, 'r') as openfile:
  object = openfile.read()
print(object)
```
### 2. Writing 
```python
with open('new_file.csv', 'wb') as f:
  f.write(body)
```

```python
import pandas as pd
# Chuyển thành DataFrame và lưu CSV trong 1 dòng
pd.DataFrame(data).to_csv('scrape.csv', index=False, encoding='utf-8-sig')
```

```python
import csv

# Ghi dữ liệu vào CSV
with open('scrape.csv', 'w', newline='', encoding='utf-8-sig') as f:
    writer = csv.writer(f)
    writer.writerow(['col1', 'col2', 'col3']) # Header
    writer.writerow([var1, var2, var3])       # Row
```
---
## 1. Cấu trúc cơ bản của HTML

### 1.1. HTML display

```html
<!DOCTYPE html>
<html lang="vi">
  <head>
    <meta charset="UTF-8"> #bộ mã unicode
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tiêu đề trang</title>
  </head>
  <body>
    <h1>Nội dung hiển thị ở đây</h1>
    <p>Đây là một đoạn văn.</p>
  </body>
</html>
```

```text
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
```

### 1.2. Thẻ cấu trúc cơ bản (Document Structure)

Tạo khung xương nền tảng cho một trang HTML.

| Thẻ | Vai trò |
|---|---|
| `html` | Thẻ gốc bao bọc toàn bộ trang web |
| `head` | Chứa thông tin cấu hình, metadata, tiêu đề trang và liên kết file CSS/JS |
| `title` | Đặt tiêu đề hiển thị trên thanh tab của trình duyệt |
| `body` | Chứa toàn bộ nội dung hiển thị cho người dùng (văn bản, hình ảnh, video...) |

### 1.3. Thẻ bố cục ngữ nghĩa (Semantic Layout)

Phân chia các phần chính của giao diện, giúp Google/SEO hiểu cấu trúc trang.

| Thẻ | Vai trò |
|---|---|
| `header` | Phần đầu trang (logo, menu chính, thanh tìm kiếm) |
| `nav` | Chứa danh sách các liên kết điều hướng (navigation menu) |
| `main` | Chứa nội dung chính và duy nhất của trang |
| `section` | Đóng gói một phần nội dung độc lập có chủ đề chung |
| `article` | Định nghĩa bài viết, tin tức hoặc bình luận hoàn chỉnh |
| `aside` | Nội dung phụ bên cạnh (thanh sidebar, quảng cáo) |
| `footer` | Phần chân trang (bản quyền, liên hệ, chính sách) |

### 1.4. Thẻ văn bản (Text Formatting)

Định dạng nội dung đoạn văn, tiêu đề và nhấn mạnh chữ.

| Thẻ | Vai trò |
|---|---|
| `h1` đến `h6` | Tiêu đề bài viết theo thứ tự từ lớn nhất (`h1`) đến nhỏ nhất (`h6`) |
| `p` | Định nghĩa một đoạn văn bản (paragraph) |
| `span` | Gom nhóm văn bản dạng inline để đặt màu/style riêng cho từng chữ |
| `strong` | Làm đậm chữ (mang nghĩa nhấn mạnh nội dung quan trọng) |
| `em` | In nghiêng chữ (mang nghĩa nhấn mạnh tone giọng) |
| `br` | Xuống dòng đơn |

### 1.5. Thẻ danh sách (Lists)

Tạo các danh sách thông tin.

| Thẻ | Vai trò |
|---|---|
| `ul` | Danh sách không sắp xếp theo thứ tự (dùng dấu chấm tròn) |
| `ol` | Danh sách có sắp xếp theo thứ tự (đánh số 1, 2, 3...) |
| `li` | Mỗi item/dòng nằm trong danh sách `ul` hoặc `ol` |

### 1.6. Thẻ Liên kết và Đa phương tiện (Links & Media)

Chèn hình ảnh, đường dẫn và các loại tệp nghe/nhìn.

| Thẻ | Vai trò |
|---|---|
| `a` | Tạo đường dẫn (link) liên kết sang trang/file khác qua thuộc tính `href` |
| `img` | Chèn hình ảnh vào trang web qua thuộc tính `src` |
| `audio` | Chèn file phát âm thanh |
| `video` | Chèn file phát video |
| `iframe` | Nhúng một trang web khác vào trong trang hiện tại (VD: Google Maps, video YouTube) |

### 1.7. Thẻ Bảng (Tables)

Hiển thị dữ liệu theo dạng hàng và cột.

| Thẻ | Vai trò |
|---|---|
| `table` | Khung chứa toàn bộ bảng dữ liệu |
| `tr` | Định nghĩa một dòng (row) trong bảng |
| `th` | Ô tiêu đề của cột/hàng (chữ đậm, căn giữa) |
| `td` | Ô chứa dữ liệu thông thường trong dòng |

### 1.8. Thẻ Biểu mẫu và Tương tác (Forms & Inputs)

Thu thập dữ liệu do người dùng nhập (đăng nhập, đăng ký, tìm kiếm).

| Thẻ | Vai trò |
|---|---|
| `form` | Khung chứa biểu mẫu để gửi dữ liệu về server |
| `input` | Ô nhập dữ liệu (text, password, email, checkbox, radio, file...) |
| `textarea` | Ô nhập văn bản nhiều dòng (đánh giá, bình luận) |
| `button` | Nút bấm (dùng để gửi form hoặc kích hoạt sự kiện JavaScript) |
| `select` và `option` | Tạo danh sách lựa chọn thả xuống (dropdown menu) |

### 1.9. Thẻ bọc chung (Generic Container)

> 💡 Ngoài các nhóm trên, không thể không nhắc tới `div` — đây là thẻ khối (block-level) phổ biến nhất dùng làm hộp chứa để gom nhóm các phần tử và dựng bố cục trang bằng CSS/JS.

---

## 2. Các Object trong BeautifulSoup

### 2.1. Các loại Object chính

- **`BeautifulSoup`** — object gốc, đại diện cho toàn bộ document HTML/XML sau khi parse. Là điểm bắt đầu để tìm kiếm mọi thẻ khác.

  ```python
  soup = BeautifulSoup(html_doc, 'html.parser')
  ```

- **`Tag`** — đại diện cho 1 thẻ HTML (ví dụ thẻ `div`, `a`, `p`). Đây là object dùng nhiều nhất khi trích xuất dữ liệu.

  ```python
  tag = soup.find('a')   # trả về 1 Tag object
  ```

- **`NavigableString`** — đại diện cho phần văn bản (text) nằm bên trong 1 thẻ (không phải thẻ, mà là nội dung chữ giữa thẻ mở và thẻ đóng).

  ```python
  tag.string   # trả về NavigableString
  ```

- **`Comment`** — kiểu con đặc biệt của `NavigableString`, đại diện cho comment HTML.
(<!-- ... -->).

- **`.prettify()`** show HTML structure as a tree
  ```python
  soup = BeautifulSoup(html, 'html5lib')
  print(soup.prettify())
  ```
  
### 2.2. Thuộc tính quan trọng của Tag Object

| Thuộc tính | Ý nghĩa |
|---|---|
| `.name` | Tên thẻ (ví dụ: `a`, `div`) |
| `.attrs` | Dictionary chứa toàn bộ thuộc tính của thẻ (ví dụ: `href`, `class`) |
| `.string` | Chuỗi text bên trong thẻ (nếu thẻ chỉ có 1 nội dung text duy nhất) |
| `.text` / `.get_text()` | Lấy toàn bộ text bên trong thẻ, kể cả các thẻ con lồng nhau |
| `.contents` | List các phần tử con, gồm cả Tag và NavigableString |
| `.children` | Iterator duyệt qua các phần tử con (tương tự `.contents` nhưng không tạo list) |
| `.descendants` | Iterator duyệt qua toàn bộ phần tử con cháu (đệ quy nhiều cấp) |
| `.parent` | Thẻ cha trực tiếp |
| `.next_sibling` / `.previous_sibling` | Thẻ/text liền kề cùng cấp (sau/trước) |

### 2.3. Phương thức tìm kiếm phổ biến

| Phương thức | Ý nghĩa |
|---|---|
| `.find(name, attrs, ...)` | Tìm thẻ đầu tiên khớp điều kiện |
| `.find_all(name, attrs, ...)` | Tìm tất cả thẻ khớp điều kiện, trả về list các Tag |
| `.select(css_selector)` | Tìm theo cú pháp CSS selector |
| `.get('href')` | Lấy giá trị 1 thuộc tính cụ thể của thẻ (tương đương `tag['href']`) |

> 🔑 **Tóm gọn:** `BeautifulSoup` = cả document → chứa nhiều `Tag` → mỗi `Tag` có thể chứa `Tag` con khác hoặc `NavigableString` (text thuần) → dùng `.find()` / `.find_all()` / `.select()` để duyệt tìm đúng `Tag` cần lấy dữ liệu.

---

## 3. Hướng dẫn cào dữ liệu web cơ bản với Python

Đoạn mã dưới đây hướng dẫn cách tải nội dung một trang web và trích xuất tất cả các đường liên kết (links) bằng hai thư viện phổ biến: `requests` và `BeautifulSoup`.

**Yêu cầu tiền đề (Prerequisites):**

```bash
pip install requests bs4
```

```python
# 1. Nhập (import) các thư viện cần thiết
import requests
from bs4 import BeautifulSoup

# 2. Khai báo URL của trang web bạn muốn cào dữ liệu text/image
url = "https://en.wikipedia.org/wiki/IBM"

# 3. Gửi một yêu cầu HTTP GET đến trang web để lấy dữ liệu về
response = requests.get(url)

# 3.1. Kiểm tra trạng thái của yêu cầu
response.status_code

# 3.2. Xem request headers
print(response.request.headers)
print(response.headers)  # trả về dictionary chứa các HTTP response headers

# 3.3. Xem request body
print(response.request.body)

# 3.4. Xem trường Date trong response headers
print(response.headers['Date'])

# 3.5. Xem trường Content-Type trong response headers
print(response.headers['Content-Type'])

# 3.6. Kiểm tra encoding của response
response.encoding

# 4. Lấy nội dung mã nguồn HTML thô (Raw HTML) từ phản hồi
html_content = response.text

# 5. Tạo một đối tượng BeautifulSoup để phân tích (parse) cú pháp HTML thành cấu trúc dạng cây (tree-like structure)
soup = BeautifulSoup(html_content, "html.parser")

# 6. In ra 500 ký tự đầu tiên của mã HTML để kiểm tra dữ liệu thô
print("--- 500 KÝ TỰ HTML ĐẦU TIÊN ---")
print(html_content[:500])
print("\n" + "=" * 50 + "\n")

# 7. Tìm tất cả các thẻ <a> (thẻ chứa đường dẫn/link) trong trang web
links = soup.find_all("a")

# 8. Duyệt qua từng thẻ <a> tìm được và in ra văn bản hiển thị (text) của link đó
print("--- DANH SÁCH VĂN BẢN TRONG CÁC THẺ LINK ---")
for link in links:
    # .strip() giúp loại bỏ các khoảng trắng thừa hoặc dòng trống
    # link.text: chỉ lấy phần chữ hiển thị người dùng nhìn thấy trên màn hình, loại bỏ toàn bộ thẻ tag HTML xung quanh
    text = link.text.strip()

    # Chỉ in ra nếu thẻ link đó có chứa văn bản (tránh in ra các dòng trống)
    if text:
        print(text)
```

---

## 4. Trích xuất dữ liệu bảng trên Web bằng pd.read_html

**Tổng quan:** Hàm `pd.read_html()` trong thư viện Pandas cho phép bạn tự động cào (scrape) tất cả các bảng dữ liệu (`table`) từ một trang web và chuyển đổi chúng thành các DataFrame.

> **Hình dung thực tế:** Nó giống như việc bạn copy một bảng dữ liệu từ trang web rồi dán trực tiếp vào Excel/Google Sheets chỉ bằng 1 dòng lệnh Python, sẵn sàng cho việc phân tích dữ liệu ngay lập tức!

### 4.1. Hàm chính — pd.read_html()

`pd.read_html(url_hoac_html)` — đọc file HTML hoặc đường dẫn URL, tự động tìm các thẻ `table` và trả về **một danh sách các DataFrame** (`List[DataFrame]`).

### 4.2. Các tham số thực hành quan trọng

| Tham số | Ý nghĩa & Cách dùng thực tế |
|---|---|
| `match` | Lọc bảng cần lấy dựa trên chữ/chuỗi có chứa trong bảng đó (VD: `match="Doanh thu"`) |
| `header` | Chỉ định dòng nào trong bảng làm tiêu đề cột (thường là `header=0`) |
| `index_col` | Chọn cột làm chỉ số (index) cho DataFrame |
| `flavor` | Động cơ phân tích HTML (mặc định dùng `lxml` hoặc `bs4`) |

### 4.3. Lưu ý

- **Kết quả trả về luôn là List:** `pd.read_html()` luôn trả về danh sách các bảng. Bạn cần dùng chỉ số index như `tables[0]`, `tables[1]` để truy cập từng bảng cụ thể.
- **Không cào được web có JavaScript động:** `read_html` chỉ đọc được mã HTML tĩnh gửi về từ server. Nếu bảng dữ liệu được tạo ra bằng JavaScript (React, Vue, AJAX...), nên dùng Selenium hoặc Playwright để tải trang trước khi dùng `read_html`.
- **Tránh bị chặn IP:** Nếu gặp lỗi `HTTP Error 403: Forbidden`, cần kết hợp thêm thư viện `requests` để giả lập trình duyệt (thêm headers).

**Yêu cầu cài đặt (Prerequisites):**

```bash
pip install pandas lxml html5lib bs4
```

```python
import pandas as pd

# 1. Đường dẫn trang Wikipedia về mùa giải Ngoại hạng Anh
url = "https://en.wikipedia.org/wiki/2023%E2%80%9324_Premier_League"

# 2. Dùng pandas đọc bảng có chứa chữ "Arsenal" để lọc đúng bảng xếp hạng
tables = pd.read_html(url, match="Arsenal")

# 3. Lấy bảng xếp hạng
df_bxh = tables[0]

# 4. Hiển thị 5 đội dẫn đầu
print("TOP 5 ĐỘI DẪN ĐẦU BẢNG XẾP HẠNG:")
print(df_bxh.head())

# 5. Lọc ra các cột quan trọng (Vị trí, Đội bóng, Số trận, Thắng, Hòa, Thua, Điểm)
# Dùng iloc để chọn cột theo thứ tự index
df_sach = df_bxh.iloc[:, [0, 1, 2, 3, 4, 5, 9]]

# Đổi tên cột sang tiếng Việt cho dễ đọc
df_sach.columns = ["Hạng", "Đội bóng", "ST", "Thắng", "Hòa", "Thua", "Điểm"]

print("\nBẢNG XẾP HẠNG ĐÃ ĐƯỢC LÀM SẠCH:")
print(df_sach.head(10))

# 6. Lưu kết quả ra file CSV
df_sach.to_csv("bxh_ngoai_hang_anh.csv", index=False, encoding="utf-8-sig")
print("\nĐã xuất thành công file 'bxh_ngoai_hang_anh.csv'!")
```

---

## 5. Xử lý HTTP Requests: GET vs POST

Hướng dẫn chi tiết về cách gửi **GET Request** (với URL Parameters) và **POST Request** (với Data Body) bằng thư viện `requests` trong Python, sử dụng dịch vụ thử nghiệm `httpbin.org`.

| Tiêu chí | HTTP GET | HTTP POST |
|---|---|---|
| Vị trí chứa dữ liệu | Đính trực tiếp trên URL dưới dạng Query String (`?key=value`) | Đóng gói bên trong Request Body (ẩn khỏi thanh địa chỉ) |
| Cấu trúc URL (`r.url`) | Thay đổi theo dữ liệu gửi đi (VD: `http://example.com/api?id=123`) | Giữ nguyên đường dẫn gốc (VD: `http://example.com/api`) |
| Thân yêu cầu (`r.request.body`) | `None` (không sử dụng body để truyền dữ liệu) | Chứa chuỗi dữ liệu gửi đi (VD: `id=123` hoặc chuỗi JSON) |
| Giới hạn dung lượng | Bị giới hạn bởi độ dài tối đa của URL (~2.048 ký tự) | Không giới hạn dung lượng truyền trong body |

### 5.1. GET Request với URL Parameters

Phương thức GET thường dùng để truy vấn hoặc lấy dữ liệu từ Server/API. Có thể truyền tham số qua URL bằng một chuỗi Query String (bắt đầu bằng dấu `?`, các cặp `key=value` nối nhau bằng dấu `&`).

```python
import requests

# 1. Khai báo URL gốc (Endpoint)
url_get = "http://httpbin.org/get"

# 2. Tạo dictionary chứa các tham số (Query parameters)
payload = {"name": "Joseph", "ID": "123"}

# 3. Gửi GET Request truyền dictionary vào tham số `params`
r = requests.get(url_get, params=payload)

# 4. Kiểm tra URL thực tế được tạo ra
print("URL hoàn chỉnh:", r.url)
# Output: http://httpbin.org/get?name=Joseph&ID=123

# 5. Kiểm tra Request Body (GET không có body)
print("Request body:", r.request.body)
# Output: None

# 6. Kiểm tra Mã trạng thái (Status Code)
print("Status code:", r.status_code)

# 7. Kiểm tra Content-Type của dữ liệu trả về
print("Content-Type:", r.headers["Content-Type"])

# 8. Giải mã dữ liệu JSON trả về thành Python Dictionary
data = r.json()

# Lấy các tham số đã gửi từ key 'args'
print("Dữ liệu args nhận được từ Server:", data["args"])
# Output: {'ID': '123', 'name': 'Joseph'}
```

### 5.2. POST Request với Data Body

Phương thức POST thường dùng để gửi dữ liệu lên Server/API nhằm tạo mới, cập nhật dữ liệu hoặc thực hiện các tác vụ như đăng nhập, gửi biểu mẫu (Form). Khác với GET, dữ liệu gửi đi không nằm trên URL mà được đóng gói an toàn bên trong Request Body dưới dạng các cặp `key-value`.

```python
import requests

# 1. Khai báo URL Endpoint cho POST
url_post = "http://httpbin.org/post"

# 2. Dữ liệu cần gửi
payload = {"name": "Joseph", "ID": "123"}

# 3. Gửi POST Request truyền dictionary vào tham số `data`
r_post = requests.post(url_post, data=payload)

# 4. Kiểm tra URL (URL giữ nguyên, không chứa query string)
print("POST request URL:", r_post.url)
# Output: http://httpbin.org/post

# 5. Kiểm tra Request Body (dữ liệu nằm ở đây)
print("POST request body:", r_post.request.body)
# Output: name=Joseph&ID=123

# 6. Kiểm tra dữ liệu Form được Server nhận diện
print("Form data nhận được:", r_post.json()["form"])
# Output: {'ID': '123', 'name': 'Joseph'}
```
## 6. Danh sách HTML Attributes

## 📑 Mục lục

- [6.1. Global Attributes (dùng được cho mọi thẻ)](#1-global-attributes-dùng-được-cho-mọi-thẻ)
- [6.2. Attributes cho Form & Input](#2-attributes-cho-form--input)
- [6.3. Attributes cho Link & Media](#3-attributes-cho-link--media)
- [6.4. Attributes cho Table](#4-attributes-cho-table)
- [6.5. Attributes cho Iframe & Script](#5-attributes-cho-iframe--script)
- [6.6. Event Handler Attributes (on*)](#6-event-handler-attributes-on)
- [6.7. Attributes cũ / không khuyến khích dùng (Deprecated)](#7-attributes-cũ--không-khuyến-khích-dùng-deprecated)

---

### 6.1. Global Attributes (dùng được cho mọi thẻ)

Nhóm attribute có thể gắn vào **bất kỳ thẻ HTML nào**, không phân biệt loại thẻ.

| Attribute | Ý nghĩa |
|---|---|
| `id` | Định danh duy nhất cho phần tử trong toàn trang |
| `class` | Gán một hoặc nhiều tên lớp (class), dùng để style bằng CSS hoặc chọn bằng JS |
| `style` | Gán CSS trực tiếp (inline style) |
| `title` | Chú thích hiển thị dạng tooltip khi rê chuột vào |
| `lang` | Khai báo ngôn ngữ nội dung (VD: `vi`, `en`) |
| `dir` | Hướng văn bản: `ltr` (trái sang phải) hoặc `rtl` (phải sang trái) |
| `tabindex` | Thứ tự focus khi nhấn phím Tab |
| `hidden` | Ẩn phần tử khỏi trang |
| `draggable` | Cho phép kéo-thả phần tử (`true`/`false`) |
| `contenteditable` | Cho phép người dùng chỉnh sửa trực tiếp nội dung (`true`/`false`) |
| `spellcheck` | Bật/tắt kiểm tra chính tả của trình duyệt |
| `translate` | Cho phép/không cho phép công cụ dịch tự động dịch nội dung |
| `accesskey` | Gán phím tắt để focus/kích hoạt phần tử |
| `data-*` | Attribute tùy chỉnh để lưu dữ liệu riêng (VD: `data-user-id`) |
| `role` | Khai báo vai trò ARIA cho hỗ trợ tiếp cận (accessibility) |
| `aria-*` | Nhóm attribute ARIA hỗ trợ trình đọc màn hình (VD: `aria-label`, `aria-hidden`) |
| `autocapitalize` | Điều khiển tự động viết hoa khi nhập trên thiết bị di động |
| `autofocus` | Tự động focus vào phần tử khi trang tải xong |
| `inert` | Vô hiệu hóa tương tác (không click/focus được) với cả cụm phần tử |
| `is` | Khai báo custom element kế thừa từ thẻ chuẩn |
| `itemid`, `itemprop`, `itemref`, `itemscope`, `itemtype` | Nhóm attribute hỗ trợ Microdata (structured data cho SEO) |
| `nonce` | Mã bảo mật dùng với Content Security Policy (CSP) |
| `part` | Đánh dấu phần tử để style từ bên ngoài Shadow DOM |
| `slot` | Gán phần tử vào 1 "khe" (slot) trong Web Component |
| `popover` | Khai báo phần tử là popover (HTML mới) |
| `inputmode` | Gợi ý loại bàn phím ảo hiển thị trên di động (VD: `numeric`, `email`) |

---

### 6.2. Attributes cho Form & Input

| Attribute | Ý nghĩa |
|---|---|
| `action` | URL nhận dữ liệu khi submit form |
| `method` | Phương thức gửi form: `get` hoặc `post` |
| `enctype` | Kiểu mã hóa dữ liệu khi submit (VD: `multipart/form-data` khi có upload file) |
| `name` | Tên trường dữ liệu, dùng làm key khi gửi lên server |
| `value` | Giá trị hiện tại của input |
| `placeholder` | Chữ gợi ý mờ hiển thị khi ô input còn trống |
| `required` | Bắt buộc phải nhập trước khi submit |
| `disabled` | Vô hiệu hóa phần tử, không thể tương tác |
| `readonly` | Chỉ đọc, không cho phép chỉnh sửa (nhưng vẫn gửi được giá trị) |
| `checked` | Đánh dấu checkbox/radio đã được chọn sẵn |
| `selected` | Đánh dấu option đã được chọn sẵn trong dropdown |
| `multiple` | Cho phép chọn nhiều giá trị (input file, select) |
| `maxlength` / `minlength` | Giới hạn số ký tự tối đa/tối thiểu được nhập |
| `min` / `max` / `step` | Giới hạn giá trị nhỏ nhất/lớn nhất và bước nhảy (cho input number, range, date) |
| `pattern` | Biểu thức chính quy (regex) để validate giá trị nhập |
| `autocomplete` | Bật/tắt gợi ý tự động điền của trình duyệt |
| `form` | Liên kết input với 1 form cụ thể theo `id`, dù input nằm ngoài thẻ `form` |
| `formaction`, `formmethod`, `formenctype`, `formnovalidate`, `formtarget` | Ghi đè thuộc tính của `form` cha, áp dụng riêng cho 1 nút submit |
| `list` | Liên kết input với 1 thẻ `datalist` (gợi ý nhập liệu) |
| `novalidate` | Tắt việc kiểm tra hợp lệ (validation) mặc định của trình duyệt khi submit |
| `accept` | Giới hạn loại file được chọn (input file), VD: `image/*` |
| `accept-charset` | Khai báo bảng mã ký tự chấp nhận khi submit form |

---

### 6.3. Attributes cho Link & Media

| Attribute | Ý nghĩa |
|---|---|
| `href` | Đường dẫn liên kết (dùng ở thẻ `a`, `link`) |
| `src` | Đường dẫn nguồn tài nguyên (ảnh, video, audio, script, iframe) |
| `alt` | Văn bản thay thế khi ảnh không tải được, hỗ trợ SEO và accessibility |
| `target` | Nơi mở liên kết: `_blank`, `_self`, `_parent`, `_top` |
| `rel` | Mối quan hệ giữa trang hiện tại và tài nguyên liên kết (VD: `nofollow`, `noopener`) |
| `download` | Cho phép tải file về thay vì mở trực tiếp |
| `hreflang` | Khai báo ngôn ngữ của trang được liên kết tới |
| `type` | Khai báo kiểu MIME của tài nguyên |
| `media` | Điều kiện media query áp dụng resource (VD: cho `link`, `source`) |
| `sizes` / `srcset` | Khai báo nhiều kích thước/độ phân giải ảnh khác nhau để responsive |
| `crossorigin` | Cấu hình chính sách CORS khi tải tài nguyên |
| `referrerpolicy` | Quy định thông tin referrer gửi kèm khi tải tài nguyên |
| `integrity` | Mã hash để kiểm tra tính toàn vẹn của file tải từ CDN |
| `loading` | Chế độ tải ảnh/iframe: `lazy` (tải khi cuộn tới) hoặc `eager` |
| `decoding` | Gợi ý cách trình duyệt giải mã ảnh: `sync`, `async`, `auto` |
| `poster` | Ảnh đại diện hiển thị trước khi video được phát |
| `controls` | Hiển thị thanh điều khiển cho audio/video |
| `autoplay` | Tự động phát audio/video khi tải trang |
| `loop` | Lặp lại audio/video liên tục |
| `muted` | Tắt tiếng mặc định |
| `preload` | Gợi ý cách tải trước media: `none`, `metadata`, `auto` |
| `playsinline` | Cho phép video phát ngay trong trang trên di động, không mở toàn màn hình |

---

### 6.4. Attributes cho Table

| Attribute | Ý nghĩa |
|---|---|
| `colspan` | Gộp 1 ô trải ngang qua nhiều cột |
| `rowspan` | Gộp 1 ô trải dọc qua nhiều hàng |
| `headers` | Liên kết ô dữ liệu (`td`) với ô tiêu đề (`th`) tương ứng, hỗ trợ accessibility |
| `scope` | Khai báo phạm vi của ô tiêu đề: `row`, `col`, `rowgroup`, `colgroup` |

---

### 6.5. Attributes cho Iframe & Script

| Attribute | Ý nghĩa |
|---|---|
| `sandbox` | Giới hạn quyền hạn của nội dung bên trong `iframe` (bảo mật) |
| `allow` | Khai báo các quyền trình duyệt được phép dùng trong `iframe` (camera, micro...) |
| `allowfullscreen` | Cho phép nội dung trong `iframe` mở toàn màn hình |
| `async` | Tải script bất đồng bộ, không chặn parse HTML |
| `defer` | Tải script song song nhưng chỉ thực thi sau khi parse HTML xong |
| `nomodule` | Chỉ chạy script này ở trình duyệt **không** hỗ trợ ES module |

---

### 6.6. Event Handler Attributes (on*)

Nhóm attribute gắn hành vi JavaScript trực tiếp vào thẻ HTML khi có sự kiện xảy ra (không khuyến khích dùng nhiều vì lẫn logic vào HTML, nhưng vẫn phổ biến trong ví dụ cơ bản).

| Nhóm sự kiện | Attribute tiêu biểu |
|---|---|
| Chuột (Mouse) | `onclick`, `ondblclick`, `onmouseover`, `onmouseout`, `onmousedown`, `onmouseup`, `onmousemove` |
| Bàn phím (Keyboard) | `onkeydown`, `onkeyup`, `onkeypress` |
| Form | `onsubmit`, `onreset`, `onchange`, `oninput`, `onfocus`, `onblur`, `oninvalid` |
| Trang / Cửa sổ (Window) | `onload`, `onunload`, `onresize`, `onscroll`, `onerror` |
| Kéo-thả (Drag & Drop) | `ondrag`, `ondragstart`, `ondragend`, `ondrop` |
| Media | `onplay`, `onpause`, `onended`, `onvolumechange` |

---

### 6.7. Attributes cũ / không khuyến khích dùng (Deprecated)

Các attribute này vẫn có thể hoạt động ở một số trình duyệt nhưng đã bị thay thế bằng CSS — **không nên dùng** trong dự án mới.

| Attribute | Đã bị thay thế bằng |
|---|---|
| `bgcolor` | CSS `background-color` |
| `align` | CSS `text-align` / `float` |
| `valign` | CSS `vertical-align` |
| `border` (trên thẻ `table`) | CSS `border` |
| `cellpadding`, `cellspacing` | CSS `padding`, `border-spacing` |
| `width`, `height` (trên thẻ layout như `table`, `td`) | CSS `width`, `height` |

> 🔑 **Ghi nhớ:** Nhóm **Global Attributes** (mục 1) là quan trọng nhất cần nhớ trước — vì gắn được vào mọi thẻ. Các nhóm còn lại chỉ áp dụng cho từng nhóm thẻ cụ thể (form, media, table...), nên học theo ngữ cảnh sẽ dễ nhớ hơn là học thuộc lòng toàn bộ danh sách.

## <a id="section-7"></a>7. Pagination (chia trang), Error handling, If __name__ = __main__

### 7.1. Pagination:
url = baseurl + endpoint + ?page=(number)

### 7.2. Error Handling:
a/ timeout
```python
import requests
from requests.exceptions import Timeout
baseurl = 'http://..........'
maxRetries = 3

for i in range(maxRetries):
  try: 
      response = requests.get(base_url, timeout = (number) )
      time.sleep(1.0)
      print(response.text)
      print(response.status_code)
      break
  except Timeout as to:
      print("Timeout")
```

### 7.3. Khối thực thi chạy thử:

### Khối thực thi chạy thử (ngay tại file gốc, main.py, còn nếu tái sử dụng hàm cào ở một nơi khác thì sẽ ko bị dính code thực thi thử vào, do biến __name__ != __main__ 
```python
import time

if __name__ = __main__:
          find_jops()
          df.to_csv()
          df.to_excel()
```

```python
def smart_sleep(min_s=1.2, max_s=2.8):
    # nghỉ ngẫu nhiên để “giống người”
    time.sleep(random.uniform(min_s, max_s))
```

```command line
python main.py
```
