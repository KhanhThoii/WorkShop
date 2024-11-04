---
title : "Khởi tạo Database Instance với RDS"
date :  "2024-11-01" 
weight : 4 
chapter : false
pre : " <b> 2.3 </b> "
---

## Tạo Subnet group cho Database instance

Truy cập vào [AWS Management Console](https://aws.amazon.com/console/)

- Tìm **RDS**
- Chọn **RDS**

![rds1](/images/2.prerequisite/01-vpc.png)

- Chọn **Subnet groups**
- Chọn **Create DB subnet group**
  
![rds2](/images/2.prerequisite/02-CreateVPC.png)

Trong giao diện **Create DB subnet group**

- **Name**, nhập `FCJ-Management-Subnet-Group`
- **Description**, nhập `Subnet Group for FCJ Management`
- Chọn VPC đã tạo.

![dbsbg](/images/2.prerequisite/040-iamrole.png)

Cấu hình subnet

- Chọn các **AZ**
- Chọn các **Private subnet**

  ![dbsbg2](/images/2.prerequisite/040-iamrole.png)

Chọn **Create**

![create](/images/2.prerequisite/041-iamrole.png)

Hoàn thành tạo DB Subnet Group với 2 AZ
 
  ![complete](/images/2.prerequisite/041-iamrole.png)

  ![complete2](/images/2.prerequisite/041-iamrole.png)

## Tạo Database instance 

Truy cập vào **RDS AWS Management Console**

- Chọn **Databases**
- Chọn **Create database**

  ![db](/images/2.prerequisite/041-iamrole.png)

Chọn phương thức tạo **Databases** như sau:

- Chọn **Standard create**

  ![db2](/images/2.prerequisite/041-iamrole.png)

- **Engine** database chọn **MySQL**

  ![engine](/images/2.prerequisite/041-iamrole.png)

**Template**

- Chọn **Production**
- Chọn **Mutil-AZ DB instance**

  ![production](/images/2.prerequisite/041-iamrole.png)

Thực hiện cài đặt chi tiết

- **DB instance identifier**, nhập `fcj-management-db-instance`
- **Master username**, nhập `admin`
- Chọn sang **Self managed**

  ![db3](/images/2.prerequisite/041-iamrole.png)

 **Master password**, nhập tùy ý của bạn (nhập `06022003Min*`) - Confirm password, nhập lại password 1 lần nữa

  ![pass](/images/2.prerequisite/041-iamrole.png)

Cấu hình chi tiết cho instace

Chọn `db.m5d.large`
Chọn `General Purpose SSD (gp3)`
Allocated storage nhập vào `20`

  ![instance](/images/2.prerequisite/041-iamrole.png)

**Connectivity** cho db instance

- Chọn **Don’t connect to an EC2 compute resouce**
- VPC, chọn `WorkShop` đã tạo
- **Subnet group**, chọn subnet group đã tạo.

  ![db4](/images/2.prerequisite/041-iamrole.png)

- **VPC security group**, Chọn **Choose existing**
- **Security Group**, chọn **FCJ-Management-DB-SG**

  ![db5](/images/2.prerequisite/041-iamrole.png)

Khởi tạo Initial Database với tên `awsfcjuser`, còn lại để mặc định.

  ![createpolicy](/images/2.prerequisite/041-iamrole.png)

Chọn **Create database**

  ![createpolicy](/images/2.prerequisite/041-iamrole.png)

Chờ một vài phút để Database instance được khởi tạo

  ![createpolicy](/images/2.prerequisite/041-iamrole.png)

Chúng ta có được **Endpoint** và **Port** như dưới đây.

  ![createpolicy](/images/2.prerequisite/041-iamrole.png)