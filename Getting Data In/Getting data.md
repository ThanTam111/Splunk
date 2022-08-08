# 1. Quy trình thời gian lập chỉ mục của Splunk.
Quy trình thời gian lập chỉ mục có thể được chia làm 3 giai đoạn.
1. Giai đoạn đầu vào: được xử lý tại nguồn ( Forwarder thực hiện ).
* Các nguồn dữ liệu đang được mở và đọc.
* Dữ liệu được xử lý dưới dạng luồng và mọi cài đặt cấu hình được áp dụng cho toàn bộ luồng.
2. Giai đoạn phân tích cú pháp: được xử lý bởi Indexer.
* Dữ liệu được chia thành các sự kiện và có thể thực hiện xử lý nâng cao.
3. Giai đoạn lập chỉ mục.
* Ghi dữ liệu dạng thô và tệp chỉ mục vào đĩa,nơi diễn ra quá trình nén sau lập chỉ mục.
![anh]()

# 2. Các kiểu dữ liệu đầu vào.
* Splunk hỗ trợ nhiều kiểu dữ liệu đầu vào như:
    * Tệp và thư mục( File and Direction)
    * Dữ liệu mạng ( Network data )
    * Script output
    * Windows logs
    * HTTP: using HTTP event colector
* Người dùng có thể thêm dữ liệu đầu vào theo một số cách sau:
    * Apps và add-ons từ Splunkbase
    * Splunk Web
    * CLI
    * Chỉnh sửa nội dung file inputs.conf
# 3. Cài đặt dữ liệu mặc định
Khi lập chỉ mục nguồn dữ liệu, Splunk sẽ chỉ định các giá trị dữ liệu
* Dữ liệu sẽ được áp dụng cho toàn bộ nguồn
* Splunk áp dụng mặc định nếu không được chỉ định
* Cũng có thể ghi đề chúng tại thời điểm nhập liệu hoặc sau đó
![anh]()




