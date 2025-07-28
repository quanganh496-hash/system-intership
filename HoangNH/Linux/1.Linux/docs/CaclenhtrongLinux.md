# Các lệnh trong Linux

## 1.ls

Lệnh ls là lệnh dùng để liệt kê các tập tin và thư mục trong Linux.

- Liệt kê các thư mục, tập tin hiện hành: `ls`

![image1](/HoangNH/Linux/1.Linux/image/ls1.png)

- Hiển thị chi tiết các tập tin và thư mục hiện hành: `ls -l`

![image2](/HoangNH/Linux/1.Linux/image/ls.png)

- Liệt kê thông tin trong thư mục: `ls -l /boot`

![image8](/HoangNH/Linux/1.Linux/image/ls7.png)

- Liệt kê các thư mục, tập tin mẹ: `ls ..`

![image3](/HoangNH/Linux/1.Linux/image/ls2.png)

- Liệt kê trong thư mục:

![image4](/HoangNH/Linux/1.Linux/image/ls3.png)

- Hiển thị tất cả các file và thư mục ẩn ở thư mục hiện hành: `ls -a`

![image5](/HoangNH/Linux/1.Linux/image/ls4.png)

- Liệt kê và sắp xếp theo thời gian: `ls -t`
- Hiển thị kích thước quy đổi ra Mb hoặc Gb: `ls -h`
- Liệt kê các tập tin theo thứ tự ngược: `ls -r`
- Danh sách đệ quy danh mục con: `ls -R`

![image6](/HoangNH/Linux/1.Linux/image/ls5.png)

- Các lệnh kết hợp:

![image7](/HoangNH/Linux/1.Linux/image/ls6.png)

![image9](/HoangNH/Linux/1.Linux/image/ls8.png)


## 2.cd

- Di chuyển từ thư mục hiện tại đến thư mục khác:

![image10](/HoangNH/Linux/1.Linux/image/cd1.png)

- Thay đổi thư mục hiện tại thành thư mục cha: `cd ..`

![image11](/HoangNH/Linux/1.Linux/image/cd2.png)

- Chuyển trở lại thư mục trước đó đã làm việc: `cd -`

![image12](/HoangNH/Linux/1.Linux/image/cd3.png)

- Di chuyển đến thư mục người dùng từ bất kỳ đâu: `cd` hoặc `cd ~`

![image13](/HoangNH/Linux/1.Linux/image/cd4.png)

## 3.pwd(present working directory)

Cú pháp: pwd [OPTION]

OPTION:

|Tùy chọn|Mô tả|
|:---|:---|
|-L(logical)|Sử dụng biến môi trường PWD, ngay cả khi nó chứa các liên kết tượng trưng|
|-P(physical)|Tránh sử dụng tất cả các liên kết tượng trưng|
|-help|Hiển thị trợ giúp|
|-version|In ra thông tin phiên bản|

- In thư mục làm việc hiện tại: `/bin/pwd`

![image14](/HoangNH/Linux/1.Linux/image/pwd1.png)

- Phiên bản in của pwd: `/bin/pwd --version`

![image15](/HoangNH/Linux/1.Linux/image/pwd2.png)

- In tất cả các vị trí chứa tệp thực thi có tên pwd: `type -a pwd`

![image16](/HoangNH/Linux/1.Linux/image/pwd3.png)

## 4.mkdir

- Tạo một thư mục: `mkdir <path_name>`

![image17](/HoangNH/Linux/1.Linux/image/mkdir1.png)

Có thể tạo nhiều thư mục cùng lúc: `mkdir <path_name_1> <path_name_2>`

![image18](/HoangNH/Linux/1.Linux/image/mkdir2.png)

- Tạo một thư mục khi thư mục cha chưa tồn tại: `mkdir -p <path_name>`

![image19](/HoangNH/Linux/1.Linux/image/mkdir3.png)

- Hiển thị quá trình tạo thư mục: `mkdir -v <path_name>`

![image20](/HoangNH/Linux/1.Linux/image/mkdir4.png)

