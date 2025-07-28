# **Tìm hiểu về ngôn ngữ Markdown** 

# Mục lục
1. [Giới thiệu về ngôn ngữ Markdown](#1-giới-thiệu-về-ngôn-ngữ-markdown)
2. [Những định dạng phổ biến khi sử dụng Markdown](#2-những-định-dạng-phổ-biến-khi-sử-dụng-markdown)

    2.1) [Văn bản in đậm, in nghiêng](#21-văn-bản-in-đậm-in-nghiêng)

    2.2) [Tiêu đề](#22-tiêu-đề)    

    2.3) [Liên kết & email](#23-liên-kết--email)

    2.4) [Hình ảnh](#24-hình-ảnh) 

    2.5) [Bảng](#25-bảng) 

    2.6) [Gạch ngang chữ](#26-gạch-ngang-chữ) 

    2.7) [Dùng cho chèn Code](#27-dùng-cho-chèn-code) 

    2.8) [Danh sách](#28-danh-sách) 

    2.9) [Dùng cho Blockquote](#29-dùng-cho-blockquote) 

--------------------------


## 1. Giới thiệu về ngôn ngữ Markdown 

Ngôn ngữ này khá đơn giản, bạn có thể đọc tại [đây](https://daringfireball.net/projects/markdown/syntax) để biết cách sử dụng.

Markdown là một ngôn ngữ đánh dấu chuyển đổi văn bản thô thành mã HTML. Ngôn ngữ này cho phép người dùng sử dụng các ký tự đặc biệt như dấu hoa thị, dấu số, gạch dưới và dấu gạch ngang trong cú pháp markdown thay vì HTML. Cú pháp markdown này sau đó sẽ tự động chuyển đổi thành mã HTML.

## 2. Những định dạng phổ biến khi sử dụng Markdown

#### 2.1) Văn bản in đậm, in nghiêng
- In đậm

MARKDOWN 

    Ai hay **Ảo tưởng**    
    Thì bớt __Ảo Tưởng__ đi.

OUTPUT 

Ai hay **Ảo tưởng**    
Thì bớt __Ảo Tưởng__ đi.

- In nghiêng: Sử dụng _ ở đầu hoặc * (hoặc đầu và cuối câu) nếu muốn in nghiêng câu đó.

MARKDOWN

      _TopDev việc làm IT hàng đầu_
 
OUTPUT

_TopDev việc làm IT hàng đầu_

- In đậm và in nghiêng

MARKDOWN 

    *Chào buổi sáng, ***buổi trưa*** và* **buổi tối**


OUTPUT

*Chào buổi sáng, ***buổi trưa*** và* **buổi tối**

#### 2.2) Tiêu đề
 Có thể viết các lớp tiêu đề h1, h2, h3 cho đến h6 bằng cách thêm số lượng ký tự # tương ứng vào đầu dòng. Một ký tự # tương đương với h1, 2 ký tự # tương đương với h2 ...

Ví dụ:

MARKDOWN 

    # h1
    ## h2
    ### h3
    #### h4
    ##### h5
    ###### h6

OUTPUT

# h1
## h2
### h3
#### h4
##### h5
###### h6

#### 2.3) Liên kết & email

Cú pháp: Để nhanh chóng biến URL hoặc địa chỉ email thành một liên kết, đặt nó trong dấu ngoặc nhọn <>

Ví dụ: 

MARKDOWN 

    <https://google.com>  
    <info@meta.vn>

OUTPUT

<https://google.com>  
<info@meta.vn>


#### 2.4) Hình ảnh
Cú pháp: Để thêm hình ảnh trong markdown, thêm ký tự ! vào đầu tiên, sau đó ghi alt text trong ngoặc vuông [] và URL ảnh trong ngoặc đơn ()

Ví dụ:

MARKDOWN 

    ![hinh_1](/LinhNH/CCNA/01.Timhieu_Markdown/images/hinh_1.png)


OUTPUT 

![hinh_1](/LinhNH/CCNA/01.Timhieu_Markdown/images/hinh_1.png)


* Đính kèm liên kết vào hình ảnh: 

Cú pháp: Để thêm một liên kết vào hình ảnh trong Markdown, đặt toàn bộ khai báo hình ảnh như bước trên trong ngoặc vuông [] và thêm liên kết mình cần vào ngoặc đơn () đặt ngay tiếp sau.

Ví dụ: 

MARKDOWN

    [![hinh_1](/LinhNH/CCNA/01.Timhieu_Markdown/images/hinh_1.png)](https://facebook.com/)

OUTPUT

[![hinh_1](/LinhNH/CCNA/01.Timhieu_Markdown/images/hinh_1.png)](https://facebook.com/)

#### 2.5) Bảng

Cú pháp: Để tạo bảng, sử dụng 3 hoặc nhiều dấu gạch ngang --- và sử dụng pipes | để tách các cột. Để căn chỉnh text trong cột sang trái, phải hoặc giữa thì thêm dấu 2 chấm : vào trước, sau hoặc cả trước và sau.

Ví dụ: 

MARKDOWN 


    | Cột 1 Hàng 1 | Cột 2 | Cột 3| Cột 4 |
    |--------------|-------|------|-------|
    | Hàng 2 | 2 x 1 | 2 x 2 | 2 x 3 | 2 x 4 |
    | Hàng 3 | 3 x 1 | 3 x 2 | 3 x 3 | 3 x 4 |
    | Hàng 4 | 4 x 1 | 4 x 2 | 4 x 3 | 4 x 4 |

OUTPUT 
| Cột 1 Hàng 1 | Cột 2 | Cột 3| Cột 4 |
|--------------|-------|------|-------|
| Hàng 2 | 2 x 1 | 2 x 2 | 2 x 3 | 2 x 4 |
| Hàng 3 | 3 x 1 | 3 x 2 | 3 x 3 | 3 x 4 |
| Hàng 4 | 4 x 1 | 4 x 2 | 4 x 3 | 4 x 4 |

MARKDOWN

    |Họ và tên | Giới tính|Dân tộc|
    |:---|:----------------:|----:|
    |Sùng a bái | Nam|Mường|
    |Lò a hính|Nữ|Ê đê|

OUTPUT

|Họ và tên | Giới tính|Dân tộc|
|:---|:----------------:|----:|
|Sùng a bái | Nam|Mường|
|Lò a hính|Nữ|Ê đê|

#### 2.6) Gạch ngang chữ
Cú pháp: Sử dụng cặp dấu ~~ ở đầu (hoặc đầu và cuối câu) nếu muốn gạch ngang giữa chữ của câu đó.

Ví dụ:   
MARKDOWN 

    ~~Chúc bạn một ngày tốt lành~~ nhé.

OUTPUT

 ~~Chúc bạn một ngày tốt lành~~ nhé.

#### 2.7) Dùng cho chèn Code
- Code theo từ hoặc cụm từ: Sử dụng ` hoặc ``` ở đầu và cuối câu nếu muốn định dạng câu đó ở dạng code.

Ví dụ: 

MARKDOWN

    `TopDev việc làm IT hàng đầu`  

OUTPUT

`TopDev việc làm IT hàng đầu`  

-   Code theo đoạn/khối: Sử dụng 4 khoảng trắng ở đầu câu      nếu muốn định dạng cả đoạn đó ở dạng code.

Ví dụ: 
MARKDOWN 

    </style>
    <body>
        <div>TopDev tuyen dung IT hang dau.</div>
        <div class="relative">TopDev tuyen dung IT hang dau.</div>
        <div>TopDev tuyen dung IT hang dau.</div>
    </body>

OUTPUT

    </style>
    <body>
        <div>TopDev tuyen dung IT hang dau.</div>
        <div class="relative">TopDev tuyen dung IT hang dau.</div>
        <div>TopDev tuyen dung IT hang dau.</div>
    </body>

#### 2.8) Danh sách
Cú pháp: Sử dụng kí hiệu - hoặc * hoặc + nếu muốn định dạng câu đó ở dạng list. Trong trường hợp muốn tạo thêm lớp level thấp hơn thì lùi thụt thêm 2 khoảng trắng vào nữa.

Ví dụ: 

MARKDOWN

    - Thời khóa biểu
      - Thứ 2: Toán
        + Sáng: 7h
        - Chiều: 13H
      * Thứ 3: Lý    
      + Thứ 4: Hóa

OUTPUT

- Thời khóa biểu
  - Thứ 2: Toán
    + Sáng: 7h
    - Chiều: 13H
  * Thứ 3: Lý    
  + Thứ 4: Hóa

#### 2.9) Dùng cho Blockquote
 Cú pháp: Sử dụng > nếu muốn định dạng câu đó ở dạng quote.

Ví dụ: 

MARKDOWN 
 
    > TopDev việc làm IT hàng đầu 

OUTPUT

> TopDev việc làm IT hàng đầu





