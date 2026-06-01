# **PHẦN A - KIỂM TRA ĐỌC HIỂU**

**Câu A1:**
1. Inline CSS: CSS được viết trực tiếp trong thuộc tính `style` của thẻ HTML
```html
<body>
    <h1 style="color: blue; font-size: 40px;">Xin chào<h1>
</body>
```
- Ưu điểm:
    - Nhanh, đơn giản
    - Áp dụng ngay cho một phần tử cụ thể
    - Không cần tạo file CSS riêng
- Nhược điểm:
    - Khó bảo trì khi code lớn
    - Lặp lại nhiều mã CSS
    - làm HTML bị rối 
    - Không tái sử dụng được
- Khi nào nên dùng:
    - Test nhanh giao diện
    - Chỉnh style cho 1 phần tử duy nhất
    - Email HTML(Nhiều hệ thống email ưu tiên inline CSS)

2. Internal CSS: CSS được viết trong thẻ `<style>` bên trong file HTML.
```html
<head>
    ...
    <style>
        h1 {
            color: green;
            font-size: 40px;
        }

        p {
            color: gray;
        }
    </style>
</head>
```
- Ưu điểm:
    - Code gọn hơn inline
    - Quản lý style tập trung trong một file
    - Không cần tạo file CSS riêng
- Nhược điểm:
    - Không tái sử dụng giữa nhiều trang
    - File HTML sẽ lớn hơn khi CSS nhiều
    - Khó quản lý với dự án lớn
- Khi nào nên dùng:
    - Website nhỏ
    - Trang đơn (single page)
    - Demo hoặc bài tập học tập

3. External CSS: CSS được đặt trong file .css riêng và liên kết với HTML bằng thẻ `<link>`
```html
<head>
   ...
    <link rel="stylesheet" href="style.css">
</head>
```
Trong file `style.css`
```css
h1 {
    color: red;
    font-size: 40px;
}
p {
    color: gray;
}
```
- Ưu điểm:
    - Dễ bảo trì
    - Tái sử dụng cho nhiều trang
    - Code sạch và chuyên nghiệp
    - Tăng hiệu năng nhờ cache CSS
- Nhược điểm:
    - Cần thêm file CSS riêng
    - Nếu file CSS lỗi hoặc tải chậm thì giao diện bị ảnh hưởng
- Khi nào nên dùng:
    - Dự án thực tế
    - Website nhiều trang
    - Ứng dụng web lớn
    - Khi cần quản lý giao diện chuyên nghiệp

4. Khi cùng một element được áp dụng CSS bằng cả 3 cách (inline, internal, external), thì CSS sẽ được ưu tiên theo thứ tự:
- Inline CSS → ưu tiên cao nhất
- Internal CSS
- External CSS

Giải thích: Trình duyệt dùng cơ chế gọi là CSS Cascade (quy tắc phân tầng CSS). CSS sẽ xét:
- Nguồn CSS
- Độ ưu tiên (specificity)
- Thứ tự xuất hiện
=> Inline CSS được xem là cụ thể nhất vì nó gắn trực tiếp vào element.

**Câu A2**
- `h1` chọn `ShopTLU`. `<h1>ShopTLU</h1>`
- `.price` chọn `25.990.000đ` và `45.990.000đ`. `<p class="price">25.990.000đ</p>` và `<p class="price">45.990.000đ</p>`
- `#app header` chọn toàn bộ thẻ `<header>` bên trong `#app`, chứa: `ShopTLU` `Home` `Products` `About`.
- `nav a:first-child` chọn thẻ `<a>` đầu tiên trong `nav`. Chọn `<a href="/" class="active">Home</a>`
- `.product.featured h2` chọn thẻ `<h2>` nằm trong element có đồng thời class product và featured. Chọn `<h2>MacBook Pro</h2>`
- `article > p` chọn tất cả thẻ `<p>` là con trực tiếp của `<article>`. Chọn `<p class="price">25.990.000đ</p>` `<p>Mô tả sản phẩm...</p>` `<p class="price">45.990.000đ</p>` `<p>Mô tả sản phẩm...</p>`
- `a[href="/"]` chọn thẻ `<a>` có thuộc tính href="/". Chọn `<a href="/" class="active">Home</a>`
- `.top-bar.dark h1` chọn thẻ `<h1>` nằm bên trong element có đồng thời class top-bar và dark. Chọn  `<h1>ShopTLU</h1>`

**Câu A3**
1. Trường hợp 1:
```css
.box-1 {
    width: 400px;
    padding: 20px;
    border: 5px solid black;
    margin: 10px;
}
```
- Content box => width chỉ chiếm phần content
- Nên kích thước thực tế sẽ cộng thêm:
    - Padding trái + phải = 20 × 2 = 40px
    - Border trái + phải = 5 × 2 = 10px
- => Chiều rộng hiển thị: 400 + 40 + 10 = 450px
- Không gian chiếm trên trang: 
    - Cộng thêm margin trái phải = 10 × 2 = 20px
    - =>Tổng không gian chiếm: 450 + 20 = 470px
2. Trường hợp 2:
```css
.box-2 {
    box-sizing: border-box;
    width: 400px;
    padding: 20px;
    border: 5px solid black;
    margin: 10px;
}
```
- Với border-box: width đã bao gồm: content + padding + border
- => Tổng chiều rộng hiển thị luôn = 400px
- Kích thước content thực tế: 
    - Padding trái + phải = 40px
    - Border trái + phải = 10px
    - → Content thực tế = 400 - 40 -10 = 350px
