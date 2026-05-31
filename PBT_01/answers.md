PHẦN A
Câu A1
1. Các bước xảy ra khi gõ https://shopee.vn và nhấn Enter:
- Request đi qua router WiFi nhà trọ
- Request chạy qua mạng lưới Internet đến data center chứa Server (máy chủ) của Shopee
- Server của Shopee tiếp nhận HTTP Request, xử lý yêu cầu
- Server trả về một HTTP Response chạy ngược lại qua mạng Internet về thiết bị của toi
- Trình  nhận file HTML, CSS, JS → render ra giao diện 
Nguồn tham chiếu: File 01_introduction_html_universe.md — Phần Cuộc Hành Trình 0.3 Giây Xuyên Đại Dương và phần 1.3. Browser Rendering — Từ Code thành Hình ảnh.

2.  Tab Network hiển thị toàn bộ lịch sử các HTTP requests và responses diễn ra trong quá trình tải trang. Nó cho biết các file nào đang được tải về, dung lượng bao nhiêu, tốn bao nhiêu thời gian (thời gian tải), HTTP method là gì và Status code (thành công hay lỗi). Công cụ này thường dùng để kiểm tra xem file nào làm website tải chậm nhất hoặc request API nào bị lỗi.
Nguồn tham chiếu: File 01_introduction_html_universe.md — Phần 4.3. Developer Tools (F12) — "Kính hiển vi" cho website.

Câu A2
- Lỗi 1: Không dùng các thẻ cấu trúc (Landmark Tags). Việc dùng <div class="header">, <div class="main">, <div class="footer"> không giúp trình duyệt hiểu được đâu là phần đầu trang, nội dung chính hay chân trang. Cần thay bằng <header>, <main>, <footer>.
- Lỗi 2: Không dùng thẻ điều hướng cho Menu. Menu chứa các link quan trọng để bot Google bò (crawl) khắp trang web, nhưng lại dùng <div>. Cần thay bằng thẻ <nav>.
- Lỗi 3: Thiếu thẻ Heading cho tiêu đề. Tiêu đề sản phẩm dùng <div class="title"> là sai lầm lớn về SEO. Bot Google tìm kiếm các thẻ từ <h1> đến <h6> để hiểu nội dung chính của trang. Cần thay bằng <h1> hoặc <h2>.
- Lỗi 4: Thẻ <img> thiếu thuộc tính alt. Google không có mắt để xem ảnh, nó chỉ đọc chữ. Thiếu thuộc tính alt (mô tả ảnh) sẽ làm mất hoàn toàn điểm SEO hình ảnh và ảnh hưởng nghiêm trọng đến Accessibility.
Sửa lại code: 
<header>
    <div class="logo">ShopTLU</div>
    <nav class="menu">
        <ul>
            <li><a href="/">Trang chủ</a></li>
            <li><a href="/products">Sản phẩm</a></li>
        </ul>
    </nav>
</header>

<main>
    <article class="product">
        <h1 class="title">iPhone 16 Pro</h1>
        <div class="price">25.990.000đ</div>
        <div class="image"><img src="iphone.jpg" alt="Điện thoại iPhone 16 Pro"></div>
    </article>
</main>

<footer>© 2026 ShopTLU</footer>

Câu A3
Hộp 1
Text A Text B
Hộp 2
Text C Text D
Hộp 3

Bố cục trên được tạo ra do sự khác biệt giữa hai loại thẻ HTML: Block-level và Inline.
- Thẻ <div> là thẻ dạng Block. Đặc tính của thẻ Block là nó sẽ chiếm toàn bộ chiều rộng (100% width) của phần tử chứa nó và luôn bắt đầu trên một dòng mới. Do đó, "Hộp 1", "Hộp 2", và "Hộp 3" đều đứng một mình một dòng và đẩy các phần tử khác xuống dưới.
- Thẻ <span> và <strong> là các thẻ dạng Inline. Đặc tính của thẻ Inline là nó chỉ chiếm đúng một khoảng không gian bằng với nội dung bên trong nó và không tự động xuống dòng. Vì vậy, "Text A" và "Text B" sẽ xếp cạnh nhau trên cùng một dòng. Tương tự, "Text C" và "Text D" cũng nằm cạnh nhau cho đến khi bị thẻ <div> tiếp theo đẩy xuống.

Câu A4
1. Giải thích sự khác nhau giữa <thead>, <tbody>, <tfoot>:
Đây là 3 thẻ dùng để phân nhóm cấu trúc một bảng (Table) cho rõ ràng và chuẩn Semantic:

<thead> (Table Head): Nhóm phần tiêu đề của bảng (các cột). Thường chứa các thẻ <tr> và <th> (Table Heading).

<tbody> (Table Body): Nhóm phần nội dung chính của bảng, chứa các dữ liệu thực tế (các hàng). Thường chứa <tr> và <td>.

