---
title : "Tạo Load Balancer"
date :  "2024-11-01" 
weight : 4 
chapter : false
pre : " <b> 4.2 </b> "
---

### Tạo Load Balancer

Ở giao diện EC2, ở bảng điều khiển bên trái

- Chọn **Load Balancers**
- Nhấn vào nút **Create Load Balancer**

![lb](/images/2.prerequisite/01-vpc.png)

Xuất hiện bảng **Compare and select load balancer type**

- Ở phần Load balancer types
  - Ở phần **Application Load Balancer**
  - Chọn **Create**

![lb2](/images/2.prerequisite/02-CreateVPC.png)

Chúng ta sẽ thấy xuất hiện bảng **Create Application Load Balancer**

- Ở phần **Basic configuration**
  - Load balancer name `FCJ-Management-LB`
  - Scheme **Internet-facing**
  - Load balancer IP address type **IPv4**

![lb3](/images/2.prerequisite/040-iamrole.png)

Ở phần Network mapping
- Chọn **VPC AutoScaling-Lab**
- Chọn Subnet **Public ap-southeast-1a**, **ap-southeast-1b**, **ap-southeast-1c**. Lưu ý chọn **public subnet**
  
  ![network](/images/2.prerequisite/040-iamrole.png)

- Ở phần Security groups
  - Security groups **FCJ-Management-SG**
- Ở phần Listeners and routing
  - Default action **FCJ-Management-TG**

![security](/images/2.prerequisite/041-iamrole.png)

- Nhấn vào nút **Create Balancer**
  
  ![create](/images/2.prerequisite/041-iamrole.png)

#### Kết quả

- Sau khi tạo Load Balancer chúng ta chọn **FCJ-Management-LB** để xem thông tin


  ![viewlb](/images/2.prerequisite/041-iamrole.png)

- Chọn **Resource map** - new để xem tổng quan liên kết của Load Balancer

  ![viewlbdetail](/images/2.prerequisite/041-iamrole.png)