- Tạo thư mục với phân quyền cụ thể

![image21](/HoangNH/Linux/1.Linux/image/mkdir5.png)

- Xem hướng dẫn sử dụng của lệnh MKDIR trong Linux: `man mkdir`

## 5.cp

- Sao chép tập tin vào một thư mục:

![image22](/HoangNH/Linux/1.Linux/image/cp1.png)

- Nhận cảnh báo khi ghi đè:

![image23](/HoangNH/Linux/1.Linux/image/cp2.png)

-  Sao chép thư mục:

![image24](/HoangNH/Linux/1.Linux/image/cp3.png)

## 6.rm

- Xóa 1 file:

![image25](/HoangNH/Linux/1.Linux/image/rm1.png)

- Xóa thư mục: 

Khi xóa thư mục trống:

![image26](/HoangNH/Linux/1.Linux/image/rm2.png)

Khi xóa thư mục không trống: 

![image27](/HoangNH/Linux/1.Linux/image/rm3.png)

- Nhận thông báo khi xóa:

![image28](/HoangNH/Linux/1.Linux/image/rm4.png)

## 7.rmdir

- Dùng để xóa thư mục trống:

Khi thư mục không trống sẽ có thông báo:

![image29](/HoangNH/Linux/1.Linux/image/rmdir1.png)

Khi thư mục trống:

![image30](/HoangNH/Linux/1.Linux/image/rmdir2.png)

- Xóa thư mục con, nếu thư mục cha rỗng cũng bị xóa:

![image31](/HoangNH/Linux/1.Linux/image/rmdir3.png)

## 8.mv

- Cú pháp: mv [OPTIONS] SOURCE DESTINATION
- Các options:
   - -i: hỏi xác nhận trước khi ghi đè
   - -v: ghi lại bản ghi của hoạt động
   - -b: tạo một bản backup trước khi ghi đè

![image32](/HoangNH/Linux/1.Linux/image/mv1.png)

## 9.man

Lệnh man, viết tắt của manual, phục vụ một hệ thống tài liệu tích hợp cung cấp thông tin về các lệnh, chức năng, và tệp cấu hình Linux khác.

-  `man ls`:

![image33](/HoangNH/Linux/1.Linux/image/man1.png)

- Khi muốn thoát khỏi lệnh man, ấn q.

## 10.touch

- Cú pháp: touch [options] [filename]
- option -a: tạo tệp mới và gán thời gian
- -m: thay đổi thời gian sửa đổi

![image34](/HoangNH/Linux/1.Linux/image/touch1.png)

- -c: Đổi Access Time mà không phải tạo file mới
- -t: đặt thời gian truy cập và chỉnh sửa đến một ngày giờ nhất định

`touch -t YYMMDDhhmm.ss [filename]`

![image35](/HoangNH/Linux/1.Linux/image/touch2.png)

- -d: đặt ngày giờ bằng chuỗi

![image36](/HoangNH/Linux/1.Linux/image/touch3.png)

## 11.cat

- Cú pháp: cat [options] [filename]
-  `cat > [filename]`: tạo file mới và điền nội dung vào file. Ấn Ctrl+D để thoát file.
- `cat [filename]`: xem nội dung file

![image37](/HoangNH/Linux/1.Linux/image/cat1.png)

- `cat [file1] > [file2]`: chuyển hướng nội dung file. Nếu file đích không có sẵn, lệnh này sẽ tự tạo file đó ra. Hoặc ghi đè lên file có cùng tên.

![image38](/HoangNH/Linux/1.Linux/image/cat2.png)

- `cat -n [filename]`: hiện thị số dòng

![image39](/HoangNH/Linux/1.Linux/image/cat3.png)

- -v: hiển thị tất cả những ký tự không in được
- -T: hiển thị ký tự dấu tab
- -s: cắt bớt dòng trống
- -b: hiển thị những dòng không trống với số dòng trước nó

## 12.head

- In ra 10 dòng đầu của file:

![image40](/HoangNH/Linux/1.Linux/image/head1.png)

