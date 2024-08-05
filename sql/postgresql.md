# Sql

## PostgreSQL Regex

| Toán tử  | Giải thích |
| -------- | ------- |
| ~   | Dùng khi so sánh xem **có phù hợp** với Regular expression hay không và chữ **cái hay thường là quan trọng** (Case sensitive) |
| ~*  | Dùng khi so sánh xem **có phù hợp** với Regular expression hay không và chữ **cái hay thường là không quan trọng** (Case sensitive)|
| !~  | Dùng khi so sánh xem **có không phù hợp** với Regular expression hay không và **chữ cái hay thường là quan trọng** (Case sensitive)|
| !~* | Dùng khi so sánh xem **có không phù hợp** với Regular expression hay không và **chữ cái hay thường là không quan trọng** (Case sensitive) |

Ví dụ :

Kiểm tra xem một chuỗi chỉ gồm các số

````
select * from table_test where column_test !~* '^[0-9]\d*$';
````
