
# 1. Khái niệm:
- HTTP là viết tắt của Giao thức Truyền tải Siêu văn bản (Hypertext Transfer Protocol), một giao thức nền tảng để truyền dữ liệu qua Internet, chủ yếu giữa trình duyệt web (client) và máy chủ (server). Nó cho phép người dùng truy cập và tải các tài nguyên như trang web HTML, hình ảnh, video và các loại nội dung khác trên World Wide Web. HTTP hoạt động theo mô hình yêu cầu-phản hồi và là nền tảng của mọi giao tiếp trên web, hoạt động thuộc tầng ứng dụng, trên cơ sở TCP/IP. Cổng mặc định mà HTTP sử dụng là 80.

- Nó hoạt động dựa trên cơ chế yêu cầu-phản hồi (request-response), cho phép các thiết bị kết nối với máy chủ để truy cập nội dung web. Tim Berners-Lee và nhóm làm việc tại CERN đã phát minh ra HTTP vào năm 1989 cùng với HTML, nhằm tạo nên nền tảng cho trình duyệt web đầu tiên.
- Ngày nay, HTTP vẫn là giao thức phổ biến nhất trên toàn cầu, hoạt động thông qua nền tảng TCP/IP, và được mở rộng với phiên bản bảo mật HTTPS, sử dụng mã hóa TLS (Transport Layer Security) để bảo vệ dữ liệu trong quá trình truyền tải.


Ví dụ: Khi bạn nhập một **URL (Uniform Resource Locator)**(ví dụ: `http://example.com`), trình duyệt sẽ gửi yêu cầu HTTP tới máy chủ, và máy chủ sẽ phản hồi lại nội dung trang web.

## 1.1 Các đặc trưng cơ bản của HTTP

- HTTP là giao thức connectionless (kết nối không liên tục) : ví dụ như HTTP Client khởi tạo 1 request, Client sẽ ngắt kết nối từ Server và đợi cho 1 phản hồi, Server xử lí request và thiết lập lại sự kết nối với Client để gửi phản hồi trở lại.
- HTTP là một phương tiện độc lập : Bất cứ loại dữ liệu nào cũng có thể được gửi bởi HTTP, miễn là Server và Client biết cách kiểm soát nội dung dữ liệu. Nó được yêu cầu cho Client cũng như Server để xác định kiểu nội dung bởi sử dụng kiểu MIME (Multipurpose Internet Mail Extensions - Giao thức mở rộng thư điện tử Internet đa mục đích) thích hợp.
- HTTP là stateless (không trạng thái) : Request hiện tại không biết những gì đã hoàn thành trong request trước đó.

## 1.2.HTTP Message

- Là cách để trao đổi dữ liệu giữa client và server.

- HTTP messeges gồm 3 phần là :Request Line , Header, Body

- HTTP Message có 2 loại:

   - REQUESTS
   - RESPONSES


# 2.What is in an HTTP request?

Yêu cầu HTTP là cách các nền tảng truyền thông Internet như trình duyệt web yêu cầu thông tin cần thiết để tải một trang web.

Mỗi yêu cầu HTTP được thực hiện trên Internet đều mang theo một chuỗi dữ liệu được mã hóa mang các loại thông tin khác nhau. Một yêu cầu HTTP thông thường bao gồm:
- HTTP version type
- a URL
- an HTTP method
- HTTP request headers
- Optional HTTP body(có thể có hoặc không)

![alt text](image-1.png)

# 3.Lịch sử và phiên bản
## Các cột mốc chính trong lịch sử HTTP
- 1990: Tim Berners-Lee tại CERN phát minh ra HTTP và xây dựng trình duyệt web đầu tiên, WorldWideWeb. Phiên bản đầu tiên, HTTP/0.9, ra đời với mục đích đơn giản hóa việc truy cập tài liệu. 
- 1996: Giới thiệu HTTP/1.0. Phiên bản này bổ sung nhiều tính năng quan trọng như hỗ trợ nhiều loại nội dung (hình ảnh, video, v.v.), các phương thức mới (POST, HEAD) và mã trạng thái để phản hồi từ server. 
- 1997: Ra mắt HTTP/1.1. Phiên bản này mang đến nhiều cải tiến về hiệu suất, bao gồm kết nối liên tục (pipelining), lưu trữ cache và hỗ trợ bảo mật. Đây là phiên bản tiêu chuẩn phổ biến nhất trong nhiều năm. 
- 2015: Công bố HTTP/2. Phiên bản này dựa trên công nghệ của SPDY từ Google, mang lại những cải tiến đáng kể về hiệu suất như đa luồng (multiplexing), nén header và hỗ trợ giao thức bảo mật TLS. 
- 2018: Phát hành HTTP/3. Phiên bản mới nhất này được xây dựng dựa trên giao thức QUIC (Quick UDP Internet Connections) thay vì TCP, giúp cải thiện tốc độ và hiệu suất kết nối, đặc biệt là trên mạng có độ trễ cao. 

