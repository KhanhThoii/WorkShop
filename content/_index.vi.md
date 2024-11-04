---
title : "Deploying FCJ Management Application with Auto Scaling Group"
date :  "2024-11-01" 
weight : 1 
chapter : false     
---
# Triển khai ứng dụng FCJ Management với Auto Scaling Group

### Tổng quan

Trong hướng dẫn này, chúng ta sẽ triển khai ứng dụng với Auto Scaling Group nhằm đảm bảo khả năng mở rộng linh hoạt, đáp ứng kịp thời nhu cầu truy cập của người dùng. Đồng thời, chúng ta sẽ tích hợp Load Balancer để phân phối lưu lượng và điều phối các yêu cầu từ người dùng đến tầng ứng dụng (Application Tier), giúp tối ưu hiệu suất và đảm bảo tính sẵn sàng của hệ thống.

Trước khi bắt đầu, hãy chắc chắn bạn đã tham khảo tài liệu về cách triển khai Ứng dụng FCJ Management trên máy ảo Windows hoặc Amazon Linux để nắm rõ các bước thiết lập trên máy ảo. Chúng ta sẽ sử dụng các máy ảo FCJ Management đã được triển khai để thực hiện mở rộng quy mô tự động và đồng loạt trong Auto Scaling Group.

![Mohinh](/images/mohinh.png)

### Nội dung    

 1. [Giới thiệu](1-introduce/)
 2. [Các bước chuẩn bị](2-prerequiste/)
 3. [Khởi tạo Template](3-create-launch-template/)
 4. [Thiết lập Load Balancer](4-setting-up-load-balancer/)
 5. [Kiểm thử](5-test)
 6. [Khởi tạo Auto Scaling Group](6-create-auto-scaling-group/)
 7. [Kiểm thử giải pháp manual scaling](7-test-solutions/)
 8. [Dọn dẹp tài nguyên](8-cleanup/)
