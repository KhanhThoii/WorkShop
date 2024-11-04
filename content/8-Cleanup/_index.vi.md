---
title : "Dọn dẹp tài nguyên"
date :  "2024-11-01" 
weight : 8 
chapter : false
pre : " <b> 8. </b> "
---
### Dọn dẹp tài nguyên 

Sau khi thực hành xong bài workshop chúng ta tiến hành bước dọn dẹp tài nguyên

#### Xóa Auto Scaling Group 

Ở giao diện quản lý **EC2**, ở thanh điều hướng bên trái, lướt xuống và chọn **Auto Scaling Groups**

- Chọn Auto Scaling Groups **FCJ-Management-ASG**
- Nhấn vào nút **Actions** ở góc trên bên phải màn hình
- Chọn **Delete**

    ![clear1](/images/2.prerequisite/041-iamrole.png)

#### Xóa Load Balancer:

Ở giao diện quản lý EC2, ở thanh điều hướng bên trái, lướt xuống và chọn **Load Balancer**

- Chọn Load Balancer **FCJ-Management-LB**
- Nhấn vào nút **Actions** ở góc trên bên phải màn hình
- Chọn **Delete load balancer**

    ![clear2](/images/2.prerequisite/041-iamrole.png)

#### Xóa Target Group:

Ở giao diện quản lý EC2, ở thanh điều hướng bên trái, lướt xuống và chọn **Target Group**

- Chọn Target Group **FCJ-Management-TG**
- Nhấn vào nút **Actions** ở góc trên bên phải màn hình
- Chọn **Delete**

    ![clear3](/images/2.prerequisite/041-iamrole.png)

#### Xóa Launch Template:

Ở giao diện quản lý **EC2**, ở thanh điều hướng bên trái, lướt xuống và chọn **Launch Templates**

- Chọn Launch Templates **CJ-Management-TG**
- Nhấn vào nút **Actions** ở góc trên bên phải màn hình
- Chọn **Delete template**

    ![clear4](/images/2.prerequisite/041-iamrole.png)

#### Xóa AMI:

Ở giao diện quản lý **EC2**, ở thanh điều hướng bên trái, lướt xuống và chọn **AMIs**

- Chọn AMI **FCJ-Management-AMI**
- Nhấn vào nút **Actions** ở góc trên bên phải màn hình
- Chọn **Deregister AMI**

    ![clear5](/images/2.prerequisite/041-iamrole.png)

#### Terminate EC2 instance

Ở giao diện quản lý **EC2**, ở thanh điều hướng bên trái, chọn **Instance**

- Chọn **FCJ-Management** instance
- Nhấn vào nút **Instance state** ở góc trên bên phải màn hình
- Chọn **Terminate (delete) instance**

    ![clear6](/images/2.prerequisite/041-iamrole.png)

#### Xóa RDS Database

- Truy cập **RDS**
- Trên thanh điều hướng bên trái, chọn **Databases** instance
- Chọn database instance **fcj-management-db-instance** liên quan tới bài lab.
- Nhấn vào **Modify**.

    ![clear7](/images/2.prerequisite/041-iamrole.png)

## Modify DB Instance

Ở phần **Modify DB Instance**, chúng ta kéo xuống dưới cùng

- Nhấp bỏ **Enable deletion protection**
- Nhấn **Continue**

    ![clear8](/images/2.prerequisite/041-iamrole.png)

## Schedule Modifications

Tiếp tục ở phần **Schedule modifications**

- Chọn **Apply immediately**
- Nhấn **Modify DB instance**

    ![clear8](/images/2.prerequisite/041-iamrole.png)

## Xóa DB instance

- Chọn database instance **fcj-management-db-instance**
- Nhấn vào nút **Actions** ở góc trên bên phải màn hình
- Chọn **Delete**

    ![clear9](/images/2.prerequisite/041-iamrole.png)   

- Chọn **I acknowledge that upon instance deletion, automated, including system snapshots and point-in-time recovery, will no longer be available**
- Điền **delete me**
- Nhấn **Delete**

    ![clear10](/images/2.prerequisite/041-iamrole.png)

#### Xóa Subnet Group

- Chọn **Subnet groups**
- Chọn subnet group **fcj-management-subnet-group**
- Chọn **Delete**
  
  ![clear11](/images/2.prerequisite/041-iamrole.png)

