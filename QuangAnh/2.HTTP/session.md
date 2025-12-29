#  Session

 **Session (phiên làm việc)** là cơ chế giúp ghi nhớ trạng thái của người dùng trên một website trong suốt phiên tương tác. Thông thường, khi người dùng truy cập vào trang web, server sẽ tạo một phiên làm việc mới và gán cho phiên đó một mã định danh phiên (Session ID) duy nhất . Vì giao thức HTTP nguyên bản là stateless (mỗi yêu cầu độc lập), session giúp server lưu trữ tạm thời thông tin như trạng thái đăng nhập, nội dung giỏ hàng, tùy chọn người dùng… để phục vụ các yêu cầu sau đó một cách nhất quán. Dữ liệu của session được lưu trữ trên phía server (không lưu trữ trực tiếp trên trình duyệt), nên an toàn hơn cho thông tin nhạy cảm

## 1.Cơ chế hoạt động của Session

![alt text](/QuangAnh/HTTP/image/image-10.png)

- Khởi tạo phiên (Session bắt đầu): Khi người dùng gửi yêu cầu đầu tiên (ví dụ đăng nhập hoặc vào trang web), server sẽ tạo một phiên làm việc mới và phát sinh một Session ID duy nhất cho phiên đó.
- Lưu trữ dữ liệu (Server-side): Tất cả dữ liệu liên quan đến phiên (ID người dùng, trạng thái đăng nhập, giỏ hàng, tùy chọn ngôn ngữ…) được lưu trữ ở phía server, thường trong bộ nhớ RAM hoặc cơ sở dữ liệu.
- Gửi Session ID đến client: Server trả về cho trình duyệt một cookie chứa Session ID sau khi phiên được tạo.

- Gửi lại Session ID trong các yêu cầu sau: Ở các yêu cầu tiếp theo, trình duyệt sẽ tự động gửi kèm cookie chứa Session ID này lên server. Nhờ vậy, server nhận biết được người dùng nào đang thực hiện yêu cầu, và có thể truy xuất dữ liệu tương ứng với phiên làm việc của họ.
- Kết thúc phiên: Phiên làm việc sẽ kết thúc khi người dùng đăng xuất hoặc khi timeout (hết thời gian) xảy ra. Khi đó, server sẽ xóa bỏ dữ liệu phiên đã lưu.
-  Thời gian timeout thường được cấu hình tùy theo nhu cầu – quá lâu có thể nguy hiểm, quá ngắn lại làm gián đoạn trải nghiệm.

Với mỗi session sẽ được cấp phát một định danh duy nhất SessionID. Khi kết thúc một phiên làm việc và bắt đầu một phiên mới, dĩ nhiên bạn sẽ được cấp một SessionID khác với trước đó. Bạn có thể tuỳ ý quyết định xem nên lưu trữ những thông tin nào vào Session. Nhưng thông thường chúng ta chỉ nên lưu những thông tin tạm thời trong session.

## 2.Ứng dụng của Session

Session thường được dùng cho các chức năng cần duy trì trạng thái người dùng xuyên suốt nhiều trang:

- Xác thực người dùng (đăng nhập): Server lưu trạng thái “đã đăng nhập” trong session để nhận biết người dùng khi chuyển trang

- Quản lý giỏ hàng: Dữ liệu các sản phẩm người dùng thêm vào giỏ hàng được lưu trong session để tồn tại giữa các trang và các lần truy cập.

- Tùy chọn cá nhân hóa: Session có thể lưu ngôn ngữ hiển thị, giao diện, hoặc các cài đặt cá nhân của người dùng để áp dụng cho các trang tiếp theo
.

- Dữ liệu tạm thời khác: Ví dụ thông tin nhập liệu giữa chừng (form chưa hoàn thành), điểm game, lịch sử duyệt phiên hiện tại,… cũng thường dùng session.

Các thông tin này được server ghi nhớ nhờ Session để tạo trải nghiệm liền mạch (không phải đăng nhập lại, không mất giỏ hàng…) cho người dùng

# 🍪 Cookie

Cookie là một đoạn dữ liệu nhỏ do trang web lưu trữ trên máy khách (trình duyệt) của người dùng ￼. Cookie thường dùng để ghi nhớ thông tin phiên làm việc và tuỳ chọn của người dùng, từ đó cá nhân hoá trải nghiệm web (ví dụ: lưu thông tin đăng nhập, ngôn ngữ, các giá trị đã chọn) ￼. Trình duyệt cho phép người dùng cấu hình việc chấp nhận, từ chối hoặc xoá cookie nếu cần. Cookie được gửi từ server thông qua header HTTP Set-Cookie hoặc được thiết lập bởi mã JavaScript trên trang (bằng document.cookie)

## 1.Cách hoạt động

