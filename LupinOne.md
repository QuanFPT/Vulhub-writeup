LupinOne 
Name : Tran Le Anh Quan
Step 1: Dùng lệnh nmap để tìm kiếm các port
nmap -sC -sV -A 192.168.150.130
 
Step 2:  Có cổng 80 mở, truy cập vào đường link 192.168.150.130
 
Step 3 : duyệt qua trang web trên bằng lệnh 
dirb http:// 192.168.152.130/
 
Trong đó chúng ta có thể đọc  trang như là robot.txt
 
Nhưng khi tìm kiếm với đường link ~myfiles thì lại ra lỗi 404 
 
Nên chúng ta có thể giả định là có 1 directory  nào đó bắt đầu bằng ~ .

 
Tiếp theo sử dụng tool FFuF để tìm các file có bắt đầu ~. Qua đó ta tìm đc file secret
ffuf -u http://192.168.1.15/~FUZZ -w /usr/share/wordlists/dirbuster/directory-list-2.3-small.txt -e .php,.txt -fc 403
Truy cập vào trang web thì ta được :

 
Đọc trang trên, chúng ta có 1 số thông tin như là ssh private key file được dấu ở đâu đó, và cái directory này được share cho người bạn thân nhất.
Chúng ta tiếp tục dung ffuf để scan thêm 1 lượt nữa với từ khoá dungf là secret
ffuf -u http://192.168.152.130/~secret/.FUZZ -w /usr/share/wordlists/dirbuster/directory-list-2.3-small.txt -e .php,.txt -fc 403
chúng ta thêm /. Để hiện lên các folder ẩn.
 
Kết quả sau khi scan là mysecret.txt. Đọc file này ta được hình như sau
 
Có thể thấy được đây là mã ssh đã được mã hoá. Chúng ta dung lệnh wget để down file này về máy.
 
Wget http://192.168.152.130/~secret/.mysecret.txt
Lên web decrypt file mysecret ta được 
 
Tạo 1 file key.txt để chứa key 
 
Chúng ta thử kết nối vào máy lupinOne nhưng mà cần mật khẩu
 
Sử dụng johntheripper để crack file ssh_key.rsa
 
 
Password P@55w0rd!
 
Kết nối vào lupinOne

 
Đọc file user.txt 
Flag : 3mp!r3{I_See_That_You_Manage_To_Get_My_Bunny}
Chạy lệnh cat /etc/issue để biết check thông tin chi tiết về hệ điều hành
Chạy lệnh uname -a để check phiên bản kernel của target machine
Sudo -l để check permission của icex64.
L= 
Chúng ta có thể đọc được file scrypt python của 1 user khác. Đọc content của file đó
 
Mở port 80 trên máy rồi chuyển linpeas.sh qua máy victim
 
 
 
Chúng ta tìm ra được file python3.9/webbroswer.py
Edit lại file này, thêm dòng os.system ("/bin/bash")
 
Thực thi file heist.py thì ta đổi qua được user arsene
 
Dungf lệnh sudo -l ta được
 
Dung Gtfobin tìm pip shell để chuyển qua root
 
 
 