- In ra n dòng đầu: -n <số dòng>

![image40](/HoangNH/Linux/1.Linux/image/head2.png)

- Loại trừ n dòng cuối: -n -<số dòng>

![image41](/HoangNH/Linux/1.Linux/image/head3.png)

- In n ký tự đầu tiên của file: -c <số ký tự>

![image42](/HoangNH/Linux/1.Linux/image/head4.png)

- Thực hiện với nhiều file:

![image43](/HoangNH/Linux/1.Linux/image/head5.png)

- Lọc dữ liệu với grep:

![image44](/HoangNH/Linux/1.Linux/image/head6.png)

- Hiển thị các file sử dụng gần đây nhất:

![image45](/HoangNH/Linux/1.Linux/image/head7.png)

## 13.tail

- In ra 10 dòng cuối:

![image46](/HoangNH/Linux/1.Linux/image/tail1.png)

- In ra n dòng cuối: -n <số dòng>

![image47](/HoangNH/Linux/1.Linux/image/tail2.png)

- In từ dòng n: -n +<số dòng>

![image48](/HoangNH/Linux/1.Linux/image/tail3.png)

- In n ký tự cuối của file: -c <số ký tự>

![image49](/HoangNH/Linux/1.Linux/image/tail4.png)

## 14.grep

- Tìm kiếm chuỗi trong 1 file:

![image50](/HoangNH/Linux/1.Linux/image/grep1.png)

- Tìm kiếm trong nhiều file:

![image51](/HoangNH/Linux/1.Linux/image/grep2.png)

- Tìm kiếm chuỗi sử dụng biểu thức chính quy:

  - `^`: tìm kiếm chuỗi bắt đầu bằng 1 ký tự nào đó

![image52](/HoangNH/Linux/1.Linux/image/grep3.png)

  - `$`: tìm kiếm chuỗi kết thúc bằng 1 ký tự nào đó

![image53](/HoangNH/Linux/1.Linux/image/grep4.png)

  -`[]`: chỉ định ký tự bất kỳ trong ngoặc

![image54](/HoangNH/Linux/1.Linux/image/grep5.png)

  - `.`: đại diện cho bất kỳ ký tự nào

![image55](/HoangNH/Linux/1.Linux/image/grep6.png)

