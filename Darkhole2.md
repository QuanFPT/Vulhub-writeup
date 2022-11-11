1.	Dò tìm ip và các port mở
 
Tìm ra được ip 192.168.152.132 có mở port 22 và port 80
2.	Truy cập vào http://192.168.152.132
 
3.	Dùng gosbuster để brute-force 
 
4.	Sử dụng gitdumper để nhận git repo từ trang web để nắm bắt tốt hơn về tập dữ liệu
 
 
 
5.	Kiểm tra config vì ở đó thường lưu trữ password
 
6.	Copy commit để xem có gì thay đổi
 
Chúng ta tìm thấy 1 username và password bị xoá
7.	Sử dụng username và password mới tim thấy để login
 
8.	Dùng SQLMap để exploit web
 
Vào phần storage và copy value. Kiểm tra xem web này có bị SQL injection không.
 
 
	
Kết nối vào database darkhole_2
 
 
 
Chúng ta tìm ra được user jehad với pass là fool
9.	Kết nối với máy jehad
 

 
Chúng ta tìm ra thêm 2 user nữa là lama và losy
 
Tìm ra user.txt ở losy
10.	Đọc được file user.txt
 
DarkHole{‘This_is_the_life_man_better_than_a_cruise’}
11.	Xem ở Lama có gì
 
12.	Upload file linpeas.sh lên máy nạn nhân
 
 
 
13.	Quay về losy và đọc crontab
 
Chúng ta tìm ra được 1 web đang chạy trên port 9999
14.	Kết nối tới /otp/web/index.php
 
15.	Dùng netsta để có thêm thông tin
 



