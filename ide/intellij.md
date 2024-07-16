# Intellij

## Shortcut

### Completion

| Phím tắt         | Hiệu ứng                                                                                                                          |
|------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| Ctrl+Shift+Enter | thêm dấu chấm phẩy sau dấu nháy ("";) hoặc kết thúc câu lệnh ({}) hoặc gõ "for" hoặc "if" rồi gõ tổ hợp phím tắt này sẽ thêm (){} |
| Alt+Enter        | Hiển thị context actions                                                                                                          |
| Ctrl+space       | hiển thị code completion                                                                                                          |
| Ctrl+Shift+space | hiển thị smart code completion                                                                                                    |
| Tab              | Gõ vài kí tự đầu rồi tab để thay thế kiểu, chẳng hạn : List<String> => List<Integer>                                              |
| Alt+/            | Cyclic Expand Word                                                                                                                |
| Alt+Shift+/      | Cyclic Expand Word (backward)                                                                                                     |
| Ctrl+/           | Comment //                                                                                                                        |
| Ctrl+Shift+/     | Comment /**/                                                                                                                      |

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

| Phím tắt     | Hiệu ứng                                                                       |
|--------------|--------------------------------------------------------------------------------|
| Ctrl+b       | đi vào code của hàm, biến ... hiện thời ngay con trỏ                           |

### Language injection

//language=JSON

Alt+Enter > Inject language or reference

Alt+Enter > Edit JSON fragment

````
    //language=XML
    String text = """
            html>body>div*3
            """; // then tab
````
    