<tfoot> (Table Foot): Nhóm phần chân bảng, thường dùng để chốt lại vấn đề, hiển thị hàng tổng kết, tính tổng số lượng/giá tiền.
(Lưu ý: Dù viết <tfoot> ở đâu trong HTML, trình duyệt vẫn luôn render nó ở dưới cùng của bảng).

2. Tại sao KHÔNG NÊN dùng table để tạo layout trang web? (3 lý do):
Ngày xưa (những năm 2000), lập trình viên thường dùng <table> để chia cột layout, nhưng hiện nay điều này là tối kỵ vì:

Không Responsive (Kém linh hoạt): Table rất cứng nhắc. Rất khó để một layout bằng table có thể tự động co giãn, xếp lại cột để hiển thị đẹp mắt trên màn hình điện thoại hay máy tính bảng.

Tệ cho Accessibility và SEO: Trình đọc màn hình (Screen Readers) sẽ đọc layout theo cấu trúc hàng/cột (vd: "Hàng 1 cột 1, Hàng 1 cột 2..."), khiến người dùng khiếm thị vô cùng bối rối. Bot Google cũng không hiểu được đâu là nội dung chính, đâu là sidebar nếu tất cả đều nằm trong thẻ <td>.

Code phình to (Spaghetti Code) & Khó bảo trì: Để chia các bố cục phức tạp, bạn sẽ phải lồng ghép (nest) hàng chục thẻ <table>, <tr>, <td> vào nhau. Điều này làm file HTML trở nên rất nặng, rối rắm và cực kỳ khó sửa lỗi sau này. (Hiện nay, người ta dùng CSS Flexbox hoặc Grid để làm layout).

Phần C
Câu C1:
<header>
    <nav aria-label="main-navigation">
        <ul>
            <li><a href="/">Trang chủ</a></li>
            <li><a href="/category">Danh mục</a></li>
        </ul>
    </nav>
</header>

<main>
    <nav aria-label="breadcrumb">
        <ol>
            <li><a href="/">Trang chủ</a></li>
            <li><a href="/dien-thoai">Điện thoại</a></li>
            <li aria-current="page">iPhone 16 Pro</li>
        </ol>
    </nav>

    <article>
        <section class="product-gallery">
            <figure>
                <img src="main-image.jpg" alt="Mặt trước iPhone 16 Pro">
            </figure>
            <ul class="thumbnails">
                <li><img src="thumb1.jpg" alt="Mặt sau"></li>
                <li><img src="thumb2.jpg" alt="Cạnh bên"></li>
                <li><img src="thumb3.jpg" alt="Camera"></li>
                <li><img src="thumb4.jpg" alt="Màu sắc"></li>
            </ul>
        </section>

        <section class="product-info">
            <h1>iPhone 16 Pro 256GB</h1>
            <p class="price">25.990.000đ</p>
            <div class="rating" aria-label="Đánh giá 4.5 trên 5 sao">⭐⭐⭐⭐✨</div>
            <p class="description">Mô tả ngắn gọn về sản phẩm...</p>
        </section>

        <section class="technical-specs">
            <h2>Thông số kỹ thuật</h2>
            <table>
                <tbody>
                    <tr>
                        <th scope="row">Màn hình</th>
                        <td>6.1 inch, Super Retina XDR</td>
                    </tr>
                </tbody>
            </table>
        </section>

        <section class="reviews">
            <h2>Đánh giá từ khách hàng</h2>
            <article class="user-review">
                <h3>Nguyễn Văn A</h3>
                <p>Máy mượt, chụp ảnh đẹp!</p>
            </article>
        </section>
    </article>

    <aside class="related-products">
        <h2>Sản phẩm tương tự</h2>
        <ul>
            <li><a href="/iphone-15">iPhone 15 Pro</a></li>
            <li><a href="/samsung-s24">Samsung Galaxy S24</a></li>
        </ul>
    </aside>
</main>

<footer>
    <p>&copy; 2026 ShopTLU. All rights reserved.</p>
</footer>

Câu C2
- Việc lạm dụng <div> (hội chứng Divitis) có thể tiết kiệm chút thời gian ban đầu khi code, nhưng lại tạo ra một "mớ bòng bong" về mặt kỹ thuật, gây thiệt hại lớn cho dự án ở hai khía cạnh: SEO và Accessibility (Khả năng tiếp cận).

- Về SEO, các bộ máy tìm kiếm như Google dựa vào Semantic HTML để hiểu cấu trúc và mức độ quan trọng của nội dung. Một trang web toàn <div> giống như một cuốn sách không có mục lục hay tiêu đề chương. Khi bạn dùng <article> cho bài viết và <h1> cho tiêu đề, bot Google sẽ lập tức hiểu trọng tâm của trang nằm ở đâu, từ đó xếp hạng website tốt hơn so với một biển <div class="title"> vô nghĩa.

