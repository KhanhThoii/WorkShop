---
title : "Giới thiệu"
date :  "2024-11-01" 
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---
#### Giới thiệu

Trong bối cảnh công nghệ thông tin hiện nay, việc quản lý hiệu quả tài nguyên hệ thống và đảm bảo độ ổn định của dịch vụ là yêu cầu thiết yếu đối với các doanh nghiệp. Khi số lượng người dùng truy cập ngày càng gia tăng, việc đảm bảo hiệu suất hệ thống luôn ổn định trở thành thách thức lớn. Do đó, đề tài **“Triển khai hệ thống Workload Management bằng AWS”** sẽ tập trung vào việc xây dựng một hệ thống quản lý tài nguyên linh hoạt và hiệu quả, tận dụng các công cụ và dịch vụ mạnh mẽ của AWS như **Auto Scaling**, **Load Balancer** và **CloudWatch**.

#### Auto Scaling Group

1. Auto Scaling Group là gì và Tại sao cần sử dụng Auto scaling group ?
   
   **Auto Scaling Group (ASG)** là một dịch vụ của Amazon Web Services (AWS) giúp tự động điều chỉnh số lượng máy chủ (instances) dựa trên nhu cầu thực tế của ứng dụng. Khi lưu lượng truy cập hoặc nhu cầu sử dụng tăng lên, ASG có thể tự động tạo thêm máy chủ mới để đảm bảo hiệu suất ổn định. Ngược lại, khi lưu lượng giảm, ASG sẽ giảm số lượng máy chủ để tiết kiệm chi phí.

2. Các lợi ích chính của Auto Scaling Group:
   
    **Khả năng mở rộng tự động:** Tăng hoặc giảm số lượng máy chủ dựa trên các điều kiện được thiết lập, ví dụ như mức độ CPU sử dụng, bộ nhớ, hoặc số lượng yêu cầu.

    **Tối ưu chi phí:** Tự động tắt máy chủ không cần thiết khi nhu cầu giảm, giúp tiết kiệm tài nguyên.

    **Đảm bảo tính sẵn sàng:** Duy trì một số lượng máy chủ tối thiểu để đảm bảo hệ thống luôn hoạt động, ngay cả khi một số máy chủ gặp sự cố.

#### Elastic Load Balancer

**Elastic Load Balancer (ELB)** là một dịch vụ của Amazon Web Services (AWS) dùng để phân phối tự động lưu lượng truy cập đến nhiều máy chủ (instances) trong một hoặc nhiều vùng sẵn sàng (Availability Zones). ELB giúp đảm bảo rằng các yêu cầu truy cập được phân bổ đồng đều, tránh tình trạng quá tải ở một máy chủ, từ đó tối ưu hóa hiệu suất và tăng tính sẵn sàng của ứng dụng.

#### Launch Template

**Launch Template** là một công cụ trong Amazon Web Services (AWS) giúp đơn giản hóa và tự động hóa việc khởi tạo các máy chủ ảo (EC2 instances) bằng cách lưu trữ các cấu hình khởi tạo. Khi bạn sử dụng Launch Template, bạn không cần cấu hình thủ công mỗi khi tạo instance mới, giúp tiết kiệm thời gian và đảm bảo tính nhất quán.

#### Target Group

**Target Group** là một thành phần của Elastic Load Balancer (ELB), dùng để xác định và quản lý các EC2 instances mà Load Balancer sẽ phân phối lưu lượng truy cập đến.