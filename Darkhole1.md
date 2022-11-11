Khởi chạy máy nạn nhân dark hole.
Dùng lệnh netdiscover ta quét ra được ip 192.168.152.131 khả nghi.
Dùng lệnh nmap để duyệt qua ip trên
 ![image](https://user-images.githubusercontent.com/93258260/201323276-f8afa52f-5095-4b7e-a54d-9a004fc6c79e.png)

Ta quét ra được 2 port là port 22 và port 80.
Có port 80 nên ta thử truy cập trang web của máy nạn nhân 
 ![image](https://user-images.githubusercontent.com/93258260/201323288-7beb3d41-fab4-4fa7-a7bc-6b65e4107ccf.png)

Có chức năng Login 
 ![image](https://user-images.githubusercontent.com/93258260/201323314-ead1c7e2-2237-419f-a288-7c3d354734bb.png)

Tạo 1 tài khoản và đăng nhập vào.
 ![image](https://user-images.githubusercontent.com/93258260/201323328-b987f8b0-4cb3-46fe-ba2d-715bc74ad4b3.png)

Khởi chạy burp site
 ![image](https://user-images.githubusercontent.com/93258260/201323355-7792d660-a614-42ab-ba33-81130e7016fd.png)
 ![image](https://user-images.githubusercontent.com/93258260/201323385-e40fb86b-1cdd-49b5-907d-116c9f2a562e.png)


 Chọn tab proxy, tắt interception, và chọn open browser.
 ![image](https://user-images.githubusercontent.com/93258260/201323410-84e17281-1a66-412a-bda8-03de6a7d8c75.png)

 
Copy đường link ở mục login vào.
![image](https://user-images.githubusercontent.com/93258260/201323425-0f319f5d-ba87-4050-92ad-33c0299688ba.png)
![image](https://user-images.githubusercontent.com/93258260/201323437-8c5f5e49-6366-4399-b859-6fe050c75899.png)


 
 Đăng nhập bằng tài khoản đã tạo lúc nãy.
 ![image](https://user-images.githubusercontent.com/93258260/201323463-6f5ad4fa-f548-4dd6-a78d-0888740fdd3d.png)

 
Bật interception, và đổi mật khẩu.
![image](https://user-images.githubusercontent.com/93258260/201323477-327acadb-d990-4123-91c6-ba2a49d5956b.png)

 Ta được kết quả như sau. Nếu như lúc tạo tài khoản, chúng ta thử username admin thì nó hiện đã tạo. Nên chúng ta có thể thử thay id ở đây thành 1 rồi bấm forward. ( Hoàn tất can thiệp)
 ![image](https://user-images.githubusercontent.com/93258260/201323487-ecb476e6-4540-4f33-b0eb-7b6f71f203d0.png)

 
Chúng ta đăng nhập theo username : admin, password là 12341234 ( đã đổi ở trên)
 ![image](https://user-images.githubusercontent.com/93258260/201323515-9f391c72-2afd-44e0-88d3-4fa462e43212.png)

Đăng nhập thành công, ta thấy có 1 chỗ để upload shell.
 ![image](https://user-images.githubusercontent.com/93258260/201323531-e6ee671b-41e7-490c-9fb3-eda054a07d8b.png)

Tạo 1 file shell ở máy và copy php pentestmonkey vào.
Sau đó upload lên. Ta có 
 ![image](https://user-images.githubusercontent.com/93258260/201323552-084fcf65-fdf5-42c2-814d-5379b5585765.png)

Dùng lệnh nc -lvnp 8000 để đọc, và bấm php.shell5 
![image](https://user-images.githubusercontent.com/93258260/201323573-29f41a6a-27e0-4749-b3d8-7da7e4661b8e.png)

Bắt đầu thử tìm kiếm xung quanh
 
 ![image](https://user-images.githubusercontent.com/93258260/201323588-912e775c-2f87-43b5-aa1b-fe0e45dba89c.png)
 ![image](https://user-images.githubusercontent.com/93258260/201323624-bd7b7253-6acb-4f6d-93d3-079edbcdb228.png)


Tìm ra người dung John và secret file user.txt tuy nhiên không thể đọc được file user.
Tìm kiếm file python3 để leo quyền
 ![image](https://user-images.githubusercontent.com/93258260/201323660-ce79f349-6723-49b7-bce8-816a19300862.png)

Leo thang
 ![image](https://user-images.githubusercontent.com/93258260/201323693-15fb0764-1fe4-459e-818d-7b6a66969b4d.png)

sử dụng path abuse để báo cáo đặc quyền, sau đó thực thi ./toto để nhận trình bao với tư cách là John 
 ![image](https://user-images.githubusercontent.com/93258260/201323732-ae05bc4d-4297-4423-9f18-7774003d1dbb.png)

Đọc file user.txt
 ![image](https://user-images.githubusercontent.com/93258260/201323750-a797b86b-3171-48b4-bfa3-b4252d449d60.png)

User.txt : DarkHole{You_Can_DO_It}
Đọc file password
 ![image](https://user-images.githubusercontent.com/93258260/201323763-07b1a78a-bde8-44ef-90e7-a30ad689e212.png)

Kết nối ssh với password vừa có
 ![image](https://user-images.githubusercontent.com/93258260/201323804-56374234-c639-463e-9d6c-fadb2082f3e8.png)

Kiểm tra quyền sudo của người dùng này, nó cho thấy rằng người dùng này có thể thực thi một tập lệnh py mà chúng tôi có thể chỉnh sửa để có shell
 ![image](https://user-images.githubusercontent.com/93258260/201323810-2cdd45b9-552d-491e-92df-fac3733c0423.png)

Bây giờ chúng ta phải thực thi tập lệnh py đó, để chúng ta có thể truy cập vào root shell
 ![image](https://user-images.githubusercontent.com/93258260/201323821-96f9fa00-9ffe-4055-b862-06b053418413.png)
![image](https://user-images.githubusercontent.com/93258260/201323850-988ef121-ed96-48fd-8dff-95b1443521b3.png)

 
Cd root và tìm ra file root.txt, cat root.txt
 ![image](https://user-images.githubusercontent.com/93258260/201323868-a1854694-6bff-4f67-8999-e1fa3221d607.png)

Root.txt : DarkHole{You_Are_Legend}





