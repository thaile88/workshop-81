---
title : "Tạo Security Group cho API Service"
date : "`r Sys.Date()`"
weight : 4
chapter : false
pre : " <b> 3.2.3. </b> "
---

Security Group này chỉ cho phép lưu lượng từ ALB tới các API servers trên cổng 8080, đảm bảo bảo mật và kiểm soát truy cập chặt chẽ.

#### **Các bước thực hiện:**

1. **Truy cập trang Security Groups**
   - Điều hướng đến **EC2 Service** → **Security Groups**
   - Nhấp **Create security group**

2. **Cấu hình cơ bản**
   - **Tên Security Group:** `api-sg`
   - **Mô tả:** `Cho phép lưu lượng từ ALB tới API servers trên c cổng 8080`
   - **VPC:** Chọn `advanced-alb-vpc`
   ![Cấu hình cơ bản](/images/3-VPCSetup/3.2-CreateSecurityGroup/3.2.3-APIServiceSG/01-BasicConfig.png)

3. **Thiết lập Inbound Rules**
   - Nhấp **Add rule** và cấu hình:
     - **Loại:** Custom TCP
     - **Port range:** 8080
     - **Nguồn:** Chọn Security Group `alb-sg` từ danh sách
   ![Cấu hình Inbound Rules](/images/3-VPCSetup/3.2-CreateSecurityGroup/3.2.3-APIServiceSG/02-InboundRule.png)

4. **Hoàn tất**
   - Nhấp **Create security group**