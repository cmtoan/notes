# Intellij

## Shortcut

### Completion

| Phím tắt         | Hiệu ứng                                                                                                                          |
|------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| Ctrl+Shift+Enter | thêm dấu chấm phẩy sau dấu nháy ("";) hoặc kết thúc câu lệnh ({}) hoặc gõ "for" hoặc "if" rồi gõ tổ hợp phím tắt này sẽ thêm (){} |
| Alt+Enter        | Hiển thị context actions, sửa lỗi gõ nhầm (fix typo)                                                                              |
| Ctrl+space       | hiển thị code completion                                                                                                          |
| Ctrl+Shift+space | hiển thị smart code completion                                                                                                    |
| Tab              | Gõ vài kí tự đầu rồi tab để thay thế kiểu, chẳng hạn : List<String> => List<Integer>                                              |
| Alt+/            | Cyclic Expand Word                                                                                                                |
| Alt+Shift+/      | Cyclic Expand Word (backward)                                                                                                     |
| Ctrl+/           | Comment //                                                                                                                        |
| Ctrl+Shift+/     | Comment /**/                                                                                                                      |

#### Refactoring

| Phím tắt       | Hiệu ứng                                            |
|----------------|-----------------------------------------------------|
| Ctrl+Alt+v     | nhằm tạo một biến (variable) từ một giá trị (value) |
| (Fn+)Shift+F6  | rename                                              |
| (Fn+)Shift+F10 | run                                                 |

#### Edit

| Phím tắt | Hiệu ứng     |
|----------|--------------|
| Ctrl+y   | xóa một dòng |

#### Postfix completion

| Phím tắt | Hiệu ứng                                                 |
|----------|----------------------------------------------------------|
| .not     | thêm phủ định "!" vào đầu giá trị                        | 
| .nn      | để in giá trị thành "if (value != null) {}"              |
| .null    | để in giá trị thành "if (value == null) {}"              |
| .sout    | để in giá trị với System.out.println(value)              |
| .soutv   | để in giá trị với System.out.println("value = " + value) |

### Selection

| Phím tắt      | Hiệu ứng                                 |
|---------------|------------------------------------------|
| Ctrl+Shift+<- | chọn từ con trỏ đến đầu từ               |
| Ctrl+w        | chọn một từ, ở cuối dòng sẽ chọn cả dòng |

### Zoom

| Phím tắt           | Hiệu ứng |
|--------------------|----------|
| Alt+Shift+ "+" (/) | zoom in  |
| Alt+Shift+ "0" (.) | zoom out |

### Add shortcut

Ctrl+Alt+S
> Keymap > Editor actions > choose one action > right click > Add keyboard Shortcut

### Lookup

#### Tooltip lookup

| Phím tắt     | Hiệu ứng                                                                       |
|--------------|--------------------------------------------------------------------------------|
| Ctrl+p       | Ở trong một hàm nhấn tổ hợp phím này để xem các đối số của hàm                 |
| Ctrl+Shift+p | Ở trong một hàm nhấn tổ hợp phím này để xem tooltip, giá trị trả vể của hàm... |
| Ctrl+q       | xem Java doc                                                                   |
| Ctrl+Shift+i | hiển thị nhanh code của hàm, biến ... hiện thời ngay con trỏ                   |

#### Navigation

| Phím tắt                        | Hiệu ứng                                             |
|---------------------------------|------------------------------------------------------|
| Ctrl+b                          | đi vào code của hàm, biến ... hiện thời ngay con trỏ |
| Right click > Local history     | hiển thị local history                               |
| Shift+Shift > Jshell console... | hiển thị jshell console                              |

### Một số tính năng khác

#### Language injection

//language=JSON

Alt+Enter > Inject language or reference

Alt+Enter > Edit JSON fragment

````
    //language=XML
    String text = """
            html>body>div*3
            """; // then tab
````

#### Jshell console

Shift+Shift > Jshell console... => hiển thị jshell console

Gõ

````
"hello" // Ctrl+Enter
"hello".substring(1)    // Ctrl+Enter
````

#### Scratch file

Ctrl+Shift+Alt+Insert

hoặc

Shift+Shift > Scratch File

#### Check Regex

Di chuyển đến Regex, nhấn Alt+Enter, rồi chọn Check RegExp

````Java
Pattern pattern = Pattern.compile("[0-9]"); // Alt+Enter > Check RegExp
````

#### Search Structurally

Shift+Shift > Search Structurally

#### Docker

Install Docker plugin

Shift+Shift > Docker

#### Http Client

Shift+Shift > Http Client (Ultimate version)