- Tìm kiếm trong tất cả các file và thư mục: `grep -r "chuỗi" [directory]
- Hiển thị dòng trước/sau của chuỗi tìm kiếm: -A là dòng trước, -B là dòng sau

![image56](/HoangNH/Linux/1.Linux/image/grep7.png)

- Tìm kiếm chuỗi không có từ khóa cụ thể

![image57](/HoangNH/Linux/1.Linux/image/grep8.png)

- Đếm số lần xuất hiện của chuỗi:  `grep -c "chuỗi" [filename]`
- Hiển thị số thứ tự dòng chứa chuỗi kết quả: `grep -n "chuỗi" [filename]`

## 15.find

- Cú pháp: `find [path] [options] [expression]`
- Tìm file theo tên ở thư mục hiện tại: `find . -name [filename]`
- Tìm file trong thư mục cụ thể: `find [directory] -name [filename]`

![image58](/HoangNH/Linux/1.Linux/image/find1.png)

- Tìm kiếm theo loại tệp: -type

Các options:
- f: file thông thường
- d: directories
- l: liên kết tượng trưng
- c: character devices
- b: block devices
- p: names pipe
- s: sockets

![image59](/HoangNH/Linux/1.Linux/image/find2.png)

- Tìm kiếm theo kích thước: -size

![image60](/HoangNH/Linux/1.Linux/image/find3.png)

- Tìm kiếm theo quyền cụ thể: -perm

![image61](/HoangNH/Linux/1.Linux/image/find4.png)

## 16.echo

- Nhập một dòng văn bản và hiển thị nó trên đầu ra tiêu chuẩn

![image62](/HoangNH/Linux/1.Linux/image/echo1.png)

- Khai báo một biến và hiển thị giá trị của nó

![image63](/HoangNH/Linux/1.Linux/image/echo2.png)

- In tất cả các tệp/thư mục:



## 17.locate

- Tìm kiếm các file, thư mục:

## 18.cut

- Cú pháp: cut <options> <file>
- Các options:
  - -b: Cắt theo vị trí byte
  - -C: Cắt theo vị trí ký tự
  - -d: Trích xuất chuỗi bằng cách dùng dấu phân cách được chỉ định với tùy chọn trường
  - -f: Trích xuất theo một trường cụ thể
  - -S: Trích xuất chỉ cho dấu phân cách

- Trích xuất các ký tự từ chuỗi: `cut -b 1,3,5,7,9 filename.txt`

- Cắt trong phạm vi: `cut -b 1-10,11-20 number.txt`

- Trích xuất văn bản từ vị trí bắt đầu, kết thúc:

## 19.tr(translate)

- Cú pháp: `tr [options] <SET1> <SET2>` 

SET là các chuỗi ký tự và một số trình tự được diễn giải mà terminal tự động nhận dạng:\\, \b, \t, \v, [:alnum:], [:alpha:], [:blank:], [:digit:], [:lower:], [:punct:], [:space:], [:upper:] 

- Đổi chữ thường thành chữ hoa:

`cat alphabet.txt | tr [:lower:] [:upper:]`
hoặc `cat alphabet.txt | tr [a-z] [A-Z]`

- Xóa ký tự: `cat number.txt | tr -d "e"`

- Chuyển khoảng trắng thành tab: 

- Xóa dấu câu, xóa các chữ số: 

## 20.wc

- Sử dụng wc với file, lệnh sẽ trả về số dòng,từ và byte trong file (-l, -w, -c):

- Hiển thị độ dài của dòng dài nhất (- L):

## 21.strings

- Hiển thị các chuỗi ký tự trong tệp:
Các options:

  - -e: Hiển thị các ký tự không in được dưới dạng mã hex
  - -n <n>: Chỉ hiển thị các chuỗi có ít nhất n ký tự
  - -o <n>: Bỏ qua n ký tự đầu tiên của mỗi chuỗi
  - -t: Hiển thị các ký tự tab dưới dạng \T
  - -v: Hiển thị số lượng dòng của mỗi chuỗi

## 22.alias

Lệnh Alias cho phép chỉ định các từ khóa ngắn cho các chuỗi dài gồm các lệnh dùng thường xuyên.

- Cú pháp: `alias shortName="your custom command here"`

- Xóa alias dùng lệnh unalias

## 23.sort 

- Mặc định:

- Tạo tệp đầu ra mới: -o để chỉ định tên file đã sắp xếp, tạo 1 file mới và thêm nội dung:

- Sắp xếp ngược: -r 

- Sắp xếp theo số: -n 

- Sắp xếp bỏ qua viết hoa, viết thường: -f 

- Sắp xếp bỏ qua hàng trống: -b 

- Sắp xếp theo cột: - k(số cột)

## 24.date

- Lấy ngày giờ hiện tại: date

- Lấy một ngày trong quá khứ/ tương lai: date -d "< ... >"

- Nhận ngày trong tuần: 

- Nhận giờ phối hợp quốc tế: date -u 

- Nhận thời gian sửa đổi cuối cùng của tệp: date -R 

## 25.sed (stream editor)

- Thay thế từ đầu tiên mỗi dòng: `sed 's/từ cũ/từ mới/' <filename>`

- Thay thế từ thứ n: `sed 's/từ cũ/từ mới/n' <filename>`

- Thay thế tất cả: `sed 's/từ cũ/từ mới/g' <filename>`

- Thay thế trên dòng m nhất định: `sed 'm s/từ cũ/từ mới/' <filename>`

- Nhân bản dòng được thay thế: `sed 's/từ cũ/từ mới/p' <filename>`

- Chỉ hiện thị các dòng được thay thế: `sed -n 's/từ cũ/từ mới/p' <filename>`

- Thay thế trên khoảng dòng từ x đến y `sed 'x,y s/từ cũ/từ mới/' <filename>`

- Xóa dòng thứ n trong file: `sed 'nd' <filename>`

- Xóa dòng cuối cùng trong file : `sed '$d' <filename>`

- Xóa các dòng từ x đến y: `sed 'x,yd' <filename>`

- Xóa dòng thứ n đến cuối file: `sed 'nth,$d' <filename>`

- Xóa dòng khớp mẫu: `sed '/pattern/d' <filename>`

## 26.time 

Lệnh time dùng để xác định thời gian thực hiện một hoạt động cụ thể.
Khi thực hiện lệnh time có 3 kết quả:

- real: liên quan đến thời gian trôi qua giữa khi thực thi và hoàn thành command
- user: là thời gian người dùng dành cho bộ xử lý
- sys: thời gian hệ thống (kernel) sử dụng để chạy command


## 27.cal

- Xem lịch tháng hiện tại: cal

- Xem lịch n tháng gần nhất: cal -n

- Xem lịch cả năm: cal -y 

- Xem lịch một tháng trong năm cụ thể: cal month year


## 28.uniq

- Bỏ qua những dòng trùng lặp: `uniq <filename>`

- Cho biết số dòng lệnh lặp lại: `uniq -c <filename>`

- Chỉ in những dòng lặp lại: `uniq -d <filename>`

- Chỉ in các dòng duy nhất: `uniq -u <filename>`

- Bỏ qua các trường trong khi kiểm tra trùng lặp: `uniq -f N <filename>`

- Bỏ qua các ký tự khi so sánh: `uniq -s N <filename>`

- Kiểm tra các ký tự xem có trùng lặp không: `uniq -w N <filename>`


## 29.gzip

- Nén một file và xóa file gốc: `gzip file`

- Nén một file và không xóa file gốc: `gzip -k file` hoặc `gzip -c file > file.gz`

- Nén file trong thư mục: `gzip -r folder`

- Thay đổi mức nén: `gzip -[1..9] file. 1 là tốc độ nén nhanh nhất và tỉ lệ nén dung lượng tối thiểu nhất. 9 là tốc độ nén chậm nhất và tỉ lệ nén dung lượng tốt nhất.

