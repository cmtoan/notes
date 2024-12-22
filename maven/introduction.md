# Giới thiệu

## Quy ước về cấu trúc thư mục và tập tin trong một project Maven

Một dự án maven thường có cấu trúc theo quy ước sau:

````
└───maven-project
    ├───pom.xml
    ├───README.md
    ├───NOTICE.md
    ├───LICENSE.md
    ├───src
    │    ├───main
    │    │   ├───java
    │    │   ├───resources
    │    │   ├───filters
    │    │   └───webapp
    │    ├───test
    │    │   ├───java
    │    │   ├───resources
    │    │   └───filters
    │    ├───it
    │    ├───assembly
    │    └───site
    └───target
````

### Thư mục gốc

* pom.xml : tập tin mô tả về project, nó định nghĩa các dependency và modules cần thiết cho vòng đời của project maven.
* LICENSE.md : thông tin về license của dự án.
* README.md : tóm tắt về dự án
* NOTICE.md : thông tin về các thư viện bên thứ ba dùng trong dự án.
* src/main : chứa source code và resources của dự án.
* src/test : chứa test và resources test.
* src/it : thường dùng cho integration tests cho Maven Plugin
* src/site : site documentation được tạo bằng cách dùng Maven Site Plugin
* src/assembly : mô tả cấu hình assembly để đóng gói binaries
* target : dùng để trữ tất cả output của quá trình build dự án.


### Thư mục src/main

* src/main/java : chứa source code Java
* src/main/resources : chứa các tập tin cấu hình(.xml, .properties, .yaml, configuration files) và những tập tin cấu hình cho từng evironment, các tập tin khác như i18n files.
* src/main/webapp : dành cho ứng dụng web, chứa các tập tin JavaScript, CSS, HTML, templates, hình ảnh...
* src/main/filters : chứa các tập tin để inject values vào configuration properties trong thư mục resources trong quá trình build.

### src/test

Không có thư mục nào trong thư mục src/test này sẽ được đóng gói vào artifact.

* src/test/java : source code Java để tests
* src/test/resources : các tập tin cấu hình ... dùng bởi tests
* src/test/filters : chứa các tập tin để inject values vào configuration properties trong thư mục resources trong quá trình test.

### Khi làm việc với front-end

* src/main/webapp : là nơi chứa code source của ứng dụng web.
* target/classes/static : là nơi ứng dụng web được đóng gói.

**Spring Boot** sẽ tự động thêm static web resources nằm ở bất kỳ thư mục nào dưới đây trong classpath:

* /META-INF/resources/
* /resources/
* /static/
* /public/

Chẳng hạn các thư mục src/main/resources hay /static mặc định nằm trong classpath thì các tập tin
nằm trong đó sẽ được tự động thêm vào static web resources.

**Quarkus** sẽ tự động thêm static web resources nằm ở bất kỳ thư mục nào dưới đây:
* target/META-INF/resources/ : đây là vị trí tiêu chuẩn dành cho resources của tập tin jar được định nghĩa trong đặc tả của Servlet.
* target/classes/static

## Tham khảo

https://maven.apache.org/guides/introduction/introduction-to-the-standard-directory-layout.html

````
````