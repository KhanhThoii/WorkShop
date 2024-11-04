---
title : "Chuẩn bị các metric cho Predictive scaling"
date :  "2024-11-01" 
weight : 7 
chapter : false
pre : " <b> 2.6 </b> "
---

### Chuẩn bị dữ liệu cho Predictive scaling

Vì Predictive scaling cần phải có một lượng dữ liệu trong vòng hơn 2 ngày để có thể đưa ra được các dự đoán vào các ngày tiếp theo, mà ở đây chúng ta lại không có các dữ liệu đó cho nên là chúng ta sẽ cần phải chuẩn bị để giải lập một môi trường 

### Các bước chuẩn bị

Đầu tên là chúng ta sẽ tạo một folder mới với tên là `metric-preparation` và chuyển vào trong thư mục này

  ```bash
    mkdir metric-preparation && cd metric-preparation
  ```

Sau đó là tải kịch bản để chuẩn bị các dữ liệu

  ```bash
    curl -o prepare-metric-data.sh https://raw.githubusercontent.com/awslabs/ec2-spot-workshops/master/workshops/efficient-and-resilient-ec2-auto-scaling/prepare-metric-data.sh
  ```

![role](/images/2.prerequisite/01-vpc.png)

Sau khi tải xong thì vào trong để thay đổi phần câu lệnh trong kịch bản

  ```bash
    vim prepare-metric-data.sh
  ```

  ```bash
    #!/bin/bash
set -e
file=$1
group=$2
echo "=== Format metric file ==="
echo $file
echo $group

l=$(jq length $file)
i=0
while [ $i -lt $l ]
do
  time=$(date -d "$[5*$i] minutes ago")
  cat $file | jq --argjson i $i --arg t "$time" '.[$i].Timestamp |= $t' > tmp.json && mv tmp.json $file
  i=$[$i+1]
done

echo "replace autoscaling group name.."

sed -i $file -e "s/#ASGPLACEHOLDER#/$group/g"

echo "=== Complete ==="

  ```

![role1](/images/2.prerequisite/02-CreateVPC.png)

Sau khi chỉnh sửa xong thì giờ chúng ta tiến hành tải các dữ liệu chưa qua xử lý, Trước tiên là metric cho các instances.

  ```bash
    curl -o metric-cpu.json https://raw.githubusercontent.com/awslabs/ec2-spot-workshops/master/workshops/efficient-and-resilient-ec2-auto-scaling/metric-cpu.json
  ```

![role1](/images/2.prerequisite/040-iamrole.png)

Dữ liệu cho CPU

  ```bash
    curl -o metric-cpu.json https://raw.githubusercontent.com/awslabs/ec2-spot-workshops/master/workshops/efficient-and-resilient-ec2-auto-scaling/metric-cpu.json
  ```
  
  ![role1](/images/2.prerequisite/040-iamrole.png)

Tiến hành sửa đổi lần lượt 2 loại dữ liệu này, đầu tiên là cho CPU trước

  ```bash
    bash prepare-metric-data.sh metric-cpu.json FCJ-Management-ASG && cat metric-cpu.json
  ```

![createpolicy](/images/2.prerequisite/041-iamrole.png)

**Instances**   

  ```bash
    bash prepare-metric-data.sh metric-instances.json FCJ-Management-ASG && cat metric-instances.json
  ```
  
  ![createpolicy](/images/2.prerequisite/041-iamrole.png)

<div style="background-color: #e7f3fe; border-left: 4px solid #2196F3; padding: 10px; margin: 10px 0;">

**💡 Note**  
Ở 2 lệnh ở trên đều xuất hiện tham số **FCJ-Management-ASG** thì nó chính là tên của Auto Scaling Group mà chúng ta sẽ tạo về sau, nên về sau thì bạn cần sẽ phải tạo ASG với cùng tên như thế. Còn không thì bạn nên thay một cái tên khác từ bây giờ.

</div>

### Tải dữ liệu lên CloudWatch

Trong Amazon Linux 2023, và dùng đúng AMI thì AWS CLI đã được cài đặt sẵn ở bên trong, lúc này thì chúng ta chỉ cần lấy ra để cấu hình lại các crediential là được. Nên nhớ là bạn phải có một IAM User đủ quyền để tải dữ liệu lên CloudWatch hoặc ít nhất là đủ quyền để làm bài workshop này.

Vào trang IAM, vào thông tin IAM User và ấy Access Key Id và Serect Access Key

  ```bash
    aws configure
  ```

Tiến hành cấu hình

  ![createpolicy](/images/2.prerequisite/041-iamrole.png)

Sau đó là tải 2 file dữ liệu mà chúng ta đã chuẩn bị trước đó lên trên CloudWatch

  ```bash
    aws cloudwatch put-metric-data --namespace 'FCJ Management Custom Metrics' --metric-data file://metric-cpu.json
  ```

  ```bash
    aws cloudwatch put-metric-data --namespace 'FCJ Management Custom Metrics' --metric-data file://metric-instances.json 
  ```

  ![createpolicy](/images/2.prerequisite/041-iamrole.png)

### Kiểm tra

Vào trong **CloudWatch** để kiểm tra kết quả

- Tìm **CloudWatch**
- Click để vào trong CloudWatch Console

  ![createpolicy](/images/2.prerequisite/041-iamrole.png)

Trong giao diện Console của **CloudWatch**

- Chọn **All metrics**
- Chọn **FCJ Management Custom Metrics**

  ![createpolicy](/images/2.prerequisite/041-iamrole.png)

Chọn AutoScalingGroupName

  ![createpolicy](/images/2.prerequisite/041-iamrole.png)

Chọn tiếp 2 thông số như hình ở dưới, chờ một khoảng thời gian để nhận được kết quả.

  ![createpolicy](/images/2.prerequisite/041-iamrole.png)



