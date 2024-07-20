# Vim

## Một số lệnh thông dụng

| Lệnh           | Giải thích                                                    |
|----------------|---------------------------------------------------------------|
| `vim test.txt` | Tạo tập tin                                                   |
| `i` hoặc `a`   | Nhấn i hoặc a để vào chế độ insert                            |
| `ESC`          | Nhấn ESC để thoát chế độ insert, trở về chế độ normal         |
| `:q!`          | Thoát cửa sổ hiện thời, không lưu lại, nhưng không xóa buffer |
| `:bd!`         | Xóa buffer hiện thời                                          |

### 1. Copy, delete, cut, past

#### Copy (yank)

| Lệnh        | Giải thích                                             |
|-------------|--------------------------------------------------------|
| `yy hoặc Y` | sao chép dòng hiện thời (yank cho dễ nhớ)              |
| `50yy`      | sao chép 50 dòng kể từ dòng hiện thời ở vị trí con trỏ |
| `y$`        | sao chép từ vị trí con trỏ đến cuối dòng               |
| `y^`        | sao chép từ đầu dòng đến vị trí con trỏ                |
| `yiw`       | sao chép từ (word) hiện thời                           |

#### Move

| Lệnh    | Giải thích                           |
|---------|--------------------------------------|
| `:m 3`  | Di chuyển dòng đến hàng thứ 3.       |
| `:m -2` | Di chuyển dòng lên phía trên 2 dòng. |

#### Delete (Cut)

| Lệnh               | Giải thích                                                                                                                        |
|--------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| Shift+`d`          | xóa nội dung dòng hiện thời.                                                                                                      |
| `dd`               | xóa dòng hiện thời, vim chép dòng này vào clipboard, giống như ta thực hiện thao tác cut.                                         |
| `dk`               | xóa dòng hiện thời, và dòng trên nó.                                                                                              |
| `dj`               | xóa dòng hiện thời, và dòng dưới nó.                                                                                              |
| `d15d` hoặc `15dd` | Xóa 15 dòng kể từ dòng hiện thời.                                                                                                 |
| `d$`               | Xóa kể từ con trỏ đến cuối dòng.                                                                                                  |
| `dw`               | Xóa một từ từ chỗ con trỏ bao gồm khoảng trắng sau từ đó.                                                                         |
| Shift+`s` tức `S`  | xóa dòng hiện thời (it should delete the current line and put you in insert mode at the correct indentation level for this line.) |

#### Cut

| Lệnh | Giải thích                                                         |
|------|--------------------------------------------------------------------|
| `cw` | Cắt một từ từ chỗ con trỏ đến khoảng trắng. Rồi vào chế độ insert. |

#### Past

| Lệnh        | Giải thích                                                                                           |
|-------------|------------------------------------------------------------------------------------------------------|
| `p`         | Dán phần sao chép **sau** dòng hiện thời                                                             |
| `13p`       | Dán phần sao chép **sau** dòng hiện thời 13 lần                                                      |
| `Shift + p` | Dán phần sao chép **trước** dòng hiện thời                                                           |
| `yy`, `p`   | Copy rồi past : copy dòng hiện thời với lệnh yy, sau đó di chuyển tới chỗ cần dán rồi dán với lệnh p |
| `dd`, `p`   | Cut rồi past : cut dòng hiện thời với lệnh dd, sau đó di chuyển tới chỗ cần dán rồi dán với lệnh p   |

### 2. Undo, redo

| Lệnh                   | Giải thích                                                          |
|------------------------|---------------------------------------------------------------------|
| `u hoặc :u hoặc :undo` | Undo : Ở chế độ bình thường dùng lệnh u để undo                     |
| `4u`                   | undo 4 lần (tính là 4 lần chuyển từ chế độ bình thường sang insert) |
| `Ctrl + r`             | Redo                                                                |
| `5 + Ctrl + r`         | Redo 5 lần                                                          |

### 3. Di chuyển con trỏ

