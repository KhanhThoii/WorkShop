---
title : "Khởi tạo EC2 Instance"
date :  "2024-11-01" 
weight : 3 
chapter : false
pre : " <b> 2.2 </b> "
---

Truy cập vào [AWS Management Console](https://aws.amazon.com/console/)

- Tìm **EC2**
- Chọn **EC2**

![ec2](/images/2.prerequisite/01-vpc.png)

Trong giao diện **EC2**
- chọn **Launch instances**  

![ec22](/images/2.prerequisite/02-CreateVPC.png)

Đặt tên cho instance, nhập `FCJ-Management`

![ec23](/images/2.prerequisite/040-iamrole.png)

Chọn như sau:

- Chọn **Quick Start**
- Chọn **Amazon Linux**
- Chọn **Amazon Linux 2023 AMI**

  ![ec24](/images/2.prerequisite/040-iamrole.png)

Chọn **Instance type:**

- Chọn **t2.micro**
- Chọn **Create new key pair**
  ![ec25](/images/2.prerequisite/041-iamrole.png)

Cấu hình key pair

- Đặt tên là `fcj-key`
- Key pair type: **RSA**
- Private key format: **.pem**
- Bấm **Create key pair**

  ![keypair](/images/2.prerequisite/041-iamrole.png)

Thực hiện cấu hình **Network**:

- Bấm vào nút **Edit**
- **VPC**, chọn VPC đã tạo.
- **Subnet**, chọn **Public subnet**
- Kiểm tra đã **Auto-assign public IP** chưa? Nếu chưa, xem lại bước cấp phát public IP ở bước tạo VPC.

  ![network](/images/2.prerequisite/041-iamrole.png)

- Chọn **Select existing security group** rồi chọn **FCJ-Management-SG**.
- Chọn **Launch instance**.

  ![sg](/images/2.prerequisite/041-iamrole.png)

Khởi tạo instance thành công.

  ![complete](/images/2.prerequisite/041-iamrole.png)

  