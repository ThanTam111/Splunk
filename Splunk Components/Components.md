# 1. Quá trình xử lý dữ liệu của Splunk
Quá trình xử lý dữ liệu của Splunk chủ yếu có 3 giai đoạn chính đó là :
* Giai đoạn nhập dữ liệu
* Giai đoạn lưu trữ dữ liệu
* Giai đoạn tìm kiếm dữ liệu

![anh1](https://github.com/ThanTam111/Splunk/blob/main/Image/Screenshot_14.png)

## 1.1 Giai đoạn nhập dữ liệu :

Trong giai đoạn này, phần mềm Splunk sử dụng luồng dữ liệu thô từ nguồn của nó, chia nó thành các khối 64K và chú thích mỗi khối bằng các khóa siêu dữ liệu. Các khóa siêu dữ liệu bao gồm tên máy chủ, nguồn và loại nguồn của dữ liệu. 
Các khóa cũng có thể bao gồm các giá trị được sử dụng nội bộ, chẳng hạn như mã hóa ký tự của luồng dữ liệu và các giá trị kiểm soát việc xử lý dữ liệu trong giai đoạn lập chỉ mục, chẳng hạn như chỉ mục mà các sự kiện sẽ được lưu trữ.

## 1.2 Giai đoạn lưu trữ dữ liệu :

Lưu trữ dữ liệu bao gồm hai giai đoạn: Phân tích cú pháp và Lập chỉ mục.
* Trong giai đoạn phân tích cú pháp phần mềm Splunk kiểm tra, phân tích và biến đổi dữ liệu để chỉ trích xuất thông tin có liên quan. Đây còn được gọi là xử lý sự kiện. Chính trong giai đoạn này, phần mềm Splunk chia luồng dữ liệu thành các sự kiện riêng lẻ. Giai đoạn phân tích cú pháp có nhiều giai đoạn phụ.
    * Chia dòng dữ liệu thành các dòng riêng lẻ.
    * Xác định, phân tích cú pháp và đặt dấu thời gian.
    * Chú thích các sự kiện riêng lẻ với siêu dữ liệu được sao chép từ các khóa toàn nguồn.
    * Chuyển đổi dữ liệu sự kiện và siêu dữ liệu theo quy tắc chuyển đổi regex
* Trong giai đoạn lập chỉ mục, phần mềm Splunk ghi các sự kiện được phân tích cú pháp vào chỉ mục trên đĩa. Nó ghi cả dữ liệu thô được nén và tệp chỉ mục tương ứng. Lợi ích của lập chỉ mục là dữ liệu có thể được truy cập dễ dàng trong quá trình tìm kiếm.

## Giai đoạn tìm kiếm dữ liệu:

Giai đoạn này kiểm soát cách người dùng truy cập, xem và sử dụng dữ liệu được lập chỉ mục. Là một phần của chức năng tìm kiếm, phần mềm Splunk lưu trữ các đối tượng do người dùng tạo, chẳng hạn như báo cáo, các loại sự kiện, trang tổng quan, cảnh báo và trích xuất trường. Chức năng tìm kiếm cũng quản lý quá trình tìm kiếm.

Các giai đoạn truyền dẫn dữ liệu khác nhau mà theo đó các thành phần Splunk khác nhau nằm trong đó.

![anh1](https://github.com/ThanTam111/Splunk/blob/main/Image/Screenshot_15.png)
# 2.Các thành phần của Splunk.
Splunk gồm có 3 thành phần chính đó là :

![anh1](https://github.com/ThanTam111/Splunk/blob/main/Image/Screenshot_2.png)

## 2.1.Splunk Forwarder.
* Splunk Forwarder thu thập và gửi dữ liệu từ máy được cài đặt về Indexer.
* Tiêu tốn một lượng nhỏ tài nguyên trên máy cài đặt Splunk FWD.
* Forwarder là phương thức chủ yếu để đẩy log về Splunk Indexer.

![anh1](https://github.com/ThanTam111/Splunk/blob/main/Image/Screenshot_7.png)

## 2.2. Splunk Indexer.
* Xử lý dữ liệu, lưu trữ thành các sự kiện để hỗ trợ tìm kiếm nhanh và phân tích.
* Tổ chức phân loại các sự kiện theo thời gian (Đơn vị bucket). 

![anh1](https://github.com/ThanTam111/Splunk/blob/main/Image/Screenshot_3.png)

## 2.3. Splunk Search Head.
* Sử dụng SPL (Splunk Power Language) để thực hiện các truy vấn xuống dữ liệu tại Indexer.
* Điều hướng các truy vấn của người dùng tới các Indexer.
* Tổng hợp kết quả và trích xuất các trường từ sự kiện đến người dùng.
* Cung cấp một số công cụ để tạo báo cáo, biểu đồ.

![anh1](https://github.com/ThanTam111/Splunk/blob/main/Image/Screenshot_5.png)

Ngoài ba thành phần chính trên của Splunk thì  cũng có các thành phần khác nhưng không được phổ biến.
![anh1]()


# 3. Mô hình triển khai.

Có 5 mô hình triển khai phổ biến đó là : 
* Splunk Deployment - Standalone.
* Splunk Deployment - Basic.
* Splunk Deployment - Multi-Instance.
* Splunk Deployment - Increasing capacity.
* Splunk Deployment - Index Cluster.

## Splunk Deployment - Standalone
Tất cả các chức năng trong một phiên bản duy nhất của Splunk.
Sử dụng để thử nghiệm,cho cá nhân và học tập.

![anh](https://github.com/ThanTam111/Splunk/blob/main/Image/Screenshot_9.png)

## Splunk Deployment - Basic
Tương tự như mô hình Standalone.
Quản trị viên triển khai cấu hình Forwarder
* Forwarder.
Forwarder thu thập dữ liệu và gửi đến máy chủ Splunk.
Cài đặt forwarder tại nguồn dữ liệu.
![anh](https://github.com/ThanTam111/Splunk/blob/main/Image/Screenshot_10.png)

* Triển khai cơ bản cho tổ chức: 
    * Lập chỉ mục dưới 20GB mỗi ngày.
    * Với dưới 20 người dùng.
    * Số lượng Forwarder nhỏ.
## Splunk Deployment - Multi-Instance.
Tăng chỉ mục và dung lượng tìm kiếm.
Quản lý tìm kiếm và chỉ mục các chức năng được chia ra trên nhiều máy.
* Triển khai cho tổ chức. 
    * Lập chỉ mục lên đến 100GB mỗi ngày.
    * Hỗ trợ 100 người dùng.
    * Hỗ trợ hàng trăm đơn vị giao nhận.
![anh](https://github.com/ThanTam111/Splunk/blob/main/Image/Screenshot_11.png)

## Splunk Deployment - Increasing capacity.
* Tính năng thêm vào cho Search Head Cluster .
    * Dịch vụ nhiều người dùng hơn để tăng khả năng tìm kiếm.
    * Cho phép người dùng và tìm kiếm chia sẻ tài nguyên.
    * Các hoạt động phối hợp để xử lý tìm kiếm yêu cầu và phân phối  các yêu cầu trên một tập hợp các chỉ mục.
* Search Head Clusters yêu cầu tối thiếu 3 Search Heads.
* Người triển khai được sử dụng để quản lý và phân phối ứng dụng cho các thành viên của Search Head Cluster.

![anh](https://github.com/ThanTam111/Splunk/blob/main/Image/Screenshot_12.png)
## Splunk Deployment - Index Cluster.
* Cụm chỉ mục. 
    * Cấu hình để sao chép dữ liệu. 
    * Ngăn ngừa mất mát dữ liệu.
    * Thúc đẩy tính khả dụng.
    * Quản lý nhiều người lập chỉ mục.
* Cụm chỉ mục không sao chép.
    * Cung cấp quản lý đơn giản hóa.
    * Không cung cấp tính khả dụng hoặc phục hồi dữ liệu.

![anh](https://github.com/ThanTam111/Splunk/blob/main/Image/Screenshot_13.png)

