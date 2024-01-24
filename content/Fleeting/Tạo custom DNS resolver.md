# Tạo custom DNS resolver
Ta có thể tạo các file trong thư mục /etc/resolver. Mac sẽ tìm các file này và phân giải domain (service name) thành ip.

1.  Tạo thư mục  `/etc/resolver/
2. Trong thư mục này, tạo file với tên chính là domain mà bạn muốn resolve. trong trường hợp này là myhugelab.local 
4.  Edit file này với nội dung như sau:

```
domain myhugelab.local
search myhugelab.local
nameserver 10.0.0.53
nameserver 10.0.0.54
```