## Các phiên bản HTTP

| Phiên bản    | Năm ra mắt                        | Đặc điểm chính                                                                                                                                                                                                           | Hạn chế / Cải tiến                                                                                                            |
| ------------ | --------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------- |
| **HTTP/1.0** | 1996                              | - Mỗi yêu cầu sử dụng **một kết nối TCP riêng biệt**. <br> - Dữ liệu truyền ở dạng **text** (văn bản thuần).                                                                                                             | ❌ Rất tốn tài nguyên vì phải **liên tục mở và đóng kết nối** cho mỗi file (HTML, ảnh, CSS...).                                |
| **HTTP/1.1** | 1997 (RFC 2068) → 2014 (RFC 7230) | - Hỗ trợ **Keep-Alive**, cho phép nhiều yêu cầu dùng chung một kết nối. <br> - Thêm tính năng **pipeline** (xử lý song song).                                                                                            | ⚠️ Các gói tin vẫn phải **trả về đúng thứ tự**, nên nếu một gói chậm sẽ làm nghẽn toàn bộ hàng đợi (*Head-of-line blocking*). |
| **HTTP/2**   | 2015                              | - Dữ liệu được **nén và truyền ở dạng nhị phân (binary)** thay vì text. <br> - Hỗ trợ **Multiplexing**: gửi **nhiều request song song** trong cùng một kết nối. <br> - Có thể **ưu tiên luồng dữ liệu**, **nén header**. | 🚀 Tốc độ nhanh hơn nhiều so với HTTP/1.1, giảm trễ mạng và tiết kiệm băng thông.                                             |
| **HTTP/3**   | ~2018 – nay                       | - Chuyển từ **TCP → UDP** với giao thức **QUIC (Quick UDP Internet Connections)**. <br> - Cải thiện tốc độ kết nối, giảm độ trễ. <br> - Mặc định **mã hóa (TLS 1.3)** để tăng bảo mật.                                   | ✅ Kết nối nhanh hơn, **ổn định hơn khi mất gói tin**, đặc biệt tốt cho thiết bị di động.                                      |

# 4. URL(Uniform Resource Locator)

- URL = “địa chỉ” của tài nguyên trên Internet.
- Giúp xác định và truy cập vào tài nguyên qua giao thức xác định (HTTP, HTTPS, FTP,...).
- Là phần quan trọng trong mọi HTTP request.

Cấu trúc URL:

    protocol://hostname:port/path-and-file-name

VÍ DỤ:

    https://www.example.com:443/path/page.html?name=quang#section2
    

Trong đó:

