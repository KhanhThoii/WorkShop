---
title : "Cài đặt dữ liệu cho Database"
date :  "2024-11-01" 
weight : 5 
chapter : false
pre : " <b> 2.4 </b> "
---

Lấy **Public IP address** của EC2 instance

![role](/images/2.prerequisite/01-vpc.png)

Sử dụng **MobaXterm** để kết nối SSH vào instance qua port 22.

- Chọn **Session**
- Chọn **SSH**
- **Remote host**, nhập **Public IPv4 address** mới lấy của instance
- **Specify username**, nhập `ec2-user`
- Kiểm tra port 22
- Chọn **Advanced SSH settings**
- Chọn **Use private key** và chọn **keypair** của instance.
- Chọn **OK**

![role1](/images/2.prerequisite/02-CreateVPC.png)

SSH thành công

![role1](/images/2.prerequisite/040-iamrole.png)

Vì chúng ta sử dụng git để clone source code. Trước tiên, cài đặt git bằng lệnh sau:

  ```bash
    sudo yum install git
  ```
  ![role1](/images/2.prerequisite/040-iamrole.png)

Cài đặt MySQL command-line client

   ```bash
    sudo dnf install mariadb105
   ```

  ![createpolicy](/images/2.prerequisite/041-iamrole.png)

Kiểm tra cài đặt git

  ```bash
    mysql --version
  ```
  
  ![createpolicy](/images/2.prerequisite/041-iamrole.png)

Kết nối MySQL command-line client (unencrypted)

- Đối với tham số -h, hãy thay thế DNS name (endpoint) cho DB instance, bạn có thể lấy DNS name ở trong console chi tiết của RDS bạn đã tạo - Đối với tham số -P, hãy thay thế port cho DB instance. (3306)
- Đối với tham số -u, thay bằng master user lúc bạn tạo RDS
- Sau khi chạy lệnh thì nhập vào master user password mà bạn đã đặt khi tạo RDS

    ```bash
    sửa ở đây nha
  ```

  ![createpolicy](/images/2.prerequisite/041-iamrole.png)

Tiến hành kiểm tra các database trong instance bằng lệnh sau sẽ in ra danh sách tất cả các cơ sở dữ liệu.

  ```bash
    show databases;
  ```

  ![createpolicy](/images/2.prerequisite/041-iamrole.png)

Chọn cơ sở dữ liệu để thực hiện các thay đổi đối với nó bằng cách sử dụng USE, hãy dùng initial database lúc bạn tạo RDS.

  ```bash
    USE "tên database";
  ```

  ![createpolicy](/images/2.prerequisite/041-iamrole.png)

Thực hiện tạo bảng trong database awsuser bằng lệnh **CREATE TABLE**.
  ```bash
    tạo table ở đây nha
  ```

  ![createpolicy](/images/2.prerequisite/041-iamrole.png)

Chèn thông tin vào trong bảng dữ liệu bằng lệnh **INSERT INTO**

  ```bash
    insert ở đây nha
  ```

  ![createpolicy](/images/2.prerequisite/041-iamrole.png)

Hiển thị các bảng:

  ```bash
    SELECT * FROM "tên bảng";
  ```

  ![createpolicy](/images/2.prerequisite/041-iamrole.png)

Sử dụng **exit** đề rời khỏi. Nếu không thể ngắt kết nối với DB instance



