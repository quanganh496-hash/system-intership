# Tìm hiểu cách viết tài liệu với Markdown

## 1. Giới thiệu về Markdown
Markdown là một ngôn ngữ đánh dấu với cú pháp văn bản thô, được thiết kế để có thể dễ dàng chuyển thành HTML và nhiều định dạng khác sử dụng một công cụ cùng tên. Nó thường được dùng để tạo các tập tin readme, viết tin nhắn trên các diễn đàn, và tạo văn bản có định dạng bằng một trình biên tập văn bản thô.

## 2. Cách sử dụng Markdown
### 2.1 Dùng cho Heading

Sử dụng `#` trước tiêu đề để đánh dấu Heading, số kí tự `#` sẽ tương ứng với các cấp Heading khác nhau.

Ví dụ: 
    `# h1`
    `## h2`
    `### h3`

Kết quả:
# h1
## h2
### h3

### 2.2 Dùng cho Bold và Italic

- **Bold**: Sử dụng `**` ở đầu (hoặc đầu và cuối câu) nếu muốn bôi đậm câu đó.

Ví dụ: `**Markdown**`

Kết quả: **Markdown**
- _Italic_: Sử dụng `_` ở đầu hoặc `*` (hoặc đầu và cuối câu) nếu muốn in nghiêng câu đó.

Ví dụ: `*Markdown*`

Kết quả: *Markdown*

### 2.3 Dùng cho chèn link

Sử dụng cú pháp `[]()` để chèn link trong bài viết, ở đó nội dung trong `[]` sẽ là thẻ alt text, và nội dung trong `()` sẽ là đường link mà bạn muốn điều hướng đến.

Ví dụ: `[Github](https://github.com/)`

Kết quả: [Github](https://github.com/)

### 2.4 Dùng cho chèn Image

Sử dụng cú pháp `![]()` để chèn link trong bài viết, ở đó nội dung trong `[]` sẽ là thẻ alt text, và nội dung trong `()` sẽ là địa chỉ ảnh mà bạn muốn người đọc nhìn thấy.

Ví dụ: `![Image1](/HoangNH/1.TimhieuMarkdown/images/Image.png)`

Kết quả:
![Image1](/HoangNH/1.TimhieuMarkdown/images/Image.png)

### 2.5 Dùng cho list

Sử dụng `-` hoặc `*` hoặc `+` nếu muốn định dạng câu đó ở dạng list.Trong trường hợp muốn tạo thêm lớp level thấp hơn thì thêm 2 khoảng trắng vào nữa.

Ví dụ: `- dong 1  - dong 2`

Kết quả: 
- line 1
  - line 2

### 2.6 Dùng cho Blockquote

Sử dụng `>` nếu muốn định dạng câu đó ở dạng quote.

Ví dụ: `> Blockquote`

Kết quả: 
> Blockquote 

### 2.7 Tạo bảng

Tạo bảng theo cú pháp:
- Ký tự `|` tách các cột riêng lẻ trong bảng.
- Dấu `-` hoạt động như một hàng phân cách để tách header khỏi phần body.
- Dấu `:` căn chỉnh nội dung ô.

Ví dụ:
| Cột 1 |  Cột 2 | Cột 3|
|:------|:---------|:------|
|ND1| ND2 | ND3 |

### 2.8 Dùng cho Strikethrough

Sử dụng `~~` ở đầu (hoặc đầu và cuối câu) nếu muốn gạch ngang giữa chữ của câu đó.

Ví dụ: `~~ Text here ~~`

Kết quả: ~~Text here~~




