

**I. CÁCH BẬT HYPER-V TRÊN WINDOWS 11 HOME**

  - Bước 1: tạo file enable-hyperv.bat với nội dung sau:

    ![image](https://github.com/user-attachments/assets/3395fbd3-017f-4b7f-8a59-ee08cdf2cde1)

  - Bước 2: chạy file enable-hyperv.bat dưới quyền admin

    ![image](https://github.com/user-attachments/assets/f7d4ccaf-508b-4186-b77d-55c9c56dbde0)



**II. QUY TRÌNH CÀI ĐẶT PFSENSE**

1. Tải file PfSense iso

    [Tải pfSense-CE-v2.6.0](https://github.com/hoang2514/-pfSenseDev/releases/tag/PfSense)
   
    ![image](https://github.com/user-attachments/assets/18679a27-bb0d-4067-93ca-93aa8b04a79a)

2. Cấu hình mạng -  gán interface ( Tạo các bộ chuyển mạch mới để tạo các giao diện WAN và LAN khác nhau) 
  - Bước 1: Chọn Vitural Switch Machine...

    ![image](https://github.com/user-attachments/assets/6f66ca63-7e36-476f-8110-18b96fd51cef)


  - Bước 2: Tạo 1 bộ chuyển mạch ảo mới kết nối với mạng nội bộ, cổng LAN của PfSense sẽ kết nối với switch ảo này. Đặt tên là LAN_Switch rồi apply

    ![image](https://github.com/user-attachments/assets/4b89f85e-bb65-4ebc-9916-7e8d0f25d2f2)


    

  - Bước 3: Tạo 1 switch ảo mới kết nối với mạng bên ngoài. Switch ảo này giúp PfSense kết nối với internet. Đặt tên lalf WAN_Switch, chọn mạng vật lý rồi apply

    ![image](https://github.com/user-attachments/assets/9f1c4f7b-abf6-4ba1-a0a0-8ad5af2f4b1a)
   
3. Tạo máy ảo mới, tên là PfSense_VM
  - Đổi tên thành PfSense_VM rồi nhấn next
    
    ![image](https://github.com/user-attachments/assets/94969fd7-85d6-4c17-861b-8686f4bea69e)
    
  - Ở specify generation chọn reneration 2 rồi nhấn next
    
    ![image](https://github.com/user-attachments/assets/37aabb3a-36cc-4ab7-86ad-82167eb92b98)

  - Ở Assign memory, Startup memory có thể để 2048MB rồi nhấn next

    ![image](https://github.com/user-attachments/assets/698f2155-0b31-4c3e-9f85-2e6a8dbc038e)

  - Tiếp theo là cấu hình mạng. chọn mạng WAN cho tường lửa, mạng LAN sẽ được thiết lập sau

    ![image](https://github.com/user-attachments/assets/1dadd763-b244-4c06-8426-f065ea8668b1)

  - Conect vitural hard dish có thể thiết lập thông số như sau:

    ![image](https://github.com/user-attachments/assets/da7236a0-fa2b-442e-88df-cda8d7488ca0)

  - Tiếp theo để đường dẫn file iso đã tải ở trên vào đây

    ![image](https://github.com/user-attachments/assets/72988e22-8f36-4864-83fd-b19ea62ab915)

  - Finish.

4. Setting PfSense
  - Chuột phải vào PfSense_VM chọn Settings...
  - Add Hardware -> Network Adapter -> Add

    ![image](https://github.com/user-attachments/assets/5dfea275-4a9b-4b1f-a604-4b57cb5d6d9c)

  - Ở trường Vitural switch chọn LAN_Switch -> Apply

    ![image](https://github.com/user-attachments/assets/e4f8bfaf-8d8e-456e-9d5f-54e1d05751de)

  - Ở Firmware Move up Hard ware lên đầu-> apply

    ![image](https://github.com/user-attachments/assets/54458a77-7260-4a8b-971e-2ecb8f3eafaa)
    ![image](https://github.com/user-attachments/assets/86a4cb39-812a-4da0-b757-1786a4e46d57)
    
  - Vào mục Security bỏ chọn Enable Secure Boot rồi apply

    ![image](https://github.com/user-attachments/assets/eece2f27-c5db-4169-889d-1cce906415fe)

  - OK và kết thúc.


**III. CẤU HÌNH PFSENSE**
1. Cấu hình mạng - gán IP tĩnh cho mạng LAN
  - Khởi động pfsense lần đầu tiên và cấu hình ip tĩnh cho mạng LAN (192.168.1.1/24)

    ![image](https://github.com/user-attachments/assets/807cf193-79cf-478c-b002-fb28641532f6)

2. Truy cập giao diện quản trị (Web GUI) của PfSense
  - Mở trình duyệt truy cập 192.168.1.1 để vào giao diện quản trị

    ![image](https://github.com/user-attachments/assets/10cbdcdc-09f7-486a-9dac-6e91f26e5d33)

  - đăng nhập với usename mặc định là admin password mặc định là pfsense

    ![image](https://github.com/user-attachments/assets/a9ff334d-0bfb-4663-b26c-bdc36710f844)

  - Sau khi đăng nhập sẽ có giao diện như sau:

    ![image](https://github.com/user-attachments/assets/8284fbc9-f634-4ba6-a0f4-026801259263)

  - Nhấn next 2 lần rồi thiết lập các thông số như sau:

    ![image](https://github.com/user-attachments/assets/7c2420ce-dc69-43f5-a838-b8d223230d94)

  - Tiếp theo là thiết lập múi giờ

    ![image](https://github.com/user-attachments/assets/341f9b4f-c60d-4a56-9435-1e1ff4d8d30a)

  - Sau đó thiết lập mạng WAN (DHCP)

    ![image](https://github.com/user-attachments/assets/e901474d-64a6-4b1e-8a69-3352236e6d83)
    
  - Tiếp theo sẽ thay đổi địa chỉ mạng LAN của tường lửa để tránh xung đột

    ![image](https://github.com/user-attachments/assets/8581ae61-8106-4518-8ca1-a8099cf0da86)

  - Tiếp theo là set admin password

    ![image](https://github.com/user-attachments/assets/acdaa801-2dd6-495d-9d80-98fe65f59e74)

  - LAN mới có địa chỉ là 10.20.20.1

    ![image](https://github.com/user-attachments/assets/c3fd480e-bfe3-4e22-84fa-f525b73e8280)

3. Dựng máy chủ web và đưa vào vùng DMZ, được PfSense bảo vệ

   - Tạo switch ảo cho DMZ
     
       - Bước 1 chọn Virtual Switch Manager…
       
         ![image](https://github.com/user-attachments/assets/458304dc-0983-4b2b-8309-f5a441a250f8)
 
       -  Bước 2 tạo Switch mới: chọn  “New virtual network switch” rồi chọn loại Internal rồi Create  Virtual Switch
       
          ![image](https://github.com/user-attachments/assets/d3783197-6da2-47f2-bc54-dffb7912a166)
          
       -  Bước 3: Cấu hình Switch: name DMZ_Switch -> Type chọn Internal -> Apply -> Ok
    
          ![image](https://github.com/user-attachments/assets/472b5e80-fad2-4c8e-8b08-092d6b69d6d4)
    
   -  Thêm một card mạng cho pfSense gán vào DMZ
       -  Chuột phải vào máy pfSense VM -> Settings -> Add Hardware -> Network Adapter -> Add -> Gán vào Virtual Switch: chọn DMZ_Switch -> Apply -> OK
    
          ![image](https://github.com/user-attachments/assets/7b6d0670-3da9-4980-a1dd-3f2cc08a6afa)
    
   -   Khởi động pfSense -> gán interface DMZ
       -   Chọn option 1
    
          ![image](https://github.com/user-attachments/assets/942d2b67-5c1d-4df5-b5b7-e9d62405c164)
    
       -   khi được hỏi là Should VLANs be set up now gõ n
       -   rồi gõ lần lượt hn0 hn1 hn2
       -   cuối cùng nếu hỏi là Do you want to proceed gõ y
    
          ![image](https://github.com/user-attachments/assets/fa74900d-ad59-418e-a64c-a60c394fd4a4)
   -   Cấp IP interface DMZ
       -   Ở màn hình menu chính pfSense chọn option 2 rồi enter
       -   Gõ số tương ứng với OPT1 rồi nhấn Enter
    
          ![image](https://github.com/user-attachments/assets/098695aa-ae69-45ec-8e23-e77c75e5e5d7)
       -   pfSense hỏi: Enter the new LAN IPv4 address: 192.168.100.1 rồi nhấn Enter
       -   rồi sau đó làm theo ảnh sau
    
         ![image](https://github.com/user-attachments/assets/6294efa3-0eb6-4020-b57d-24590cd2f45e)
   -  Cấu hình máy chủ Web Apache2 bằng Docker  








     



  



    







