---
title : "Thiết lập hạ tầng mạng"
date :  "2024-11-01" 
weight : 2 
chapter : false
pre : " <b> 2.1 </b> "
---

### Tạo VPC

Truy cập vào [AWS Management Console](https://aws.amazon.com/console/)

- Tìm **VPC**
- Chọn **VPC**

![VPC](/images/2.prerequisite/01-vpc.png)

Trong giao diện **VPC**
- chọn **Create VPC**  

![VPC2](/images/2.prerequisite/02-CreateVPC.png)

Trong giao diện **Create VPC**

- Chọn **VPC and more**
- **Name**, nhập tên VPC của bạn. Trong bài lab này, ta đặt tên là `WorkShop`
- **IPv4 CIDR block**, nhập `10.0.0.0/16`

![VPC3](/images/2.prerequisite/040-iamrole.png)

Chọn như sau:

- Số lượng AZ là **3**
- Số lượng public subnet là **3**
- Số lượng private subnet là **3**
- Nat gateways chọn **None**
  
  ![VPC4](/images/2.prerequisite/040-iamrole.png)

- VPC endpoints chọn **None**
- Chọn **Create VPC**

![VPC5](/images/2.prerequisite/041-iamrole.png)

### Thực hiện cấp phát IP public.

Thực hiện cấp phát IP public.

- Chọn **Subnets**
- Chọn **public subnet**
- Chọn **Edit subnet settings**
  
  ![ip1](/images/2.prerequisite/041-iamrole.png)

Chọn **Enable auto-assign public IPv4 address**. Sau đó Chọn **Save**

  ![ip2](/images/2.prerequisite/041-iamrole.png)

Kiểm tra đã cấp phát thành công.

  ![ip4](/images/2.prerequisite/041-iamrole.png)

Thực hiện cấp phát cho Public subnet còn lại (làm tương tự). Tiếp theo chúng ta sẽ tạo Security group cho ứng dụng.

- Trong giao diện VPC, chọn **Security groups**
- Chọn **Create security group**

  ![sg1](/images/2.prerequisite/041-iamrole.png)

  Thực hiện cấu hình **Security Group**

- **Security group name**, nhập `FCJ-Management-SG`
- **Description**, nhập `Security Group for FCJ Management`
- **VPC**, thì chọn VPC vừa tạo: `WorkShop`

  ![sg2](/images/2.prerequisite/041-iamrole.png)

Cấu hình **Inbound rules**

- Đầu tiên phải cấu hình **SSH** port 22 và **Source: MyIP** để có thể truy cập vào instance.
- Tiếp theo là **HTTP** port 80.
- **Custom TCP** port `5000` dành cho **FCJ Management**
- **HTTPS** port 443.

  ![ibr](/images/2.prerequisite/041-iamrole.png)

Kiểm tra **Outbound rules** và chọn **Create security group**

  ![obr](/images/2.prerequisite/041-iamrole.png)

## Tạo Security group cho Database instance

Chúng ta tạo Security group cho Database instance. Để đảm bảo bảo mật nên không cấu hình chung Security group của ứng dụng. Cấu hình **security group**

- **Security Group name**, nhập `FCJ-Management-DB-SG`
- **Description**, nhập `Security Group for DB instance`
- Chọn vpc vừa tạo

### Cấu hình **Inbound rules**

- Chọn **Add rule**
- Chọn **MYSQL/Aurora** port 3306
- Sau đó chọn Source là **FCJ-Management-SG**

  ![ibr2](/images/2.prerequisite/041-iamrole.png)

Kiểm tra lại Outbound rules và cuối cùng bấm Create security group

  ![obr2](/images/2.prerequisite/041-iamrole.png)



