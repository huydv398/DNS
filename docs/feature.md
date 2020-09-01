# Features Domain Name System

1. [Tổng quan DNS](#what)
*   [DNS gì?](#what)
*   [Lịch sử hình thành]()
2. [Chức năng của DNS](#funtion)
3. [Hoạt động của DNS](#active)
<!-- 4. [Kiến trúc DNS](#architecture) -->
5. [Domain Registrar DNS Hosting](#Regis)
* [Registrar](#Registrar)
* [Registry](#Registry)
6. [Nhược điểm]()
<a name="what"></a>


<a name=""></a>
<a name=""></a>

## DNS là gì?

* Mở các địa chỉ Internet một cách nhanh chóng.
* Duy trì một thư mục tên miền và dịch chúng sang địa chỉ IP(Internet Protocol)

Ví dụ **DNS**:
* Tôi muốn gọi điện cho A Công nhưng không nhớ số điện thoại của A Công. Tôi sẽ lưu tên và số điện thoại vào Danh bạ của mình. Khi gọi tôi chỉ cần tìm tên A Công thay vì tôi phải nhớ từng số điện thoại của Anh
* Nom na là Tôi không thể nhớ IP facebook, google, Youtube nhưng tôi nhé tên của họ. DNS sẽ giúp tôi tìm ra các địa chỉ IP mà tôi muốn đến thông qua tên domain mà tôi nhớ.

<a name="funtion"></a>

## Chức năng của DNS
* Chức năng chính là phân giải tên miền.
* Đó là một kiến trúc ánh xạ tên đến các địa chỉ để khi người dùng cố gắng truy cập một máy tính khác trên mạng, nó sẽ hướng bạn đến đó.
<a name="active"></a>

## Hoạt động của DNS
### Bước 1: Yều cầu thông tin
Gõ tên miền `cloud365.vn` vào trình duyệt web
* Nó sẽ chạy một truy vấn DNS để tìm câu trả lời về vị trí của trang web.
### Bước 2: Máy chủ ROOT
* DNS hỏi đến Máy chủ ROOT về địa chỉ IP. ROOT phản hồi về DNS là địa chỉ của TLD(Top-Level Domain) Name server.

Ở đây là máy chủ định danh `.VN`
### Bước 3: TLD (Top-Level Domain) Name Servers
Trình phân giải DNS hiện yêu cầu của TLD Name Server cho địa chỉ IP Domain name. TLD Name Server trả lời với địa chỉ Authoritative Name Server của Domain name.

Trong ví dụ, Name Server `.vn` sẽ cung cấp địa chỉ ip cho các máy chủ định danh có thẩm quyền của `cloud365.vn`
### Bước 4: Authoritative DNS Servers
Authoritative DNS Servers giữ bản ghi DNS của domain names necessary cho phân giải DNS. Các bản ghi này được duy trì lý tưởng trong zone file bởi chủ sở hữu tên miền hoặc quản trị viên kỹ thuật chịu trách nhiệm quản lý hành vi chức năng của tên miền. Đây là các bản ghi khác nhau trong một zone file, ví dụ địa chỉ IP của máy chủ nơi lưu trữ trang web, được đại diện bằng bản ghi địa chỉ, thường được gọi là bản ghi **A**. 

### Bước 5: The Record Retrieval- Truy xuất bản ghi
The recursive server- Máy chủ đệ quy lấy bản ghi A cho trang web từ máy chủ định danh có thẩm quyền và lưu trữ nó trên bộ nhớ cache cục bộ của nó. Nếu ai đó đang tìm kiếm một trang web, thông tin sẽ có sẵn ở đó và nó sẽ không phải trải qua toàn bộ quá trình.

### Bước 6: Truy cập trang Web 
Máy chủ đệ quy gửi bản ghi A cho máy tính của bản. PC lưu bản ghi này, đọc IP và chuyển thông tin đến trình duyệt của bạn, sau đó kết nối đến máy chủ web và bạn có thể xem web `www.cloud365.vn`

Mặc dù nó có vẻ là một quá trình dài và phức tạp, nhưng chỉ mất vài giây, đôi khi chỉ micro giây, để toàn bộ quá trình DNS diễn ra.

Với hệ thống này người dùng chỉ cần biết tên miền của bạn. Địa chỉ IP cho từng máy chủ mà trang web của bạn được đặt trên đó không liên qua đến chúng. Nếu bất kỳ cập nhật nào được thực hiện trên trang web hoặc tên miền, DNS để trỏ địa chỉ IP của máy chủ mới của bạn cũng được cập nhật. Khách truy cập của bạn vẫn truy cập trang web của bạn bằng cách chỉ sử dụng trên miền của bạn; mặc dù địa chỉ IP đã thay đổi. Linh hoạt làm cho Internet trở lên mạnh mẽ
<a name="architecture"></a>

## Kiến trúc DNS


<a name="Regis"></a>

## Domain Registrar or DNS Hosting
<a name="Registrar"></a>

### Registrar là gì?
Khi bạn đăng ký một tên miền, bạn thông qua DNS Registrar. Các công ty này thường giao dịch trực tiếp với các khai thác đăng ký kiểm soát danh sách của tất cả các tên miền. Registrar được quản lý bởi IANA(International Assigned Numbers Authority - Cơ quan cấp số được ấn định quốc tế) là một bộ phận của ICANN, một tổ chức phi lợi nhuận điều hành quản lý vùng ROOT trong Hệ thống tên miền DNS.
<a name="Registry"></a>

### Whois - Registry
Bất cứ khi nào bạn chạy thông báo Whois, hoặc giao dịch trực tuyến với dữ liệu "whois", bạn thực sự đang truy vấn với domain name **Registry**. 

Trong hầu hết các trường hợ, bạn sẽ không thực hiện giao dịch trực tiếp với công ty đăng ký DNS Registrar. Hầu hết mọi người mua tên miền của họ thông qua nhà cung cấp dịch vụ lưu trữ web- Web Hosting Provider; Công ty này thay mặt bạn thực hiện tất cả công việc và đăng ký tên miền của bạn thông qua các cơ quan đăng ký Registry.

## Khác biệt
Công ty lưu trữ dịch vụ DNS hosting.
* Công ty lưu trữ tên miền cung cấp dịch vụ DNS như một dịch bổ sung.
* Web hosting providers- Nhà cung cấp dịch vụ lưu trữ web 
* Dedicated DNS hosting companies
>**Lưu ý**: Lưu trữ web về cơ bản là không gian lưu trữ các tệp tin trang web của bạn. Mặc dù lưu trữ DNS là thứ kết nối người dùng trang web và giữ domain trong trạng thái Online.

Các nhà cung cấp dịch vụ lưu trữ DNS chuyên dụng có xu hướng có cơ sở hạ tầng nhanh hơn và đáng tin cậy hơn, được thiết kế từ đầu để lưu trữ lượng truy vấn DNS và không có gì khác.

Tài liệu tham khảo

* [HuyTM](https://docs.google.com/presentation/d/1Nazuf9lVWPWT7XsduJocTok5qswI751hP5WHBU0g6e8/edit#slide=id.g94be251430_0_29)
* [Medium](https://medium.com/)