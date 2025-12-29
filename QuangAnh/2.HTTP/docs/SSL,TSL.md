# SSL/TLS cer, CSR, Pub/Private Key, CA

SSL (Secure Sockets Layer) và TLS (Transport Layer Security) là hai giao thức mã hóa được sử dụng để bảo vệ thông tin truyền qua Internet. SSL được Netscape giới thiệu năm 1995 với mục tiêu đảm bảo tính riêng tư, xác thực và toàn vẹn của dữ liệu khi truyền tải. TLS ra đời năm 1999 như một phiên bản nâng cấp của SSL, kế thừa ưu điểm và khắc phục lỗ hổng của SSL 3.0. Về cơ bản, TLS là phiên bản mới, an toàn hơn; ngày nay TLS đã thay thế hoàn toàn SSL và trở thành chuẩn bảo mật cho website.
- SSL (Secure Sockets Layer): giao thức bảo mật ban đầu do Netscape phát triển (1995) để mã hóa kết nối giữa trình duyệt và máy chủ. SSL có các phiên bản 2.0 và 3.0, nhưng hiện đã lỗi thời
- TLS (Transport Layer Security): giao thức kế thừa và cải tiến từ SSL, xuất hiện năm 1999 dưới sự chuẩn hoá của IETF. TLS có các phiên bản 1.0 đến 1.3 và được khuyến cáo sử dụng vì an toàn hơn SSL cũ

Dù thường nói chung là “SSL/TLS”, kỹ thuật hiện đại thực tế chủ yếu dùng TLS. TLS cải tiến các thuật toán mã hóa và thủ tục bắt tay để nhanh hơn và bảo mật hơn so với SSL cổ điển

# Cách hoạt động cơ bản của SSL/TLS

Khi bạn truy cập trang web có bảo mật (HTTPS), trình duyệt và máy chủ sẽ thực hiện một quá trình bắt tay (handshake) để thiết lập kết nối an toàn
. Trong quá trình này, máy chủ gửi chứng chỉ SSL/TLS (giống như hộ chiếu điện tử) cho trình duyệt. Chứng chỉ này do tổ chức chứng thực đáng tin cậy (CA) cấp, chứa thông tin danh tính trang web và khóa công khai của nó. Trình duyệt kiểm tra tính hợp lệ của chứng chỉ; nếu hợp lệ, hai bên sẽ trao đổi khóa mã hóa và tạo ra một khóa phiên (session key) riêng cho lần giao dịch đó. Sau khi kết nối thiết lập xong, mọi dữ liệu gửi qua lại sẽ được mã hóa bằng khóa phiên này. Nhờ vậy, tin nhắn được chuyển thành chuỗi ký tự ngẫu nhiên mà kẻ ngoài cuộc không thể đọc được.

# Certificate Authority (CA) là gì?
**Certificate Authority (CA)** là một tổ chức đáng tin cậy chuyên cấp phát, xác minh và quản lý các chứng chỉ số (digital certificate). Các chứng chỉ số này chứa thông tin về tên chủ sở hữu, khóa công khai, chữ ký số của CA, thời hạn hiệu lực… để chứng thực danh tính của website hoặc tổ chức. Khi một trang web sử dụng chứng chỉ số do CA phát hành, trình duyệt sẽ “tin tưởng” trang đó và hiển thị biểu tượng ổ khóa bảo mật. Nói cách khác, nếu Internet là một “thế giới số”, thì CA giống như cơ quan cấp giấy tờ tùy thân trong đó: nó đảm bảo danh tính của các đối tượng giao tiếp và ký xác nhận để người khác tin tưởng.
## Tại sao cần CA?
Khi hai bên trên Internet chưa từng gặp nhau, làm sao trình duyệt có thể biết trang web là thật chứ không phải giả mạo? CA chính là bên thứ ba đáng tin cậy giải quyết vấn đề này. Cụ thể, vai trò chính của CA bao gồm:
- Xác thực danh tính website: đảm bảo bạn đang truy cập đúng trang web, không phải trang giả mạo. Khi chứng chỉ số hợp lệ do một CA đã xác minh cấp, trình duyệt yên tâm rằng trang web là thật.
- Ngăn chặn tấn công trung gian (MITM): kẻ tấn công không thể giả mạo trang web nếu không có khóa riêng của CA để ký chứng chỉ. Điều này giúp chặn các cuộc tấn công nghe lén hay giả mạo.
- Tạo nền tảng cho mã hóa: CA cấp chứng chỉ chứa khóa công khai, làm cơ sở để thiết lập kênh mã hóa (bảo mật dữ liệu) giữa trình duyệt và máy chủ
. Nhờ vậy, thông tin cá nhân (mật khẩu, số thẻ…) được mã hóa khi truyền đi.
- Xác minh website là thật: CA giúp trình duyệt nhận biết trang web không phải là trang lừa đảo/phishing
. Nếu trang web giả mạo cố tình dùng chứng chỉ tự ký thì không có CA tin cậy ký, trình duyệt sẽ cảnh báo.

Tóm lại, CA tạo niềm tin cho kết nối an toàn: nếu không có CA, trình duyệt không thể biết tự động trang web có đáng tin cậy hay không, đồng nghĩa không thể an tâm duyệt web an toàn.
## CA hoạt động như thế nào: xác minh danh tính và cấp chứng chỉ số
Các bước cấp chứng chỉ số qua CA diễn ra tự động nhưng rất chặt chẽ:

