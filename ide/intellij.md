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
| Shift+(Fn+)F6  | rename                                              |
| Shift+(Fn+)F10 | run                                                 |

#### Edit

| Phím tắt | Hiệu ứng     |
|----------|--------------|
| Ctrl+y   | xóa một dòng |

#### Live templates

Xem thêm Live templates

| Phím tắt       | Hiệu ứng                                                                             |
|----------------|--------------------------------------------------------------------------------------|
| main hoặc psvm | để có "public static void main(String[] args)"                                       |
| sout           | để in giá trị với System.out.println(value)                                          |
| soutv          | để in giá trị với System.out.println("value = " + value)                             |
| soutm          | để in lớp hiện thời với System.out.println("CurrentClasss")                          |
| soutp          | để in hàm hiện thời với đối số System.out.println("args = " + Arrays.toString(args)) |
| iter hoặc I    | để in vòng lặp "for (String string : list) {}"                                       |
| itm            | để in vòng lặp "for (Map.Entry<String, Integer> entry : map.entrySet()) {}"          |

#### Postfix completion

Sau một giá trị, gõ các phím sau :

| Phím tắt | Hiệu ứng                                                 |
|----------|----------------------------------------------------------|
| .not     | thêm phủ định "!" vào đầu giá trị                        | 
| .if      | để in giá trị thành "if (value) {}"                      | 
| .nn      | để in giá trị thành "if (value != null) {}"              |
| .null    | để in giá trị thành "if (value == null) {}"              |
| .sout    | để in giá trị với System.out.println(value)              |
| .soutv   | để in giá trị với System.out.println("value = " + value) |
| .iter    | để in vòng lặp "for (String string : list) {}"           | 

### Selection

| Phím tắt         | Hiệu ứng                                 |
|------------------|------------------------------------------|
| Ctrl+Shift+<-    | chọn từ con trỏ đến đầu từ               |
| Ctrl+w           | chọn một từ, ở cuối dòng sẽ chọn cả dòng |
| Alt+Shift+Insert | vào chế độ chọn theo cột                 |

### Zoom

| Phím tắt           | Hiệu ứng |
|--------------------|----------|
| Alt+Shift+ "+" (/) | zoom in  |
| Alt+Shift+ "0" (.) | zoom out |

### Keymap

#### Add shortcut

Ctrl+Alt+S
> Keymap > Editor actions > choose one action > right click > Add keyboard Shortcut

#### Add abbreviation

> Keymap > Editor actions > choose one action > right click > Add Abbreviation

### Lookup

#### Tooltip lookup

| Phím tắt     | Hiệu ứng                                                                       |
|--------------|--------------------------------------------------------------------------------|
| Ctrl+p       | Ở trong một hàm nhấn tổ hợp phím này để xem các đối số của hàm                 |
| Ctrl+Shift+p | Ở trong một hàm nhấn tổ hợp phím này để xem tooltip, giá trị trả vể của hàm... |
| Ctrl+q       | xem Java doc                                                                   |
| Ctrl+Shift+i | hiển thị nhanh code của hàm, biến ... hiện thời ngay con trỏ                   |

### Navigation

Di chuyển con nháy (caret):

| Phím tắt             | Hiệu ứng                                              |
|----------------------|-------------------------------------------------------|
| Ctrl+<-              | move Caret to the next word                           |
| Ctrl+->              | move Caret to the previous word                       |
| Ctrl+<               | move Caret forward a paragraph                        |
| Ctrl+*               | move Caret backward a paragraph                       |
| Ctrl+Shift+<         | move Caret forward a paragraph with selection         |
| Ctrl+Shift+*         | move Caret backward a paragraph with selection        |
| Ctrl+Alt+<-          | Navigate Backward                                     |
| Ctrl+Alt+->          | Navigate Forward                                      |
| Ctrl+Shift+Backspace | Navigate the last edited location                     |
| Ctrl+M               | Find current caret location                           |
| Ctrl+Shift+M         | To move caret between matching code block braces ({}) |
| Ctrl+[               | move Caret to code block start                        |
| Ctrl+Shift+[         | move Caret to code block start with selection         |
| Ctrl+]               | move Caret to code block end                          |
| Ctrl+Shift+]         | move Caret to code block end with selection           |

