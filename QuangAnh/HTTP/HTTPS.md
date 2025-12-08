# 1. Khái niệm HTTPS

![alt text](image-17.png)

- HTTPS là một phần mở rộng của HTTP

- HTTPS là viết tắt của Hypertext Transfer Protocol Secure, tức là giao thức truyền tải siêu văn bản có bảo mật.Về mặt chức năng, nó hoạt động tương tự HTTP nhưng trong HTTPS, giao thức truyền thông được mã hóa bằng Transport Layer Security (TLS) hay trước đây là Secure Sockets Layer (SSL). Do đó, giao thức này còn được gọi là HTTP qua TLS, hoặc HTTP qua SSL. 
- Khi một website sử dụng HTTPS, toàn bộ dữ liệu truyền tải giữa người dùng và máy chủ đều được mã hóa. Điều đó có nghĩa là ngay cả khi dữ liệu bị chặn lại giữa chừng, kẻ tấn công cũng không thể hiểu được nội dung bên trong.

# 2.Tầm quan trọng đặc biệt của HTTPS

Việc hiểu rõ HTTPS là gì mới chỉ là bước đầu tiên. Điều quan trọng hơn là bạn phải nắm được vai trò thiết yếu của HTTPS trong thời đại số. Trước đây, HTTPS chủ yếu được áp dụng cho các trang web thương mại điện tử, ngân hàng hoặc cổng thanh toán trực tuyến. Khi mà tính bảo mật dữ liệu tài chính là ưu tiên hàng đầu. Tuy nhiên, ngày nay, việc sử dụng HTTPS đã trở thành tiêu chuẩn bắt buộc cho mọi loại website, kể cả những blog cá nhân, trang tin tức hay diễn đàn.
Một trong những lợi ích lớn nhất khi chuyển từ HTTP sang HTTPS là đảm bảo an toàn cho người dùng. Khi sử dụng HTTPS, các thông tin như mật khẩu, số điện thoại, email hay thậm chí là hành vi duyệt web đều được mã hóa nhằm bảo vệ quyền riêng tư và ngăn chặn đánh cắp dữ liệu. Ngoài ra, trình duyệt như Google Chrome hoặc Firefox hiện đã gắn nhãn "Không an toàn" cho các website không sử dụng HTTPS, gây mất uy tín trong mắt người dùng.

![alt text](image-18.png)

Không dừng lại ở đó, HTTPS còn ảnh hưởng trực tiếp đến thứ hạng tìm kiếm của website trên Google. Từ năm 2014, Google đã chính thức công bố rằng HTTPS là một yếu tố xếp hạng trong thuật toán tìm kiếm. Do đó, nếu bạn muốn tối ưu SEO cho website, việc chuyển đổi sang HTTPS là điều cực kỳ cần thiết.


# 3. Cách hoạt động của HTTPS

![alt text](image-19.png)



Bắt tay TLS là một loạt các datagram, hoặc tin nhắn, được trao đổi bởi một máy khách và một máy chủ. Một cái bắt tay TLS bao gồm nhiều bước, vì máy khách và máy chủ trao đổi thông tin cần thiết để hoàn thành cái bắt tay và thực hiện cuộc trò chuyện tiếp theo.

Các bước chính xác trong một cái bắt tay TLS sẽ khác nhau tùy thuộc vào loại thuật toán trao đổi khóa được sử dụng và các bộ mật mã được cả hai bên hỗ trợ. Thuật toán trao đổi khóa RSA, mặc dù hiện được coi là không an toàn, đã được sử dụng trong các phiên bản TLS trước 1.3. Nó đại khái như sau:

1. Tin nhắn 'xin chào khách hàng': Khách hàng bắt đầu bắt tay bằng cách gửi tin nhắn "xin chào" đến máy chủ. Tin nhắn sẽ bao gồm phiên bản TLS mà khách hàng hỗ trợ, các bộ mật mã được hỗ trợ và một chuỗi các byte ngẫu nhiên được gọi là "khách hàng ngẫu nhiên".

