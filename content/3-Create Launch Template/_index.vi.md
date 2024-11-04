---
title : "Tạo Launch Template"
date :  "2024-11-01" 
weight : 3 
chapter : false
pre : " <b> 3. </b> "
---
### AMIs và Launch Template

AMIs (Amazon Machine Images) lưu giữ các thông tin quan trọng như hệ điều hành, ứng dụng và cấu hình của một EC2. Khi tạo AMI, bạn đảm bảo rằng mỗi máy chủ mới được khởi tạo sẽ có cùng cấu hình và sẵn sàng hoạt động ngay lập tức.

Launch Template là công cụ dùng để định cấu hình cho các phiên bản EC2 mới, bao gồm việc chọn AMI, loại instance, cấu hình mạng và tùy chọn bảo mật. Khi cần khởi tạo một hoặc nhiều máy chủ với cấu hình giống nhau, chỉ cần sử dụng Launch Template đã được thiết lập sẵn để triển khai một cách dễ dàng và nhanh chóng.

### Thiết lập Launch Templates
#### Tạo Amazon Machine Images (AMIs) từ EC2

Ở trong phần giao diện quản lý **EC2**, ở bảng chọn bên phải

- Chọn **Instances**
- Chọn **FCJ-Management** instance
- Chọn **Actions**
- Chọn **Image and templates**
- Ấn **Create image**

    ![createpolicy](/images/2.prerequisite/041-iamrole.png)

Trong bảng cấu hình cho **Create AMI**, chúng ta tiến hành điền các thông tin sau

- **Image name** `FCJ-Management-AMI`
- **Image description** `AMI for FCJ-Management`
- Ấn **Create Image**

    ![createpolicy](/images/2.prerequisite/041-iamrole.png)

Sau khi tạo AMI chúng ta sẽ kiểm tra AMI vừa tạo

- Chọn **AMIs** chúng ta sẽ thấy AMI vừa tạo được
- Chọn **FCJ-Management-AMI**

    ![createpolicy](/images/2.prerequisite/041-iamrole.png)

    ![createpolicy](/images/2.prerequisite/041-iamrole.png)

### Tạo Launch Templates
Ở giao diện quản lý EC2, ở bảng chọn bên phải

- Chọn **Launch Templates**
- Chọn Create launch template
    ![createpolicy](/images/2.prerequisite/041-iamrole.png)

Ở trong bảng **Create launch template** hãy điền các thông tin sau

- Ở phần **Launch template name and description**
  - **Launch template name** `FCJ-Management-template`
  - **Template version description** `Template for FCJ Management`

    ![createpolicy](/images/2.prerequisite/041-iamrole.png)

- Ở phần **Application and OS Image (Amazon Machine Image)**
  - Chọn **My AMIs**
  - Chọn **Owned by me**
  - Chọn loại **Amazon Machine Image (AMI)**, chọn AMI đã tạo **FCJ-Management-AMI**


    ![createpolicy](/images/2.prerequisite/041-iamrole.png)

- Ở phần **Instance type**
    - Chọn loại **Instance t2.micro**
- Ở phần Key pair (logic)
    - Chọn Key pair name có tên là **fcj-key**
  
  ![createpolicy](/images/2.prerequisite/041-iamrole.png)

- **Network settings**
    - Chọn subnet public AutoScaling-Lab-public-ap-southeast-1a
    - Chọn Select existing security group
    - Chọn security group FCJ-Management-SG
    - Cuối cùng, chọn Create launch template
  
  ![createpolicy](/images/2.prerequisite/041-iamrole.png)

### Kết quả
Kiểm tra Launch Template vừa tạo

- Chọn **FCJ-Management-template**

    ![createpolicy](/images/2.prerequisite/041-iamrole.png)

- Xem lại cấu hình Launch Template chúng ta đã tạo

    ![createpolicy](/images/2.prerequisite/041-iamrole.png)
    
Hoàn thành tạo Launch Template.