Di chuyển con nháy (caret) giữa các thay :

| Phím tắt         | Hiệu ứng                    |
|------------------|-----------------------------|
| Ctrl+Alt+Shift+↓ | Navigate -> Next Change     |
| Ctrl+Alt+Shift+↑ | Navigate -> Previous Change |

Di chuyển giữa các tập tin:

| Phím tắt         | Hiệu ứng                                                                              |
|------------------|---------------------------------------------------------------------------------------|
| Ctrl+Shift+A     | Find actions                                                                          |
| Ctrl+E           | Recent files                                                                          |
| Ctrl+Shift+E     | Recent locations                                                                      |
| Ctrl+N           | Navigate->Class                                                                       |
| Ctrl+Shift+N     | Navigate->File                                                                        |
| Ctrl+Shift+Alt+N | Navigate->Symbol (methode name)                                                       |
| Ctrl+B           | Navigate->Declaration : đi vào code của hàm, biến ... hiện thời ngay con trỏ          |
| Ctrl+Shift+B     | Navigate->Type Declaration : đi vào code của kiểu (type) hiện thời ngay con trỏ       |
| Ctrl+Alt+B       | Navigate->Implements                                                                  |
| Ctrl+Alt+Left    | Navigate->Back                                                                        |
| Ctrl+Alt+Right   | Navigate->Forward                                                                     |
| Alt+(Fn+)F1, 1   | Select opened file                                                                    |
| Alt+(Fn+)F7      | Find usages                                                                           |
| Right            | Select child node                                                                     |
| Left             | undo Select child node                                                                |
| Ctrl+Shift+T     | Navigate->Test [Subject] (nhấn tổ hợp phím này để qua lại giữa test và lớp được test) |
| Ctrl+Right       | Di chuyển đến từ tiếp theo                                                            |
| Ctrl+Left        | Di chuyển đến từ trước đó                                                             |

Di chuyển giữa các cửa sổ:

| Phím tắt | Hiệu ứng                  |
|----------|---------------------------|
| Alt+0    | Commit window             |
| Alt+1    | Project window            |
| Alt+3    | Find window               |
| Alt+4    | Run window                |
| Alt+5    | Debug window              |
| Alt+6    | Problem window            |
| Alt+8    | Service window            |
| Alt+9    | Version control window    |
| Esc      | Quay trở lại Editor chính |

| Phím tắt                        | Hiệu ứng                                          |
|---------------------------------|---------------------------------------------------|
| Right click > Local history     | hiển thị local history                            |
| Shift+Shift > Jshell console... | hiển thị jshell console                           |
| Ctrl+Shift+(Fn+)F12             | Hide all window                                   |
| Ctrl+Ctrl                       | Run anything                                      |
| Ctrl+F2                         | Stop, nhấn tổ phím lần thứ hai để kết thúc tất cả |

### Chạy chương trình

| Phím tắt            | Hiệu ứng          |
|---------------------|-------------------|
| Shift+(Fn+)F5       | Run File (Script) |
| Alt+Shift+(Fn+)F10  | Run...            |
| Ctrl+Shift+(Fn+)F10 | Run Coverage      |
| Ctrl+Alt+Shift+I    | Run Inspection    |
| Shift+(Fn+)F10      | (Re)run           |
| Ctrl+(Fn+)F5        | Rerun             |

### Format

| Phím tắt         | Hiệu ứng          |
|------------------|-------------------|
| Ctrl+Alt+O       | Optimize Import   |
| Ctrl+Alt+L       | Reformat code     |
| Ctrl+Alt+I       | Auto-indent lines |
| Ctrl+Alt+Shift+L | Reformat file     |

### Tìm kiếm

| Phím tắt     | Hiệu ứng               |
|--------------|------------------------|
| (Fn+)F3      | Find next from the top |
| Ctrl+(Fn+)F3 | Find next              |

### Xem thay đổi

| Phím tắt    | Hiệu ứng               |
|-------------|------------------------|
| Alt+Shift+C | View -> Recent changes |

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



