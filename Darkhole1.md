Khởi chạy máy nạn nhân dark hole.
Dùng lệnh netdiscover ta quét ra được ip 192.168.152.131 khả nghi.
Dùng lệnh nmap để duyệt qua ip trên
 
Ta quét ra được 2 port là port 22 và port 80.
Có port 80 nên ta thử truy cập trang web của máy nạn nhân 
 
Có chức năng Login 
 
Tạo 1 tài khoản và đăng nhập vào.
 
Khởi chạy burp site
 
 chọn tab proxy, tắt interception, và chọn open browser.
 
Copy đường link ở mục login vào.
 
 Đăng nhập bằng tài khoản đã tạo lúc nãy.
 
Bật interception, và đổi mật khẩu.
 Ta được kết quả như sau. Nếu như lúc tạo tài khoản, chúng ta thử username admin thì nó hiện đã tạo. Nên chúng ta có thể thử thay id ở đây thành 1 rồi bấm forward. ( Hoàn tất can thiệp)
 
Chúng ta đăng nhập theo username : admin, password là 12341234 ( đã đổi ở trên)
 
Đăng nhập thành công, ta thấy có 1 chỗ để upload shell.
 
Tạo 1 file shell ở máy và copy php pentestmonkey vào.
Sau đó upload lên. Ta có 
 
Dùng lệnh nc -lvnp 8000 để đọc, và bấm php.shell5 
Bắt đầu thử tìm kiếm xung quanh
 
 
Tìm ra người dung John và secret file user.txt tuy nhiên không thể đọc được file user.
Tìm kiếm file python3 để leo quyền
 ’
Leo thang
 
sử dụng path abuse để báo cáo đặc quyền, sau đó thực thi ./toto để nhận trình bao với tư cách là John 
 
Đọc file user.txt
 
User.txt : DarkHole{You_Can_DO_It}
Đọc file password
 
Kết nối ssh với password vừa có
 
Kiểm tra quyền sudo của người dùng này, nó cho thấy rằng người dùng này có thể thực thi một tập lệnh py mà chúng tôi có thể chỉnh sửa để có shell
 
Bây giờ chúng ta phải thực thi tập lệnh py đó, để chúng ta có thể truy cập vào root shell
 
 
Cd root và tìm ra file root.txt, cat root.txt
 
Root.txt : DarkHole{You_Are_Legend}





