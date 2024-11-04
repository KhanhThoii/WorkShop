---
title : "Tạo Auto Scaling Group"
date :  "2024-11-01" 
weight : 6 
chapter : false
pre : " <b> 6. </b> "
---
### Vấn đề ở phần trước


Như ta đã kiểm thử ở phần trước thì website của chúng ta đã hoạt động bình thường với một số lượt request tới sẽ ra sao nếu chúng ta gửi rất rất nhiều lượt request cùng một lúc, lúc đó website cuar chúng ta sẽ không còn hoạt động ổn định được nữa và giải pháp là chúng ta sẽ phải tăng thêm nhiều EC2 Instance ở trong hệ thống và nhờ vào Load Balancer để chia sẻ các yêu cầu từ phía người dùng.

Tuy nhiên chúng ta cứ ngồi canh và thêm các máy chủ EC2 thì không được hợp lý bởi vì để khởi tạo một EC2 Instance, thì mình cần phải có được cái “lõi” ở bên trong, chính là ứng dụng đang đảm nhận nhiệm vụ xử lý các yêu cầu đó và cùng với các thư viện khác.


### Thiết lập Auto Scaling Group

#### Thiết lập Launch template
Ở trong giao diện quản lý của EC2, kéo bảng lựa chọn ở bên trái xuống cuối cùng.

- Chọn **Auto Scaling Groups**.
- Ấn **Create Auto Scaling group**.

    ![asg](/images/2.prerequisite/041-iamrole.png)

Ở trong giao diện tạo **Auto Scaling group**, chúng ta sẽ điền các thông tin sau

- Name: `FCJ-Management-ASG`
- Trong **Launch template**:
  - Launch template: chọn `FCJ-Management-template` (có thể là bất kỳ cái tên nào).
  - Version: **Default (1)** theo như lựa chọn mặc định.
  
  ![asg2](/images/2.prerequisite/041-iamrole.png)

{{% notice note %}}
Lưu ý là tên của ASG bạn nên đặt đúng với tên của ASG mà được đặt ở trong phần 2.6 trước đó, bước chuẩn bị dữ liệu cho Predictive Scaling.
{{% /notice %}}

{{% notice note %}}
Launch template được chọn cho ASG phải là template mà được cài đặt đầy đủ MySQL Client, Node, Source Code và PM2 thì mới đảm bảo các Target hoạt động bình thường, nếu như bạn làm theo các bướcr trong phần 2 và phần 3 thì bạn đã làm đúng.
{{% /notice %}}

![notical](/images/2.prerequisite/041-iamrole.png)

#### Thiết lập mạng

Ở trong phần Network, chọn các thông tin như sau:

- VPC: chọn VPC **WorkShop**, VPC mà chúng ta đã tạo ở đầu bài.
- Availability Zones and subnets: chọn 3 **public subnets** mà chúng ta đã tạo.
- Ấn **Next**.

![network](/images/2.prerequisite/041-iamrole.png)

#### Thiết lập Load Balancer và một số thứ khác

Ở buớc 4 thì chúng ta đã có tạo **Application Load Balancer** và tạo một **Target Group** và gắn vào trong bộ cân bằng tải đó. Nên giờ chúng ta sẽ chọn một số lựa chọn như sau:

- Load balancing: chọn **Attach to an existing load balancer**.
- Attach to an existing load balancer: chọn **Choose from your load balancer target group**
- Existing load balancer target group: chọn **FCJ-Management-TG | HTTP**.

![lb](/images/2.prerequisite/041-iamrole.png)

{{% notice note %}}
Khi cấu hình đúng Target Group và Application Load Balancer, thì ở lựa chọn Existing load balancer target group chúng ta có thể thấy được Target Group đó được liệt kê, nghĩa là cả ALB và TG đều tồn tại.
{{% /notice %}}

Trong phần VPC Lattice integration options: chọn **No VPC Lattice service**, trong bài này thì chúng ta không cấu hình phần này.

Tiếp theo là Health checks, chúng ta sẽ chọn (tích) **Turn on Elastic Load Balancing health checks**. Để các thiết lập còn lại theo mặc định.

![vpc](/images/2.prerequisite/041-iamrole.png)

**Additional settings**, ở phần Monitoring:

- Chọn (tích) **Enable group metrics collection within CloudWatch**.
- Ấn **Next**.

    ![AS](/images/2.prerequisite/041-iamrole.png)  

#### Thiết lập Size và Scaling cho Group
Ở trong phần này thì mình sẽ xác định các hành vi mở rộng của Group và số lượng các Instance sẽ được khởi tạo trong quá trình Scale, bao gồm Scale out (mở rộng) và Scale in (thu hẹp).

- Trong phần Group size:
    - Desired capacity: 1
- Trong phần Scaling:
    - Scaling limits:
        - Min desired capacity: 1
        - Max desired capacity: 3 (tùy thuộc vào số lượng máy chủ bạn muốn)
  
  ![size](/images/2.prerequisite/041-iamrole.png)

Trong Automatic scaling - optional: chọn **No scaling policies**, tạm thời làm mình sẽ không thiết lập chính sách scaling cho ASG.

![as](/images/2.prerequisite/041-iamrole.png)

Trong Instance maintenace policy: chọn **No policy**, sau đó ấn **next**.

![policy](/images/2.prerequisite/041-iamrole.png)

#### Thiết lập thông báo

Chúng ta sẽ thiết lập thông báo tới email (dùng Amazon SNS) khi mà ASG:

- Khởi tạo một Instance mới.
- Hủy một Instance.
- Thất bại khi khởi tạo Instance.
- Thất bại khi hủy một instance.

Chúng ta sẽ chỉ tạo thông báo tới một email duy nhất, bao gồm các thông tin:

- **Send a notification to**: `asg-topic`. Mình sẽ chọn một topic để gửi.
- **With these recipients**: nhập email mà bạn muốn SNS gửi tới.
- **Event types**: chọn tất cả.
- Ấn **Next**.

    ![TB](/images/2.prerequisite/041-iamrole.png)

    ![TB2](/images/2.prerequisite/041-iamrole.png)

Xác nhận lại các thông tin và **Create Auto Scaling group**.

![create](/images/2.prerequisite/041-iamrole.png)

#### Kết quả

Kiểm tra và đăng ký nhận email từ topic.

![kq](/images/2.prerequisite/041-iamrole.png)

![kq2](/images/2.prerequisite/041-iamrole.png)

Vào trong tab **Activity** của **ASG FCJ-Management-ASG** để kiểm tra