- Server gửi cookie: Khi server muốn lưu thông tin trên trình duyệt, nó bao gồm header Set-Cookie trong HTTP response. Ví dụ: Set-Cookie: sessionId=abc123; Path=/; HttpOnly ￼. Mỗi cookie có thể kèm các thuộc tính như Expires/Max-Age (thời gian hết hạn), Path, Domain, Secure, HttpOnly, SameSite… để điều khiển phạm vi và bảo mật của cookie.

-	Client nhận và lưu cookie: Trình duyệt nhận header Set-Cookie và lưu thông tin cookie với các thuộc tính đi kèm (chỉ lưu nếu thuộc tính Domain/Path hợp lệ). Cookie được lưu trữ theo domain/path để xác định khi nào gửi trở lại.
-	Browser gửi cookie: Trong các yêu cầu HTTP tiếp theo cùng domain (và đúng path/secure điều kiện), trình duyệt tự động đính kèm header Cookie chứa tên và giá trị của các cookie đã lưu ￼ ￼. Ví dụ:

        GET /dashboard HTTP/1.1
        Host: example.com
        Cookie: sessionId=abc123; theme=light


Điều này cho phép server nhận diện phiên làm việc của người dùng qua cookie. Nếu cookie đã hết hạn hoặc bị xoá trên trình duyệt, trình duyệt sẽ không gửi lại cookie đó.

## 2.Các loại cookie phổ biến
- `Session cookie` (cookie phiên): Không có thời hạn (Expires/Max-Age), tự động bị xoá khi đóng trình duyệt ￼. `Session cookie` thường dùng để lưu thông tin phiên đăng nhập tạm thời và sẽ biến mất khi người dùng kết thúc phiên duyệt.
-	`Persistent cookie` (cookie lâu dài): Có ngày hết hạn cụ thể hoặc độ dài tồn tại (thiết lập Expires hoặc Max-Age) ￼. Cookie này được lưu trữ trên máy khách kể cả sau khi đóng trình duyệt và chỉ bị xoá khi hết hạn hoặc người dùng xoá nó. `Persistent cookie` thường dùng để ghi nhớ đăng nhập dài hạn hoặc tuỳ chọn người dùng; chúng cũng có thể được sử dụng cho mục đích theo dõi (tracking) hành vi người dùng qua nhiều phiên truy cập ￼.
- 	`Secure cookie`: Có thuộc tính Secure, nghĩa là cookie chỉ được gửi qua kết nối HTTPS (mã hoá) ￼ ￼. Thuộc tính này giúp ngăn kẻ tấn công đánh cắp cookie qua mạng khi giao tiếp không an toàn. Ví dụ, một `secure cookie` sẽ không được gửi khi trang được truy cập qua HTTP.
- 	`HttpOnly cookie`: Có thuộc tính HttpOnly, nghĩa là cookie không thể được truy cập bởi mã JavaScript trên trang ￼ ￼. Điều này ngăn ngừa việc cookie bị đánh cắp qua tấn công XSS (Cross-Site Scripting), vì đối với cookie HttpOnly, document.cookie trên trình duyệt sẽ không trả về giá trị cookie đó. (Cookie vẫn được gửi trong header Cookie bình thường khi gửi request).
- 	`SameSite cookie`: Có thuộc tính SameSite với giá trị Strict, Lax hoặc None, điều chỉnh cách cookie được gửi trong các yêu cầu cross-site (giữa các trang khác domain). Ví dụ: SameSite=Strict chỉ gửi cookie cho các yêu cầu từ cùng site (tắt toàn bộ yêu cầu đa site), trong khi SameSite=Lax cho phép gửi trong các navigation an toàn (GET) từ site khác. Thuộc tính này giúp giảm rủi ro CSRF ￼ ￼. Nếu dùng SameSite=None thì cookie được gửi trong cả cross-site, nhưng đa số trình duyệt yêu cầu kết hợp với Secure.

## 3.Ứng dụng thực tế của cookie
- 	Quản lý phiên (Session management): Cookie dùng để lưu session ID sau khi người dùng đăng nhập. Server dựa vào session ID trong cookie để nhận biết và duy trì trạng thái đăng nhập của người dùng giữa các lần request.
- 	Ghi nhớ tuỳ chọn người dùng: Cookie có thể lưu các thiết lập như `theme`, `ngôn ngữ`, `giỏ hàng`, `form tạm`, giúp người dùng không phải nhập lại mỗi lần truy cập trang.
-	Theo dõi và phân tích (Tracking): Các cookie persistent thường được các công cụ phân tích và quảng cáo sử dụng để thu thập thói quen duyệt web của người dùng qua nhiều phiên đăng nhập ￼. Ví dụ, cookie có thể ghi nhận thông tin trang đã xem, thời gian truy cập để phân tích lưu lượng hoặc hiển thị quảng cáo cá nhân hoá.

# Session và Cookie có gì khác biệt?

![alt text](/QuangAnh/HTTP/image/image-12.png)

Session và Cookie có nhiều điểm khác biệt quan trọng cần lưu ý. Dưới đây là một bảng so sánh chi tiết giữa Session và Cookie:

![alt text](/QuangAnh/HTTP/image/image-11.png)