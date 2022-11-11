1.	Netdiscover và nmap ip vừa tìm ra
 
 
2.	Check port 8080
 
3.	Đăng nhập bằng Guest
 
4.	Bruteforce attack
 
 
5.	Dùng hydra để bruteforce user
 
Tìm ra Magellan và venus
6.	Dùng burpsite để can thiệp và bẻ khoá mật khẩu
 
 
Đoạn code lạ nhận được từ base64 decoding đã được mã hoá bởi ROT13

 
Thử nếu điều này cũng hoạt động với Venus và magella. Chúng ta có thể sử dụng lại Set-Cookie form, nhưng thay nó thành Venus
 
 
Nó đúng với Venus, Thử với Magellan
 
 
 
7.	Login với user Magellan
 
 
 
Có flag đầu tiên [user_flag_e799a60032068b27b8ff212b57c200b0]
8.	Kiểm tra sudo -l
 
9.	Dùng lệnh find để kiểm tra coi có cái nào có thể dung để leo thang đặc quyền không
 

Có 1 file lạ là polkit-agent-helper-1
 

 
10.	Mở port 4444 trên máy mình
 
 
Unzip file vừa lấy
 
Dùng lệnh make để pwn chương trình. Tiếp theo chúng ta có cve-2021-4034 và 1 số phần khác. 
 
11.	Chạy cve-2021-4043 để lấy shell, dung lệnh export TERM=xterm để cài đặt môi trường thuận tiện .
 
 
 
Ta có được root_flag : [root_flag_83588a17919eba10e20aad15081346af]