- Về Accessibility, trình đọc màn hình (Screen Reader) dành cho người khiếm thị phụ thuộc hoàn toàn vào các thẻ Semantic (Landmark tags) để điều hướng. Nếu bạn dùng <nav>, <main>, <footer>, người dùng có thể bấm phím tắt để nhảy thẳng đến phần nội dung họ muốn. Nếu chỉ dùng <div>, họ sẽ phải nghe máy đọc từng dòng code từ trên xuống dưới một cách cực hình.

- Ví dụ cụ thể: Nếu bạn dùng <div class="button" onclick="submit()">Gửi</div>, bạn phải viết thêm CSS để nó trông giống nút bấm, và viết thêm JavaScript để nó phản hồi phím Enter/Space khi người dùng dùng bàn phím (Tab) để lướt web. Ngược lại, nếu dùng đúng chuẩn <button>Gửi</button>, trình duyệt đã tự động cung cấp sẵn toàn bộ các tính năng hiển thị, focus bàn phím và tương tác mặc định.

- Trường hợp  vẫn phù hợp: Thẻ <div> không hề xấu, nó chỉ nên được dùng đúng mục đích: nhóm các phần tử lại phục vụ thuần túy cho layout hoặc CSS. Ví dụ, bạn cần tạo một <div class="container-flex"> để căn giữa các thẻ <article> bên trong, hoặc một thẻ bao bọc (wrapper) để đổ bóng (box-shadow) cho một nhóm nội dung mà nhóm đó không mang thêm ý nghĩa ngữ nghĩa nào cả.

Bài B3 — Debug HTML

Lỗi 1: Dòng 1 — Khai báo DOCTYPE sai cú pháp. — Cách sửa: Đổi <!DOCTYPE> thành <!DOCTYPE html>. Nên tách <html> và <head> xuống dòng cho dễ nhìn và thêm thuộc tính lang="vi" vào thẻ <html>.

Lỗi 2: Dòng 2 — Thẻ <title> thiếu thẻ đóng. — Cách sửa: Thêm </title> vào cuối dòng (sửa thành <title>Trang web</title>).

Lỗi 3: Dòng 3 — Thuộc tính charset sai giá trị chuẩn (thiếu dấu gạch ngang). — Cách sửa: Đổi utf8 thành utf-8 (hoặc UTF-8).

Lỗi 4: Dòng 4 — Thẻ đóng của <h1> sai cú pháp (thiếu dấu gạch chéo) và bị đặt ngoài thẻ <header> (lỗi cấu trúc ngữ nghĩa). — Cách sửa: Sửa thành </h1> và nên di chuyển dòng này vào bên trong cặp thẻ <header> cùng với thanh điều hướng.

Lỗi 5: Dòng 8 — Thẻ đóng của liên kết <a> sai cú pháp (viết thiếu dấu /). — Cách sửa: Đổi <a> ở cuối dòng thành </a>.

Lỗi 6: Dòng 15 (và Dòng 22) — Lỗi Semantic nhảy cóc cấp độ Heading (từ <h1> của trang nhảy thẳng xuống <h3>, bỏ qua <h2>). — Cách sửa: Đổi thẻ <h3> thành <h2>.

Lỗi 7: Dòng 16 — Thẻ <img> thiếu dấu ngoặc kép ở giá trị thuộc tính src và thiếu thuộc tính bắt buộc alt (lỗi Accessibility/SEO). — Cách sửa: Viết chuẩn lại thành <img src="iphone.jpg" alt="Hình ảnh iPhone 16 Pro">.

Lỗi 8: Dòng 18 — Lỗi lồng thẻ (nesting) chồng chéo giữa <b> và <p>. Thẻ nào mở sau phải được đóng trước. — Cách sửa: Đổi <b>25.990.000đ</p></b> thành <b>25.990.000đ</b></p>.

Lỗi 9: Dòng 24 đến 27 — Lỗi Semantic bảng: Hàng tiêu đề của bảng lại sử dụng thẻ dữ liệu <td> thay vì thẻ tiêu đề <th>. (Bảng cũng thiếu các thẻ nhóm cấu trúc như <thead>, <tbody>). — Cách sửa: Đổi <td>Tên</td> thành <th>Tên</th> (tương tự cho cột Giá) và bọc lại bảng bằng <thead>, <tbody>.

Lỗi 10: Dòng 36 — Lỗi Semantic: Một tài liệu HTML chỉ được phép có duy nhất một thẻ <main> để chỉ định nội dung chính. Phần "Sidebar" không được dùng <main>. — Cách sửa: Đổi cặp thẻ <main> thứ hai thành thẻ <aside>.

Lỗi 11: Dòng 41 — Thẻ đoạn văn <p> thiếu thẻ đóng. — Cách sửa: Sửa thành <p>Copyright 2026</p>.