| Lệnh             | Giải thích                                                                                              |
|------------------|---------------------------------------------------------------------------------------------------------|
| `$`              | Ở chế độ normal (nhấn ESC), di chuyển con trỏ đến cuối dòng.                                            |
| `k (↑) và j (↓)` | k (↑) và j (↓) Để di chuyển lên xuống dòng.                                                             |
| `12j`            | ta có thể viết số trước khi nhấn các nút k (↑) và j (↓). Chẳng hạn 12j để chuyển con trỏ xuống 12 dòng. |
| `gg`             | Ở chế độ normal (nhấn ESC), di chuyển con trỏ về đầu tập tin                                            |
| `G`              | Ở chế độ normal (nhấn ESC), di chuyển con trỏ về cuối tập tin                                           |
| `%`              | Ở vị trí dấu ngoặc `({[`, `)}]` để di chuyển con trỏ qua lại đến các dấu ngoặc này                      |
| `w`              | Di chuyển đến từ (word) hoặc thành tố tiếp theo.                                                        |
| `W`              | Di chuyển đến từ (word) hoặc thành tố tiếp theo sau khoảng trắng.                                       |
| `b`              | Di chuyển về trước một từ (back)                                                                        |

### 4. Chế độ visual

Chuyển sang chế độ Visual để thấy các phần được làm nổi bật khi được chọn với các lệnh sau:

| Lệnh                   | Giải thích                                                                                                                              |
|------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| `V`                    | Ở chế độ normal (nhấn `ESC`), Nhấn `Shift+v` (**V** in hoa) để chuyển sang chế độ Visual cho dòng (line visual mode)                    |
| `v`                    | nhấn `v` in thường sẽ chuyển sang chế độ visual cho kí tự (character visual mode)                                                       |
| `Ctrl+v` hoặc `Ctrl+q` | để chuyển sang chế độ visual block mode (vertical virtual mode). Trong Windows thì Ctrl+v dành cho past nên ta chỉ có thể dùng `Ctrl+q` |

#### Thực thi lệnh shell trong chế độ visual
Trong Vim, gõ
````
echo Hello
echo $((1+2))
````

Tại dòng này, nhấn `ESC`, Nhấn `Shift+v` để chuyển sang chế độ visual

Sau đó gõ lệnh `:!sh` rồi nhấn Enter để gọi lệnh shell cho câu lệnh echo này.

#### Thực thi lệnh của linux trong chế độ visual
Trong Vim, gõ
````
Hello
World
Hello
````

Tại dòng này, nhấn `ESC`, Nhấn `ggVG` để chọn toàn bộ các dòng và chuyển sang chế độ visual

Sau đó gõ lệnh `:!sort` rồi nhấn Enter để sắp thứ tự các dòng này.

Hoặc Sau đó gõ lệnh `:!sort | uniq` rồi nhấn Enter để sắp thứ tự các dòng này và chỉ giữ lại các giá trị duy nhất (không giống nhau).

Hoặc Sau đó gõ lệnh `:!sort | uniq -c` sắp xếp như trên và thêm đếm số các giá trị giống nhau ở trước mỗi dòng.

### 5. Chọn text (Select)

| Lệnh          | Giải thích                                                                                                                                                                                                              |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `ggVG`        | Chọn toàn bộ (select all tương đương với Ctrl+a) : * Tức `ESC` để về chế độ normal, rồi đặt con trỏ ở đầu tập tin (`gg`). * Tiếp theo chuyển sang chế độ visual để chọn (`V`), cuối cùng là chọn đến cuối tập tin (`G`) |
| `v`, rồi `%`  | Chọn tất cả giữa hai dấu ngoặc : chuyển sang chế độ visual `v`, ở vị trí dấu mở/đóng ngoặc, nhấn `%` để chuyển đến dấu đóng/mở ngoặc còn lại.                                                                           |
| `v`, `i`, `w` | Chọn một từ : chuyển sang chế độ visual `v`, ở một từ, nhấn `i` (inside) để vào trong từ đó, rồi `w` để chọn từ đó.                                                                                                     |
| `v`, `a`, `w` | Chọn một từ và espace sau đó : chuyển sang chế độ visual `v`, ở một từ, nhấn `a` rồi `w` để chọn từ đó và espace sau đó.                                                                                                |
| `v`, `i`, `"` | Ví dụ {("hello world")} : Chọn toàn bộ trong ngoặc kép : chuyển sang chế độ visual `v`, ở trong ngoặc kép nhấn `i` rồi `"` để chọn toàn bộ trong ngoặc kép.                                                             |
| `v`, `a`, `"` | Ví dụ {("hello world")} : Chọn toàn bộ trong ngoặc kép kể cả ngoặc kép : chuyển sang chế độ visual `v`, ở trong ngoặc kép nhấn `a` rồi `"` để chọn toàn bộ trong ngoặc kép và cả ngoặc kép.                             |