Đầu tiên, chủ website tạo yêu cầu cấp chứng chỉ (CSR) bao gồm khóa công khai và thông tin cần xác minh (tên miền, tổ chức…). CA tiếp nhận CSR này và kiểm tra danh tính của chủ thể qua email, tài liệu pháp lý hoặc xác minh chủ sở hữu tên miền
. Nếu thông tin hợp lệ, CA sẽ ký chứng chỉ bằng khóa riêng của mình và cấp lại chứng chỉ số cho chủ website
. Chứng chỉ này chứa khóa công khai đã được xác thực và chữ ký số của CA. Cuối cùng, khi người dùng truy cập website qua HTTPS, trình duyệt sẽ nhận chứng chỉ đó, kiểm tra chữ ký số của CA (so sánh với danh sách CA đáng tin cậy) và nếu hợp lệ thì thiết lập kết nối mã hóa. Nếu thành công, ổ khóa bảo mật sẽ hiện lên trên trình duyệt
. Quá trình này thường diễn ra trong vài giây nhưng tạo nền tảng cho mọi kết nối web an toàn ngày nay.
## Vai trò của CA trong trình duyệt và giao thức HTTPS
Trong thực tế, các trình duyệt và hệ điều hành như Chrome, Firefox, Windows, macOS… đã tích hợp sẵn danh sách CA gốc tin cậy (trust store)
. Khi trình duyệt kết nối đến một trang HTTPS, máy chủ sẽ gửi chứng chỉ số (chứa khóa công khai) cho trình duyệt. Trình duyệt dựa vào danh sách CA để kiểm tra chữ ký số trong chứng chỉ này
. Nếu chữ ký trùng khớp và CA cấp chứng chỉ đó nằm trong danh sách tin cậy, trình duyệt mới tin tưởng trang web và hiện biểu tượng ổ khóa màu xanh
. Nhờ CA, người dùng không cần biết khóa riêng của máy chủ, mà vẫn an tâm rằng kết nối đang được mã hóa và đúng với trang web mong đợi. Tóm lại, CA là “người giám sát” cuối cùng cho phép trình duyệt tự động xác thực danh tính trang web trong giao thức HTTPS.

## Một số CA nổi tiếng trên thế giới
Hiện có nhiều CA lớn và uy tín. Ví dụ, DigiCert, Let’s Encrypt, Comodo (nay đổi tên thành Sectigo) là những CA nổi tiếng toàn cầu
. Ngoài ra, các tổ chức như Sectigo (Comodo), GlobalSign, GoDaddy, Entrust, IdenTrust… cũng đứng đầu thị trường CA thế giới
. Mỗi CA này đều tuân thủ các tiêu chuẩn bảo mật nghiêm ngặt để xây dựng niềm tin. Khi chọn mua/chọn dùng chứng chỉ, người dùng thường lựa CA tên tuổi nhằm đảm bảo kết nối an toàn và được hỗ trợ lâu dài.

# CSR (Certificate Signing Request) - Yêu cầu cấp chứng chỉ

**CSR (Certificate Signing Request)** là một thông điệp yêu cầu cấp chứng chỉ số mà bạn gửi đến Tổ chức cấp chứng chỉ (CA – Certificate Authority) để xin cấp một chứng chỉ SSL/TLS cho trang web hoặc dịch vụ của mình. CSR bao gồm các thông tin nhận dạng của bạn và khóa công khai (public key) bạn vừa tạo ra từ khóa riêng (private key)
. Cụ thể, trong CSR có thể chứa tên miền cần bảo mật, tên tổ chức, địa chỉ, email liên lạc và khóa công khai sẽ được gắn vào chứng chỉ số
. Sau khi nhận được CSR, CA sẽ kiểm tra thông tin và tạo chứng chỉ số tương ứng (ký bởi khóa riêng của CA) để gửi lại cho bạn.
Tại sao cần CSR trong quy trình xin chứng chỉ số SSL/TLS
Để có chứng chỉ SSL/TLS cho trang web, bạn cần chứng minh quyền sở hữu tên miền và cung cấp khóa công khai cho CA. CSR chính là cơ chế thực hiện việc này. Theo SecureW2, CSR là thông điệp chứa khóa công khai và thông tin miền được gửi tới CA để lấy chứng chỉ số
. Nói cách khác, để nhận được chứng chỉ số, bạn phải tạo và nộp CSR, trong đó đã bao gồm khóa công khai và các thông tin định danh cơ bản
. CSR giúp CA xác minh rằng bạn có khóa riêng tương ứng (bằng chứng tự ký CSR) và đồng thời cung cấp danh tính hợp lệ của bạn (ví dụ tên miền, tên tổ chức, email)
.
## CSR chứa những thông tin gì
CSR bao gồm các thông tin sau mà CA cần để cấp chứng chỉ số:
- Tên miền (Common Name): Tên miền hoặc địa chỉ website cần bảo mật.
- Thông tin tổ chức: Tên công ty, địa chỉ, thành phố, tỉnh/thành và mã bưu chính của tổ chức.
- Thông tin liên lạc: Địa chỉ email liên lạc hoặc các thông tin liên hệ của tổ chức hoặc quản trị hệ thống.
- Khóa công khai (Public Key): Khóa mã hóa công khai vừa được tạo, gắn với khóa riêng của bạn. CSR cũng có thể ghi rõ loại khóa (ví dụ RSA) và độ dài khóa (ví dụ 2048 bit).

Các thông tin này được CA dùng để xác minh danh tính của bạn và tạo chứng chỉ phù hợp.
