---
title : "Tạo Target Group"
date :  "2024-11-01" 
weight : 3 
chapter : false
pre : " <b> 4.1 </b> "
---

### Tạo Target Group

Ở giao diện EC2, ở bảng điều khiển bên trái

- Chọn **Target Group**
- Nhấn vào nút **Create target group**

![tg](/images/2.prerequisite/01-vpc.png)

Xuất hiện bảng **Specify group details**

- Ở phần Basic configuration
  - Choose a target types **Instances**
  - Target group name `FCJ-Management-TG`

![sgd](/images/2.prerequisite/02-CreateVPC.png)

- Trong phần **Basic configuration**
  - Protocol : port **HTTP, 5000**
  - IP address **IPv4**
  - VPC **WorkShop**
  - Protocol version **HTTP1**

![bc](/images/2.prerequisite/040-iamrole.png)

- Nhấn **Next**
  
  ![next](/images/2.prerequisite/040-iamrole.png)

Tiếp theo chúng ta tiến hành **Register target**

- Ở phần Available instance

  - Chọn targer group **FCJ-Management-TG**
  - Ports for the seleced instances **5000**
  - Chọn **Include as pending below**

![rt](/images/2.prerequisite/041-iamrole.png)

- Ở phần Review targets
  - Ta sẽ thấy target group đã được đăng ký trước đó
  - Chọn **Create target group**
  
  ![create](/images/2.prerequisite/041-iamrole.png)

#### Kết quả

- Hoàn thành việc tạo Target Group, chọn Target Group **FCJ-Management-TG** vừa khởi tạo để xem thông tin.


  ![complete](/images/2.prerequisite/041-iamrole.png)


