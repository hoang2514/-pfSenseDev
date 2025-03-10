**I. CÁCH BẬT HYPER-V TRÊN WINDOWS 11 HOME**

  - Bước 1: tạo file enable-hyperv.bat với nội dung sau:

    ![image](https://github.com/user-attachments/assets/3395fbd3-017f-4b7f-8a59-ee08cdf2cde1)

  - Bước 2: chạy file enable-hyperv.bat dưới quyền admin

    ![image](https://github.com/user-attachments/assets/f7d4ccaf-508b-4186-b77d-55c9c56dbde0)



**II.QUY TRÌNH CÀI ĐẶT PFSENSE**

1. Tải file PfSense iso

    ![image](https://github.com/user-attachments/assets/18679a27-bb0d-4067-93ca-93aa8b04a79a)

2. Cấu hình mạng( Tạo các bộ chuyển mạch mới để tạo các giao diện WAN và LAN khác nhau) 
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

  - Ở Assign memory, Startup memory để 2048MB rồi nhấn next

    ![image](https://github.com/user-attachments/assets/698f2155-0b31-4c3e-9f85-2e6a8dbc038e)

  - Tiếp theo là cấu hình mạng. chọn mạng WAN cho tường lửa, mạng LAN sẽ được thiết lập sau

    ![image](https://github.com/user-attachments/assets/1dadd763-b244-4c06-8426-f065ea8668b1)

  - Conect vitural hard dish thiết lập thông số như sau:

    ![image](https://github.com/user-attachments/assets/da7236a0-fa2b-442e-88df-cda8d7488ca0)

  - Tiếp theo để đường dẫn file iso đã tải ở trên vào đây

    ![image](https://github.com/user-attachments/assets/72988e22-8f36-4864-83fd-b19ea62ab915)

  - Finish.