- Không gian chiếm trên trang = 400 + 10*2 = 420px
3. Trường hợp 3
```css
.box-a { margin-bottom: 25px; }
.box-b { margin-top: 40px; }    
```
- Khoảng cách thực tế = 40px
- Trong CSS, margin theo chiều dọc có cơ chế: Margin Collapse. Hai margin dọc liền nhau sẽ không cộng lại mà trình duyệt sẽ lấy margin lớn hơn
- Tương tự,  Nếu .box-a có margin-bottom: -10px và .box-b có margin-top: 40px, khoảng cách = 40px vì cơ chế Margin collapse

**Câu A4**
1. Tính Specificity
- Rule A:
```css
p { color: black; }
```
- ID = 0 ; Class = 0 ; Tag p = 1 → Specificity(0,0,1)
- Rule B:
```css
.price { color: blue; }
```
- ID = 0 ; Class `.price` = 1 ; Tag p = 0 → Specificity(0,1,0) 
- Rule C:
```css
#main-price { color: red; }
```
- ID `main-price` = 1 ; Class = 0 ; Tag p = 0 → Specificity(1,0,0) 
- Rule D:
```css
p.price { color: green; }
```
- ID = 0 ; Class `price` = 1 ; Tag p = 1 → Specificity(0,1,1) 
2. Rule mạnh nhất là: (1,0,0) → Tức là Rule C. Kết quả  Element sẽ có màu đỏ(red). Vì ID selector có độ ưu tiên cao nhất
3. Nếu thêm inline style `<p class="price" id="main-price" style="color: orange;">`
- Element sẽ có màu cam(orange). Vì Inline style có độ ưu tiên cao hơn CSS thông thường (Inline style > ID selector)
4. Element sẽ có màu đen(black). Vì `!important` có ưu tiên cao hơn specificity thông thường. Thứ tự ưu tiên tổng quát
- !important
- Inline style
- ID selector
- Class selector
- Tag selector

# **PHẦN C - DEBUG & SUY LUẬN**
**Câu C1**
1. Chiều rộng thực tế của `sidebar` và `contentbox`:
```css
.sidebar {
    width: 300px;
    padding: 20px;
    border: 1px solid #ccc;
    float: left;
}
```
- Chiều rộng thực tế: 300 + 20 x 2 + 1 x 2 = 342px
```css
.content {
    width: 660px;
    padding: 30px;
    border: 1px solid #ccc;
    float: left;
}
```
- Chiều rộng thực tế: 660 + 30 x 2 + 1 x 2 = 722px
- Tổng chiều rộng: 342 + 722 = 1064px
- Trong khi `.container` chỉ rộng: 960px => => Hai phần tử không đủ chỗ nằm cùng hàng. Vì cả hai đều: `float: left;` nên browser sẽ đẩy `.content` xuống dòng mới.
2. Nguyên nhân layout bị vỡ:
- Do width trong content-box KHÔNG bao gồm padding và border
=> Nghĩa là: `width: 300px;` không phải tổng width thực tế là 300px. Browser phải cộng thêm: padding trái/phải và border trái/phải => tổng width vượt quá container.
3. Cách sửa:
- Dùng box-sizing: border-box
```css
* {
    box-sizing: border-box;
}
```
- Không dùng border-box: Phải tự trừ padding + border khỏi width.
    - Sidebar muốn tổng = 300px: content width = 300 - 40 - 2 = 258px
    - Content muốn tổng = 660px: content width = 660 - 60 - 2 = 598px
```css
.container {
    width: 960px;
    margin: 0 auto;
}
.sidebar {
    width: 258px;
    padding: 20px;
    border: 1px solid #ccc;
    float: left;
}
.content {
    width: 598px;
    padding: 30px;
    border: 1px solid #ccc;
    float: left;
}
```
4. Minh chứng
- Ban đầu
![alt text](image.png)
- Sửa theo cách 1:
![alt text](image-1.png)
- Sửa theo cách 2:
![alt text](image-2.png)

**Câu C2**
1. "Sản phẩm A" (h2) có font-size = 20px và color = green
- Font-size: Rule áp dụng:
```css
.card .title {font-size: 20px;}
```
- Color: Các rule liên quan: 
```css
#featured .title { color: red; }
.highlight { color: green !important; }
```
- So sánh: 
    - `#featured .title` specificity: 1-1-0
    - `.highlight` specificity: 0-1-0
    - Nhưng `.highlight` có: !important => !important thắng specificity thông thường.
2. "Mô tả sản phẩm" (p trong card featured) có color = blue
- Rule liên quan:
```css
.card {color: blue;}
.card p {color: inherit;}
```
- p có: color: inherit; => lấy color từ parent.
- Parent là: `<div class="card" id="featured">`
- `.card` có: color: blue; => p nhận màu xanh.
3. "Sản phẩm B" (h2) có font-size = 20px và color = blue
- Font-size:
```css
.card .title {font-size: 20px;}
```
- Color: Không có rule color trực tiếp cho `.title` => kế thừa từ .card.
```css
.card {color: blue;}
```
4. "Mô tả sản phẩm B" (p.highlight) có color = green
```css
.card p { color: inherit; }
.highlight { color: green !important; }
```
- Lấy color là green vì có !important
- Kết quả:



