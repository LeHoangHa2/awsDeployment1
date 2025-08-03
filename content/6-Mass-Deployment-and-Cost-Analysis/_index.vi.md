---
title : "Triển khai hàng loạt và phân tích chi phí"
date :  "`r Sys.Date()`" 
weight : 6 
chapter : false
pre : " <b> 6. </b> "
---

- Trong chương này, chúng ta sẽ thực hiện triển khai hàng loạt **50 EC2 instance** nhằm đánh giá hiệu năng thực tế của hai loại AMI:

+ **Custom AMI**: đã được tối ưu hoá và cài đặt sẵn phần mềm, user data script, agent giám sát.

+ **Standard AMI**: là image mặc định do AWS cung cấp.

- Việc triển khai hàng loạt này giúp kiểm chứng các yếu tố quan trọng như:

+ Thời gian khởi động thực tế

+ Khả năng đồng bộ cấu hình

+ Tính ổn định và khả năng mở rộng quy mô

+ Tác động chi phí khi mở rộng quy mô sử dụng

- Bên cạnh đó, chương này cũng sẽ cung cấp bảng phân tích chi phí chi tiết khi chạy 50 EC2 instance trong các khoảng thời gian khác nhau (1 giờ, 1 ngày, 1 tháng) để hỗ trợ việc ra quyết định tối ưu chi phí vận hành hệ thống.

- Thông qua chương này, ta sẽ thấy được lợi ích rõ rệt của việc sử dụng **Custom AMI** trong môi trường cần khởi tạo nhanh và quy mô lớn như **autoscaling, CI/CD hoặc production server**.