1.	Quét qua các ip
 
2.	Quét qua các cổng bằng lệnh nmap
 
3.	Dùng gobuster để bruteforce attack
 
Ở đây chúng ta tìm ra 192.168.1.150/files/
Truy cập vào ta được
 
4.	Tạo 1 revershell trên máy
 
 
5.	Mở fpt và upload shell lên máy nạn nhân 
 
6.	Điều hướng đến /files/web page. Chọn reversehll vừa upload

 
7.	Lấy quyền truy cập của user
 
cd /etc
cd /directory, tìm thấy file passwd
 
 
8.	Tìm user sử dụng passwd này
 
Tìm thấy user tên SHREK
9.	Chuyển tới home tìm thấy file important.txt
 
Chạy file .runme.sh
 
10.	Decode đoạn mã vừa lấy được
 
11.	Onion cx có trên file CALL.html ở /files 
 
Sử dụng mật khẩu là onion thử để login vào shrek
 
12.	Tìm ra user.txt
 

 
13.	Kiểm tra thử sudo -l
 
Leo thang 
 
Tìm ra  root.txt
 
 
