---
title : "Triển khai máy chủ web"
date :  "2024-11-01" 
weight : 6 
chapter : false
pre : " <b> 2.5 </b> "
---

Cài đặt node version manager (nvm)

  ```bash
    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.0/install.sh | bash
  ```

![role](/images/2.prerequisite/01-vpc.png)

Sử dụng nvm để cài đặt Node.js bằng cách nhập nội dung sau vào dòng lệnh.

  ```bash
    nvm install 20
  ```

![role1](/images/2.prerequisite/02-CreateVPC.png)

clone repository code ứng dụng

  ```bash
    git clone https://github.com/First-Cloud-Journey/000004-EC2.git
  ```

![role1](/images/2.prerequisite/040-iamrole.png)

Đến thư mục của bài lab

  ```bash
    cd 000004-EC2
  ```
  
  ![role1](/images/2.prerequisite/040-iamrole.png)

Xem các thư mục có trong web và Sử dụng npm init khởi tạo project sẽ tạo ra file package.json mẫu.  

  ```bash
    ls
    npm i
  ```

![createpolicy](/images/2.prerequisite/041-iamrole.png)

Cài đặt pm2 trong Global, PM2 được sử dụng để quản lý và giám sát các ứng dụng Node.js đang chạy. Nó cho phép các ứng dụng chạy dưới nền. Kiểm tra phiên bản

  ```bash
    npm install -g pm2
    pm2 --version
  ```
  
  ![createpolicy](/images/2.prerequisite/041-iamrole.png)

chúng ta định nghĩa lại câu script để chạy ứng dụng, chúng ta sẽ dùng vim để mở file pakage.json, trong phần scripts ở key start, gán cho nó value sau, điều này sẽ giúp ứng dụng của chúng ta chạy nền:

  ```bash
    pm2 start app.js
  ```

  ![createpolicy](/images/2.prerequisite/041-iamrole.png)

Tiếp tục dùng vim để vào file .env, sau đó nhập vào nội dung sau để thiết lập kết nối tới database.

  ```bash
    DB_HOST='db_host của bạn'
    DB_NAME='awsfcjuser'
    DB_USER='admin'
    DB_PASS='mật khẩu tạo ở bước 2.3'
  ```

  ![createpolicy](/images/2.prerequisite/041-iamrole.png)

Tiến hành khởi chạy ứng dụng:

  ```bash
    npm start
  ```

  ![createpolicy](/images/2.prerequisite/041-iamrole.png)

Tiếp theo, chúng ta cần lấy được public DNS của instance để có thể truy cập được ứng dụng từ trình duyệt.

  ![createpolicy](/images/2.prerequisite/041-iamrole.png)

Ứng dụng đã hoạt động

  ![createpolicy](/images/2.prerequisite/041-iamrole.png)

Tiếp theo chúng ta dùng câu lệnh `pm2 startup` để tiến hành cấu hình PM2 tự động khởi động lại các ứng dụng khi máy chủ khởi động lại. Nó sẽ yêu cầu thiết lập Startup Script, hãy copy/paste command đó và chạy.

  ![createpolicy](/images/2.prerequisite/041-iamrole.png)

Chạy lệnh `pm2 save` để lưu trạng thái hiện tại của các tiến trình vào danh sách khởi động.

  ![createpolicy](/images/2.prerequisite/041-iamrole.png)