### 6. Thêm text vào nhiều dòng cùng một lúc

#### Lệnh :normal

* Chọn một vài dòng để áp dụng lệnh :normal. Chẳng hạn, ta chọn toàn bộ các dòng của một tập tin với lệnh `ggVG`

* Sau đó gõ lệnh `:normal` hoặc `:norm` như sau rồi nhấn Enter.

| Lệnh        | Giải thích                                                                    |
|-------------|-------------------------------------------------------------------------------|
| `:norm IHi` | Ở đây I sẽ thêm từ "Hi" vào bên trái của mỗi dòng.                            |
| `:norm A;`  | Dùng A ở đây để thêm vào cuối dòng. Ở đây ";" sẽ được thêm vào cuối mỗi dòng. |

#### Thêm/bớt tab trước các dòng

* Chọn toàn bộ các dòng của một tập tin với lệnh `ggVG`
* Shift+`>` để thêm tab vào các dòng
* Shift+`<` để bớt tab khỏi đầu các dòng
* Shift+`.` để lặp lại thao tác vừa thực hiện

#### Ctrl+v hoặc Ctrl+q visual block mode (vertical virtual mode)

| Lệnh                                   | Giải thích                                                                                                                                                                                                                                                                                                        |
|----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Ctrl+v` hoặc `Ctrl+q`                 | Để chuyển sang chế độ visual block mode. Trong Windows thì Ctrl+v dành cho past nên ta chỉ có thể dùng Ctrl+q                                                                                                                                                                                                     |
| `Ctrl+q` rồi `o`                       | Khi đang trong chế độ visual block mode, nhấn `o` để thay đổi hướng và kích thước của block đã chọn.                                                                                                                                                                                                              |
| `ESC`, `Ctrl+q`, `Shift+i`, `ESC`      | Thêm text vào đầu nhiều dòng cùng một lúc : * Nhấn `ESC` để vào chế độ normal, * `Ctrl+q` để vào chế độ visual block mode, * Di chuyển lên xuống để chọn nhiều dòng, * Nhấn `Shift+i` và đánh text muốn thêm vào đầu dòng, * Nhấn `ESC` để thêm vào tất cả các dòng được chọn                                     |
| `ESC`, `Ctrl+q`, `$`, `Shift+a`, `ESC` | Thêm text vào cuối nhiều dòng cùng một lúc : * Nhấn `ESC` để vào chế độ normal, * `Ctrl+q` để vào chế độ visual block mode, * Di chuyển lên xuống để chọn nhiều dòng, * Nhấn `$` để chọn đến cuối dòng, * Nhấn `Shift+a` và đánh text muốn thêm vào cuối dòng, * Nhấn `ESC` để thêm vào tất cả các dòng được chọn |

## Hiển thị số thứ tự dòng

### 1. Hiển thị số thứ tự dòng tuyệt đối (Absolute line numbers)

| Lệnh                             | Giải thích                         |
|----------------------------------|------------------------------------|
| `:set number` hoặc `:set nu`     | Bật absolute line numbers          |
| `:set nonumber` hoặc `:set nonu` | Tắt absolute line numbers          |
| `:set number!` hoặc `:set nu!`   | Bật hoặc tắt relative line numbers |

### 2. Hiển thị số thứ tự dòng tương đối (Relative line numbers)

| Lệnh                                      | Giải thích                         |
|-------------------------------------------|------------------------------------|
| `:set relativenumber` hoặc `:set rnu`     | Bật relative line numbers          |
| `:set norelativenumber` hoặc `:set nornu` | Tắt relative line numbers          |
| `:set relativenumber!` hoặc `:set rnu!`   | Bật hoặc tắt relative line numbers |

Để di chuyển lên xuống nhiều dòng, ta có thể viết số trước khi nhấn các nút k (↑) và j (↓).
Chẳng hạn 12j để chuyển con trỏ xuống 12 dòng.

Xoá 10 dòng d10d.

### 3. Hiển thị số thứ tự dòng tuyệt đối và tương đối cùng lúc (“Hybrid” line numbers)

Ta có thể bật/tắt cả hai chế độ hiển thị số thứ tự dòng tuyệt đối và tương đối.
Khi đó tất cả các dòng sẽ có số thứ tự tương đối, ngoại trừ dòng hiện thời tại con trỏ
sẽ có số thứ tự tuyệt đối.

| Lệnh                                                    | Giải thích                       |
|---------------------------------------------------------|----------------------------------|
| `:set number relativenumber` hoặc `:set nu rnu`         | Bật hybrid line numbers          |
| `:set nonumber norelativenumber` hoặc `:set nonu nornu` | Tắt hybrid line numbers          |
| `:set number! relativenumber!` hoặc `:set nu! rnu!`     | Bật hoặc tắt hybrid line numbers |

## Split windows

Ta có thể chia màn hình vim thành nhiều phần.

| Lệnh                   | Giải thích                                                                                                 |
|------------------------|------------------------------------------------------------------------------------------------------------|
| `:split`               | Chia ngang màn hình                                                                                        |
| `:vsplit`              | Chia dọc màn hình                                                                                          |
| `Ctrl + W + direction` | Di chuyển qua lại các màn hình với direction là các nút h(<-), j (↓), k (↑) và l(->) hoặc các nút mũi tên. |

## Số trong vim

Ta có thể tăng/giảm giá trị một số trong vim bằng các lệnh sau.

| Lệnh                        | Giải thích                                                                          |
|-----------------------------|-------------------------------------------------------------------------------------|
| `Ctrl+a`                    | ESC và để con trỏ ở trước một số, khi nhấn `Ctrl+a` sẽ tăng số này lên 1 đơn vị     |
| Chọn nhiều dòng, `Ctrl+a`   | tăng số ở các dòng này lên 1 đơn vị                                                 |
| Chọn nhiều dòng, `g+Ctrl+a` | tăng số ở các dòng này lên 1 đơn vị, và số của dòng sau lớn hơn số của dòng trước   |
| `Ctrl+x`                    | ESC và để con trỏ ở trước một số, khi nhấn `Ctrl+x` sẽ giảm số này xuống 1 đơn vị   |
| Chọn nhiều dòng, `Ctrl+x`   | giảm số ở các dòng này xuống 1 đơn vị                                               |
| Chọn nhiều dòng, `g+Ctrl+x` | giảm số ở các dòng này xuống 1 đơn vị, và số của dòng sau nhỏ hơn số của dòng trước |

## Invoking scripts/command

## Creating (dynamic) snippets

## Using fzf/search/explorer inside Vim

## Cấu hình cho vim

Tạo tập tin ~/.vimrc

````
$ vim ~/.vimrc
````

Thêm vào tập tin này nội dung sau để hiển thị mặc định số thứ tự dòng tuyệt đối và tương đối

````
set nu
set rnu
````

## Tham khảo

https://learnbyexample.github.io/vim_reference/Normal-mode.html

https://jeffkreeftmeijer.com/vim-number/

https://www.youtube.com/watch?v=5BU2gBOe9RU

https://www.warp.dev/terminus/vim-vi-page-up-and-down-controls

https://vim.fandom.com/wiki/Inserting_text_in_multiple_lines

