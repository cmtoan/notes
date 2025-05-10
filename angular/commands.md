# Lệnh

## Cài đặt Angular

Angular CLI (command line interface) là một công cụ do Angular cung cấp để ta có thể dễ
dàng tạo một ứng dụng Angular.

Ta cài đặt Angular cli bằng cách dùng lệnh npm, đây không phải là một lệnh của hệ thống.
Lệnh này dùng Node's Package Manager, nó đòi hỏi ta phải cài đặt Node JS, là ngôn ngữ 
lập trình phía server. Ta có thể tải nó về tại trang nodejs.org

Ta cài Nodejs vì hai lý do sau: package manager nodeJS sẽ tự động cài đặt với nó Node
Package Manager. Nó cho phép ta truy xuất đến package manager này, mà ta sẽ dùng nó
để quản lý các dependencies. Ta dùng nó ngay cả cho những dự án không phải phía server.
Npm là package manager cho frontend và cho bất cứ loại dự án JavaScript. Như vậy lý do
thứ nhất là để truy xuất đến Node package manager. 

Lý do thứ hai là để test ứng dụng, để xem ứng dụng chạy ra sao, ta cần một web server. 
Tuy rằng ta có thể nhấp đúp chuột vào tập tin html, nhưng thực ra nó dùng file protocole 
chứ không dùng http protocole. Và điều này sẽ không cho phép ta truy cập đến nhiều feature
mà ta muốn thấy để thực sự thấy nó hoạt động ra sao trong một browser nhìn thấy bởi người
dùng cuối.

CLI mà ta cài đặt sẽ thực sự cho phép ta truy xuất đến việc development và testing server
như thế, và bên trong hậu trường nó cũng dùng NodeJS.

Ta cài Angular Cli với lệnh sau `npm install -g @angular/cli` : npm tức Node Package Manager
được tự động cài đặt khi ta cài Node.js, `-g` để cài nó globally trên máy của ta, do đó
ta có thể truy xuất đến CLI ở bất cứ đâu trên máy. Và tên của package là `@angular/cli`.
Trên Linux ta phải thêm sudo ở đầu lệnh để cài đặt `sudo npm install -g @angular/cli`

````
$ npm install -g @angular/cli
$ ng new my-app
$ cd my-app
$ ng serve
````

Update phiên bản của npm
````
$ npm install -g npm@11.2.0
````

## Các lệnh khi lập trình với Angular

Phát sinh một component `ng generate component <component-name>`
````
$ ng generate component articles
````

Hoặc lệnh viết tắt của lệnh trên
````
$ ng g c articles
````

Lệnh này sẽ tạo ra các tập tin