2. Tin nhắn 'xin chào máy chủ': Để trả lời tin nhắn xin chào của khách hàng, máy chủ sẽ gửi một tin nhắn chứa chứng chỉ SSL của máy chủ, bộ mật mã đã chọn của máy chủ và "máy chủ ngẫu nhiên", một chuỗi byte ngẫu nhiên khác do máy chủ tạo ra.

3. Xác thực: Máy khách xác minh chứng chỉ SSL của máy chủ với cơ quan cấp chứng chỉ đã cấp chứng chỉ. Điều này xác nhận rằng máy chủ là người mà nó nói và khách hàng đang tương tác với chủ sở hữu thực tế của miền.

4. Bí mật premaster: Máy khách gửi thêm một chuỗi byte ngẫu nhiên, "bí mật premaster". Bí mật premaster được mã hóa bằng khóa công khai và chỉ có thể được giải mã bằng khóa riêng bởi máy chủ. (Khách hàng nhận được khóa công khai từ chứng chỉ SSL của máy chủ.)

5. Khóa riêng được sử dụng: Máy chủ giải mã bí mật premaster.

6. Các khóa phiên được tạo: Cả máy khách và máy chủ đều tạo các khóa phiên từ máy khách ngẫu nhiên, máy chủ ngẫu nhiên và bí mật premaster. Họ sẽ đi đến cùng một kết quả.

7. Máy khách đã sẵn sàng: Máy khách gửi một tin nhắn "đã hoàn thành" được mã hóa bằng khóa phiên.

8. Máy chủ đã sẵn sàng: Máy chủ gửi một tin nhắn "đã hoàn thành" được mã hóa bằng khóa phiên.

9. Mã hóa đối xứng an toàn đạt được: Việc bắt tay được hoàn thành và giao tiếp tiếp tục bằng cách sử dụng các khóa phiên.

Tất cả các bắt tay TLS đều sử dụng mật mã không đối xứng (khóa công khai và khóa riêng), nhưng không phải tất cả sẽ sử dụng khóa riêng trong quá trình tạo khóa phiên. Ví dụ, một cái bắt tay Diffie-Hellman phù du diễn ra như sau:

1. Khách hàng xin chào: Khách hàng gửi tin nhắn xin chào khách hàng với phiên bản giao thức, khách hàng ngẫu nhiên và danh sách các bộ mật mã.

2. Máy chủ xin chào: Máy chủ trả lời bằng chứng chỉ SSL, bộ mật mã đã chọn và máy chủ ngẫu nhiên. Trái ngược với cái bắt tay RSA được mô tả ở trên, trong tin nhắn này, máy chủ cũng bao gồm những điều sau (bước 3):

3. Chữ ký số của máy chủ: Máy chủ tính toán chữ ký số của tất cả các tin nhắn cho đến thời điểm này.

4. Chữ ký số đã được xác nhận: Máy khách xác minh chữ ký số của máy chủ, xác nhận rằng máy chủ là người mà nó nói.

5. Tham số DH của máy khách: Máy khách gửi tham số DH của nó đến máy chủ.

6. Máy khách và máy chủ tính toán bí mật premaster: Thay vì máy khách tạo bí mật premaster và gửi nó đến máy chủ, như trong một cái bắt tay RSA, máy khách và máy chủ sử dụng các tham số DH mà họ đã trao đổi để tính toán riêng bí mật premaster phù hợp.

7. Các khóa phiên được tạo: Bây giờ, máy khách và máy chủ tính toán các khóa phiên từ bí mật premaster, khách hàng ngẫu nhiên và máy chủ ngẫu nhiên, giống như trong một cái bắt tay RSA.

8. Khách hàng đã sẵn sàng: Tương tự như một cái bắt tay RSA.

9. Máy chủ đã sẵn sàng

10. Mã hóa đối xứng an toàn đạt được