- Giải nén: `gzip -d file.gz`

- Xem nội dung file nén: `gzip -l file`

## 30.gunzip

- Giải nén : `gunzip file.gz`

- Xem nội dung file mà cần giải nén: `gunzip -c file.gz`

- Giải nén một cách mạnh mẽ: `gunzip -f file.gz`

- Giải nén đệ quy các tệp: `gunzip -r file.gz`

## 31.who

Lệnh who dùng để in ra danh sách những người dùng hiện đang đăng nhập.

- `who`. Nó sẽ liệt kê danh sách tất cả những người dùng đang đăng nhập trên hệ thống. Mỗi người dùng sẽ gồm những thông tin như sau:
  - Tên đăng nhập.
  - Terminal của user.
  - Thời điểm đăng nhập.
  - Địa chỉ IP máy chủ hoặc tên máy chủ.

- `who -H`: n ra phần heading cho mỗi thông tin

- `who -b`: xem ai là người đã rời khỏi hệ thống gần đây nhất.

- `who -d`: Để xem danh sách tất cả các quy trình đã bị chết

- `who -r`: để xem cấp độ của người dùng hiện tại.

- `who -q`: Để lấy danh sách tên người dùng đang đăng nhập và tổng số lượng người dùng đó

- `who -a`: để xem thông tin đầy đủ của các user.


## 32.type

Lệnh type được sử dụng để hiển thị thông tin về loại lệnh. 

- Tùy chọn -t này cho biết mô tả loại lệnh.Mô tả các loại lệnh như sau:

  - alias (shell alias)
  - function (shell function)
  - builtin (shell builtin)
  - file (disk file)
  - keyword (shell reserved word)

- Hiển thị tất cả các vị trí có chứa lệnh: -a 







