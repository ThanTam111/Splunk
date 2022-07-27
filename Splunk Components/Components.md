# 1.Các thành phần của Splunk.
Splunk gồm có 3 thành phần chính đó là :
![anh1](https://github.com/ThanTam111/Splunk/blob/main/Image/Screenshot_2.png)
# 2.Splunk Forwarder.
* Splunk Forwarder thu thập và gửi dữ liệu từ máy được cài đặt về Indexer.
* Tiêu tốn một lượng nhỏ tài nguyên trên máy cài đặt Splunk FWD.
* Forwarder là phương thức chủ yếu để đẩy log về Splunk Indexer.
![anh1](https://github.com/ThanTam111/Splunk/blob/main/Image/Screenshot_7.png)
# 3. Splunk Indexer.
* Xử lý dữ liệu, lưu trữ thành các sự kiện để hỗ trợ tìm kiếm nhanh và phân tích.
* Tổ chức phân loại các sự kiện theo thời gian (Đơn vị bucket). 
![anh1](https://github.com/ThanTam111/Splunk/blob/main/Image/Screenshot_3.png)
# 4. Splunk Search Head.
* Sử dụng SPL (Splunk Power Language) để thực hiện các truy vấn xuống dữ liệu tại Indexer.
* Điều hướng các truy vấn của người dùng tới các Indexer.
* Tổng hợp kết quả và trích xuất các trường từ sự kiện đến người dùng.
* Cung cấp một số công cụ để tạo báo cáo, biểu đồ.
![anh1](https://github.com/ThanTam111/Splunk/blob/main/Image/Screenshot_5.png)
# 5.Splunk xử lý dữ liệu 
Quá trình xử lý dữ liệu của Splunk chủ yếu có 3 giai đoạn chính đó là :
* Giai đoạn nhập dữ liệu
* Giai đoạn lưu trữ dữ liệu
* Giai đoạn tìm kiếm dữ liệu
![anh1](https://github.com/ThanTam111/Splunk/blob/main/Image/Screenshot_14.png)

**Giai đoạn nhập dữ liệu**
Trong giai đoạn này, phần mềm Splunk sử dụng luồng dữ liệu thô từ nguồn của nó, chia nó thành các khối 64K và chú thích mỗi khối bằng các khóa siêu dữ liệu. Các khóa siêu dữ liệu bao gồm tên máy chủ, nguồn và loại nguồn của dữ liệu. 
Các khóa cũng có thể bao gồm các giá trị được sử dụng nội bộ, chẳng hạn như mã hóa ký tự của luồng dữ liệu và các giá trị kiểm soát việc xử lý dữ liệu trong giai đoạn lập chỉ mục, chẳng hạn như chỉ mục mà các sự kiện sẽ được lưu trữ.

**Giai đoạn lưu trữ dữ liệu**
Lưu trữ dữ liệu bao gồm hai giai đoạn: Phân tích cú pháp và Lập chỉ mục.
* Trong giai đoạn phân tích cú pháp phần mềm Splunk kiểm tra, phân tích và biến đổi dữ liệu để chỉ trích xuất thông tin có liên quan. Đây còn được gọi là xử lý sự kiện. Chính trong giai đoạn này, phần mềm Splunk chia luồng dữ liệu thành các sự kiện riêng lẻ. Giai đoạn phân tích cú pháp có nhiều giai đoạn phụ.
    * Chia dòng dữ liệu thành các dòng riêng lẻ.
    * Xác định, phân tích cú pháp và đặt dấu thời gian.
    * Chú thích các sự kiện riêng lẻ với siêu dữ liệu được sao chép từ các khóa toàn nguồn.
    * Chuyển đổi dữ liệu sự kiện và siêu dữ liệu theo quy tắc chuyển đổi regex
* Trong giai đoạn lập chỉ mục, phần mềm Splunk ghi các sự kiện được phân tích cú pháp vào chỉ mục trên đĩa. Nó ghi cả dữ liệu thô được nén và tệp chỉ mục tương ứng. Lợi ích của lập chỉ mục là dữ liệu có thể được truy cập dễ dàng trong quá trình tìm kiếm.
**Giai đoạn tìm kiếm dữ liệu**
Giai đoạn này kiểm soát cách người dùng truy cập, xem và sử dụng dữ liệu được lập chỉ mục. Là một phần của chức năng tìm kiếm, phần mềm Splunk lưu trữ các đối tượng do người dùng tạo, chẳng hạn như báo cáo, các loại sự kiện, trang tổng quan, cảnh báo và trích xuất trường. Chức năng tìm kiếm cũng quản lý quá trình tìm kiếm.

Các giai đoạn truyền dẫn dữ liệu khác nhau mà theo đó các thành phần Splunk khác nhau nằm trong đó.
![anh1](https://github.com/ThanTam111/Splunk/blob/main/Image/Screenshot_15.png)