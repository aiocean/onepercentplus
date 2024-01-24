---
quickshare-date: 2022-12-15 22:21:37
quickshare-url: "https://noteshare.space/note/clbp8bw7o2120101mdz99fnb4h#ojQBXrBZQOtYHlmQWuLOfBQCYu+uvUwf5exolmiHzuY"
---
In the TrueProfit project[^1], I have migrated between two different Git servers. Initially, I used Gitlab, then switched to Bitbucket, and now I am in the process of transferring some repositories to Github.

However, I did not encounter many difficulties during this migration process thanks to the use of a custom domain.

If using the Git URL of each service, the code will be imported as follows:

```go
import "bitbucket.com/mongo-driver/bson/primitive"
```

So when switching to another service, you will have to find and edit the code in every file, which is very inconvenient. If there are mistakes, it can lead to many difficult-to-debug errors. In a serverless system, mistakes are easy to occur.

Nhưng ngay từ đầu, mình đã sử dụng custom domain cho go, nên không cần thay đổi gì trong code. Cũng như có thể sử dụng nhiều git server khác nhau cùng lúc.

Vấn đề còn lại là làm sao để go mod biết remote url để pull code về.

# Cách go mod get code

Custom domain is pointed to a server or Lambda function, this server receives requests from `go mod` and returns the information that `go mod` needs to get the source.

When using `go get`, Go will send a request to the URL with the query `go-get=1`. At this point, the server needs to return an HTML file with a `go-import` meta tag containing the content path to the Git repository. For example:

```html
<meta name="go-import" content="pkg.trueprofit.goldencloud.dev/internalfns git https://bitbucket.org/trueprofit/internalfns.git">
```

Therefore, we just need to make sure that the server returns the content like that.

# Server installation

> At first, I used nginx [^2] and then switched to lambda [^3].

![[Cài đặt custom domain cho go mod sử dụng nginx]]

![[Cài đặt custom domain cho go mod bằng aws lambda]]

# Sử dụng

Đồng thời  go get cũng thực hiện checksum repo bằng dịch vụ của go, nhưng private repo thì không được checksum vì vậy sẽ bị lỗi.

Nếu bạn server trả về private repo, thì bạn cần phải setup biết môi trường `GOPRIVATE` và chỉ định git sử dụng `ssl` thay vì `http`:

![[Go mod import private repo]]

[^1]: [[Tại sao TrueProfit?]]
[^2]: [[Cài đặt custom domain cho go mod sử dụng nginx]]
[^3]: [[Cài đặt custom domain cho go mod bằng aws lambda]]