| Thành phần                                    | Mô tả                                                                                               |
| --------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| **https://**                                  | **Giao thức (Protocol)** – cho biết cách trình duyệt và máy chủ giao tiếp (HTTP, HTTPS, FTP, v.v.). |
| **[www.example.com](http://www.example.com)** | **Tên miền (Domain name)** – định danh máy chủ chứa tài nguyên.                                     |
| **:443**                                      | **Cổng (Port)** – chỉ định cổng mà server lắng nghe (HTTP mặc định là 80, HTTPS là 443).            |
| **/path/page.html**                           | **Đường dẫn (Path)** – chỉ ra vị trí cụ thể của tài nguyên trên server.                             |
| **?name=quang**                               | **Chuỗi truy vấn (Query string)** – chứa tham số được gửi đến server.                               |
| **#section2**                                 | **Phần neo (Fragment)** – tham chiếu đến một phần cụ thể trong trang.                               |

# 5. Phương thức HTTP (HTTP Methods)

HTTP hỗ trợ nhiều phương thức yêu cầu khác nhau, mỗi phương thức có mục đích riêng trong việc xử lý tài nguyên trên máy chủ:
- GET: Yêu cầu truy xuất tài nguyên từ máy chủ (ví dụ: tải một trang web).
- POST: Gửi dữ liệu đến máy chủ để tạo mới hoặc cập nhật tài nguyên(thường dùng trong form đăng ký, đăng nhập, upload file, v.v.).
- PUT: Tương tự POST, nhưng thường dùng để cập nhật toàn bộ tài nguyên.
- DELETE: Xóa tài nguyên trên máy chủ.
- HEAD: Tương tự GET nhưng không trả về phần nội dung chính của tài nguyên, chỉ trả về các tiêu đề.
- PATCH: Cập nhật một phần tài nguyên (khác với PUT cập nhật toàn bộ).
- OPTIONS: Lấy thông tin về các phương thức HTTP mà máy chủ hỗ trợ cho tài nguyên cụ thể.

# 6.HTTP Request:
- Request Line: Dòng lệnh chính (phương thức, tài nguyên, phiên bản HTTP).

![alt text](image-3.png)
- Request Headers: Các thông tin bổ sung

  - Tiêu đề HTTP chứa thông tin văn bản được lưu trữ theo cặp key-value và được bao gồm trong mọi yêu cầu HTTP (và phản hồi, sẽ nói thêm về điều này sau). Các tiêu đề này truyền đạt thông tin cốt lõi, chẳng hạn như trình duyệt mà máy khách đang sử dụng và dữ liệu nào đang được yêu cầu.

![alt text](image-2.png)

| Header                                                  | Ý nghĩa                                             | Giải thích cụ thể                                                                                     |
| ------------------------------------------------------- | --------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| **:authority: [www.google.com](http://www.google.com)** | Tên miền (Host) của server mà client muốn truy cập. | Giống như header `Host:` trong HTTP/1.1. Nó xác định địa chỉ của máy chủ nhận yêu cầu.                |
| **:method: GET**                                        | Phương thức HTTP.                                   | Yêu cầu trình duyệt **lấy dữ liệu** từ máy chủ (ở đây là trang chủ `/` của Google).                   |
| **:path: /**                                            | Đường dẫn tài nguyên trên server.                   | `/` nghĩa là **trang gốc** của website (home page). Nếu là `/search`, tức là truy cập trang tìm kiếm. |
| **:scheme: https**                                      | Giao thức truyền tải.                               | Cho biết kết nối đang dùng **HTTPS** (bảo mật qua TLS), chứ không phải HTTP thông thường.             |
| **accept: text/html**                                   | Loại nội dung mà client muốn nhận.                  | Trình duyệt mong muốn nhận **dữ liệu HTML** (trang web).                                              |
| **accept-encoding: gzip, deflate, br**                  | Các dạng nén dữ liệu mà client có thể hiểu.         | Giúp server **nén dữ liệu** trước khi gửi để tiết kiệm băng thông.                                    |
| **accept-language: en-US,en;q=0.9**                     | Ngôn ngữ ưa thích của client.                       | Client muốn nội dung bằng tiếng Anh (Mỹ). `q=0.9` là “độ ưu tiên”.                                    |
| **upgrade-insecure-requests: 1**                        | Đề nghị server nâng cấp kết nối HTTP → HTTPS.       | Cho biết client **ưu tiên** kết nối bảo mật.                                                          |
| **user-agent: Mozilla/5.0**                             | Thông tin về trình duyệt và hệ điều hành.           | Cho server biết client là **trình duyệt web kiểu Mozilla/Chrome/Edge**, giúp server phản hồi phù hợp. |

- Request Body (tuỳ chọn):là phần chứa "phần thân" thông tin mà yêu cầu đang truyền tải. Phần thân của một yêu cầu HTTP chứa bất kỳ thông tin nào được gửi đến máy chủ web, chẳng hạn như tên người dùng và mật khẩu, hoặc bất kỳ dữ liệu nào khác được nhập vào biểu mẫu.

# 7. HTTP response

là những gì máy khách web (thường là trình duyệt) nhận được từ máy chủ Internet để trả lời một yêu cầu HTTP. Những phản hồi này truyền đạt thông tin có giá trị dựa trên những gì được yêu cầu trong yêu cầu HTTP.

Một phản hồi HTTP thông thường bao gồm:

- mã trạng thái HTTP
- Tiêu đề phản hồi HTTP
- Nội dung HTTP tùy chọn

![alt text](image-5.png)

**Mã trạng thái HTTP** là mã gồm 3 chữ số thường được sử dụng để biểu thị yêu cầu HTTP đã được hoàn tất thành công hay chưa. Mã trạng thái được chia thành 5 khối sau:

- 1xx Thông tin
- 2xx Thành công
- 3xx Chuyển hướng
- 4xx Lỗi máy khách
- 5xx Lỗi máy chủ

Chữ "xx" biểu thị các số khác nhau từ 00 đến 99.

Mã trạng thái bắt đầu bằng số '2' biểu thị thành công. Ví dụ: sau khi máy khách yêu cầu một trang web, các phản hồi thường thấy nhất có mã trạng thái là '200 OK', biểu thị yêu cầu đã được hoàn tất thành công.

Nếu phản hồi bắt đầu bằng '4' hoặc '5', điều đó có nghĩa là đã xảy ra lỗi và trang web sẽ không được hiển thị. Mã trạng thái bắt đầu bằng '4' biểu thị lỗi phía máy khách (rất thường gặp mã trạng thái '404 NOT FOUND' khi nhập sai URL). Mã trạng thái bắt đầu bằng '5' nghĩa là đã xảy ra lỗi ở phía máy chủ. Mã trạng thái cũng có thể bắt đầu bằng '1' hoặc '3', tương ứng biểu thị phản hồi thông tin và chuyển hướng.

![alt text](image-6.png)

Tương tự như yêu cầu HTTP, phản hồi HTTP cũng đi kèm với các tiêu đề truyền tải thông tin quan trọng như ngôn ngữ và định dạng của dữ liệu được gửi trong nội dung phản hồi.

| Header                                       | Ý nghĩa                                                                                                   |
| -------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| **cache-control: private, max-age=0**        | Chỉ cho phép lưu trong cache riêng của người dùng, và chỉ lưu tối đa 0 giây (tức là hầu như không cache). |
| **content-encoding: br**                     | Phản hồi được nén bằng thuật toán Brotli để giảm dung lượng truyền tải.                                   |
| **content-type: text/html; charset=UTF-8**   | Nội dung trả về là một trang web HTML, sử dụng bảng mã UTF-8.                                             |
| **date: Thu, 21 Dec 2017 18:25:08 GMT**      | Thời điểm máy chủ gửi phản hồi.                                                                           |
| **status: 200**                              | Mã trạng thái cho biết yêu cầu đã **thành công**.                                                         |
| **strict-transport-security: max-age=86400** | Kích hoạt HTTPS trong 86400 giây (1 ngày) để đảm bảo kết nối an toàn.                                     |
| **x-frame-options: SAMEORIGIN**              | Ngăn chặn việc trang web bị nhúng trong iframe của website khác (chống clickjacking).                     |


- **HTTP response body**:
HTTP response thành công cho các yêu cầu "GET" thường có phần nội dung chứa thông tin được yêu cầu. Trong hầu hết các yêu cầu web, đây là dữ liệu HTML mà trình duyệt web sẽ dịch thành trang web.

# 8.Lỗi thường gặp khi duyệt HTTP

Khi duyệt HTTP, người dùng thường gặp phải một số lỗi phổ biến, mà dưới đây là những lỗi thường gặp cùng với nguyên nhân và cách khắc phục:
## 8.1. HTTP 404 Not Found

![alt text](image-7.png)

- Mô tả: Đây là một trong những lỗi phổ biến nhất khi duyệt web. Thông báo lỗi này xuất hiện khi trình duyệt không thể tìm thấy trang mà bạn đang cố gắng truy cập.
- Nguyên nhân:
   - Địa chỉ URL bị sai (như sai chính tả hoặc thiếu phần nào đó).
   - Trang web đã bị xóa hoặc di chuyển.
   - Tên miền không chính xác.
- Cách khắc phục:
   - Reload lại trang để kiểm tra xem lỗi có còn xảy ra không.
Kiểm tra và sửa lỗi chính tả trong địa chỉ URL.
Thử xóa bớt các phần trong URL để tìm ra phần còn hoạt động. Ví dụ: nếu bạn có URL `http://example.com/category/product/1/`, hãy thử `http://example.com/category/` hoặc `http://example.com/`.
## 8.2. HTTP 500 Internal Server Error

![alt text](image-8.png)

- Mô tả: Lỗi này cho biết có vấn đề xảy ra bên trong máy chủ khi xử lý yêu cầu.
- Nguyên nhân:
   - Máy chủ gặp sự cố tạm thời.
   - Lỗi cấu hình trên máy chủ.
   - Vấn đề với mã lập trình trên máy chủ.
- Cách khắc phục:
   - Reload lại trang để xem lỗi có còn xuất hiện không.
   - Nếu vẫn xảy ra lỗi, hãy thử truy cập trang vào thời điểm khác hoặc liên hệ với quản trị viên của trang web để thông báo về lỗi.

## 8.3. HTTP 403 Forbidden

![alt text](image-9.png)

- Mô tả: Lỗi này xảy ra khi máy chủ từ chối yêu cầu của bạn, nghĩa là bạn không có quyền truy cập vào tài nguyên bạn đang cố gắng truy cập.
- Nguyên nhân:
    - URL có thể bị sai, dẫn đến yêu cầu không hợp lệ.
    - Máy chủ có thể đã đặt giới hạn truy cập cho người dùng hoặc IP của bạn.
- Cách khắc phục:
    - Kiểm tra lại chính tả trong URL để đảm bảo nó là chính xác.
    - Nếu URL chính xác, bạn cần liên hệ với quản trị viên của trang web để yêu cầu quyền truy cập.


# 9. Cấu trúc cơ bản của HTTP
HTTP là giao thức hoạt động dựa trên mô hình yêu cầu-phản hồi giữa máy khách (client) và máy chủ (server). Khi người dùng nhập một URL, trình duyệt (client) gửi yêu cầu tới máy chủ chứa nội dung đó và máy chủ sẽ phản hồi với dữ liệu được yêu cầu.

Cấu trúc cơ bản của một yêu cầu HTTP bao gồm các thành phần chính sau:

![alt text](image.png)

1. Web Client
- Là người gửi yêu cầu (client): thường là trình duyệt (Chrome, Firefox...), nhưng cũng có thể là ứng dụng mobile, script, bot, curl, v.v.
- Gửi các HTTP Request (GET, POST, PUT, DELETE...) tới Web Server qua Internet.
- Hiển thị hoặc xử lý HTTP Response nhận về (HTML, JSON, ảnh...).
2. Đường chia (HTTP Protocol)
- Dọc ở giữa biểu thị ranh giới giao thức giữa client và server — mọi trao đổi qua lại đều theo quy ước HTTP/HTTPS (các request/response, header, status codes).
- Khi dùng HTTPS, lớp SSL/TLS bọc quanh HTTP.
3. Web Server
- Nhận request từ client (qua cổng 80 cho HTTP, 443 cho HTTPS).
- Có thể trực tiếp trả file tĩnh (HTML, CSS, JS, hình ảnh) hoặc chuyển request vào một server-side script / application để xử lý business logic.
- Ví dụ: Apache, Nginx, IIS, hoặc reverse-proxy (cũng có thể làm load-balancing).
4. Server Side Script (Application Layer)
- Là mã phía server thực hiện xử lý: routing, xác thực người dùng, xử lý form, truy vấn DB, gọi API khác, render trang.
- Ngôn ngữ: PHP, Node.js, Python (Django/Flask), Java (Spring), Ruby on Rails, v.v.
- Sau khi xử lý xong, script trả về một HTTP Response (có body + headers) cho Web Server rồi gửi về client.
5. Database
- Lưu trữ dữ liệu (user, products, posts...). Server-side script gửi truy vấn (SQL/NoSQL) để đọc/ghi.
- Có thể là MySQL, PostgreSQL, MongoDB, Redis, v.v.
- Thông tin trả về được server-side script xử lý trước khi trả response cho client.

