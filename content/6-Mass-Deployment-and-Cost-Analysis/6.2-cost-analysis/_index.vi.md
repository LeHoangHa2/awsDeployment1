---
title : "Phân Tích Chi Phí Khi Triển Khai 50 EC2 Instances"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre: <b> 6.2 </b>
---

### Mục tiêu:
- Ước lượng chi phí khi triển khai hàng loạt 50 EC2 từ Custom AMI, so sánh với cách làm truyền thống bằng Standard AMI và đánh giá hiệu quả kinh tế khi dùng Custom AMI + User Data.

---

### 1. Thông số hệ thống đã triển khai

| Thông số              | Giá trị                         |
|------------------------|---------------------------------|
| Số lượng EC2           | 50 instances                   |
| Loại instance          | `t2.micro`                     |
| AMI sử dụng            | Custom AMI (tối ưu sẵn)        |
| Vùng triển khai        | ap-southeast-1 (Singapore)     |
| Thời gian chạy         | 1 giờ (ví dụ cho so sánh)      |

---

### 📊 2. Ước lượng chi phí (dựa trên giá thực tế tháng 07/2025)

#### ✅ Giá tham khảo `t2.micro` tại ap-southeast-1:
- $0.0128 USD/giờ (tính theo **on-demand**, chưa bao gồm thuế)

#### 🧮 Tính toán:

| Hạng mục              | Giá trị                 |
|-----------------------|-------------------------|
| Giá 1 EC2/giờ         | $0.0128                 |
| Tổng 50 EC2/giờ       | $0.0128 × 50 = $0.64    |
| Tổng 50 EC2/ngày      | $0.64 × 24 = $15.36     |
| Tổng 50 EC2/tháng     | $15.36 × 30 = $460.8    |

> 🔸 Ghi chú: giá có thể thay đổi theo region và billing tier.

---

### 🔄 3. So sánh chi phí: Custom AMI vs Standard AMI

| Tiêu chí                  | Custom AMI                          | Standard AMI                        |
|---------------------------|-------------------------------------|-------------------------------------|
| Thời gian boot            | Nhanh hơn (30–40s)                  | Chậm hơn (50–60s)                   |
| Cấu hình phần mềm sẵn     | Có (nginx, log, v.v)                | Không có                            |
| Tốn công cài đặt lại      | Không                               | Có (mất vài phút mỗi máy)           |
| Chi phí vận hành          | Như nhau (cùng instance type)       | Như nhau                            |
| **Tổng chi phí gián tiếp**| **Thấp hơn do tiết kiệm thời gian**| Cao hơn nếu thao tác thủ công       |

---

### ✅ 4. Nhận xét tổng quan

- Về mặt **giá EC2**, dùng AMI nào cũng như nhau nếu cùng loại máy.
- Tuy nhiên, **Custom AMI tiết kiệm thời gian triển khai** rất lớn nếu bạn triển khai 50–100 máy trở lên.
- Kết hợp với User Data Script giúp bạn:
  - Triển khai hàng loạt không cần SSH
  - Giảm sai sót do thao tác tay
  - Tiết kiệm nhân lực vận hành

---

### 📌 Kết luận:

Dù chi phí EC2 giống nhau, Custom AMI + User Data giúp giảm thiểu chi phí **ẩn** như:
- Thời gian kỹ sư DevOps
- Lỗi cấu hình
- Quản lý không đồng nhất

→ Đây là cách **hiệu quả, chuẩn hóa và tiết kiệm chi phí dài hạn** khi mở rộng hệ thống trên AWS.
