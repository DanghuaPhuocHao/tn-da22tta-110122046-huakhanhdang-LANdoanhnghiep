# Đồ án mạng doanh nghiệp trên GNS3

Đây là một dự án mô phỏng mạng doanh nghiệp bằng GNS3, dùng để thể hiện cách xây dựng và vận hành một mạng LAN trong môi trường doanh nghiệp. Dự án tập trung vào việc triển khai các chức năng mạng quan trọng như VLAN, DHCP, định tuyến giữa các VLAN, OSPF, NAT/PAT, DNS, dịch vụ web, SMB, RDP, ACL và các cơ chế dự phòng để đảm bảo mạng hoạt động ổn định và an toàn.

## Mục tiêu của dự án

Dự án này được thực hiện với mục tiêu mô phỏng một hệ thống mạng doanh nghiệp thực tế, gồm các phòng ban khác nhau và các dịch vụ mạng cần thiết cho hoạt động hằng ngày. Qua dự án, có thể thấy được cách phân chia mạng theo vai trò, cách cấp phát địa chỉ IP, cách cho máy trạm truy cập Internet, cách cung cấp dịch vụ nội bộ và cách áp dụng kiểm soát truy cập bằng ACL. Mô hình này giúp người xem hiểu rõ hơn về cách một mạng doanh nghiệp được thiết kế, vận hành và bảo trì.

## Nội dung chính của dự án

- Mô phỏng mạng doanh nghiệp với nhiều VLAN riêng biệt cho các phòng ban như nhân sự, kế toán, kỹ thuật, giám đốc và máy chủ.
- Cấu hình DHCP để các thiết bị client nhận IP tự động đúng với từng VLAN.
- Thiết lập định tuyến giữa các VLAN và giữa các mạng nội bộ với mạng Internet.
- Sử dụng OSPF để trao đổi thông tin định tuyến giữa các thiết bị Layer 3.
- Cấu hình NAT/PAT để các máy trong mạng nội bộ có thể truy cập Internet.
- Triển khai DNS, web server, SMB và RDP để mô phỏng các dịch vụ nội bộ.
- Áp dụng ACL để kiểm soát quyền truy cập giữa các VLAN và các dịch vụ khác nhau.
- Thực hiện kiểm tra tính dự phòng và khả năng chuyển đổi khi một đường kết nối chính gặp sự cố.
- Tạo môi trường tương tự như một công ty có nhiều phòng ban, nhiều nhóm người dùng và nhiều yêu cầu về an ninh mạng.

## Kiến trúc mạng mô phỏng

Mô hình trong dự án được xây dựng theo hướng phân tầng. Ở tầng truy cập là các switch và thiết bị đầu cuối của người dùng. Ở tầng phân phối và lõi là các thiết bị Layer 3 có khả năng định tuyến và điều phối lưu lượng. Ngoài ra còn có các router nối mạng nội bộ với Internet. Cách tổ chức này giúp dễ dàng quản lý, mở rộng và kiểm tra lỗi khi cần thay đổi cấu hình hoặc thêm thiết bị mới.

Mỗi VLAN đại diện cho một nhóm người dùng hoặc một bộ phận riêng, giúp tách biệt luồng dữ liệu và tăng tính bảo mật. Khi các thiết bị trong cùng VLAN giao tiếp với nhau, lưu lượng đi qua mạng nội bộ một cách thuận tiện; khi cần trao đổi với VLAN khác thì phải thông qua thiết bị định tuyến. Đây là cách thức thường được áp dụng trong mạng doanh nghiệp thực tế.

## Quy trình kiểm tra và vận hành

Sau khi topology được khởi động, người dùng có thể kiểm tra các chức năng mạng theo thứ tự từ cơ bản đến nâng cao. Đầu tiên là kiểm tra kết nối vật lý và trạng thái interface, sau đó là kiểm tra IP được cấp phát đúng, tiếp theo là kiểm tra định tuyến và kết nối Internet, rồi mới đến các dịch vụ nội bộ và chính sách truy cập. Việc kiểm tra theo trình tự giúp phát hiện nhanh lỗi và hiểu rõ hơn về nguyên nhân nếu có vấn đề xảy ra.

Trong quá trình demo, có thể kiểm tra các lệnh cơ bản như xem IP, kiểm tra bảng định tuyến, kiểm tra neighbor OSPF, kiểm tra NAT translation và kiểm tra ACL. Những thao tác này cho thấy mạng không chỉ được cấu hình mà còn đang hoạt động đúng như kỳ vọng.

## Cấu trúc thư mục

- src/Demo: file topology GNS3 và các cấu hình liên quan để chạy mô hình mạng.
- src/Kichbantest: kịch bản kiểm tra nhanh các chức năng của mạng sau khi triển khai.
- docs: tài liệu báo cáo, slide và poster của đồ án.

## Yêu cầu để chạy dự án

- Phần mềm GNS3 đã được cài đặt.
- Có sẵn các image hoặc thiết bị mạng cần thiết tương thích với topology.
- Máy tính có đủ cấu hình để chạy mô phỏng mạng nhẹ nhàng.

## Cách sử dụng

1. Mở file GNS3 trong thư mục src/Demo.
2. Tải và khởi động topology trong GNS3.
3. Kiểm tra trạng thái các thiết bị như router, switch và máy tính.
4. Thực hiện các bước kiểm tra theo file trong src/Kichbantest để xác nhận các chức năng mạng đã hoạt động đúng.
5. Nếu cần, tham khảo báo cáo trong thư mục docs để hiểu rõ hơn về kiến trúc và cấu hình của mô hình.

## Những chức năng đã được kiểm tra

- Kiểm tra kết nối giữa các VLAN.
- Kiểm tra DHCP và gateway của từng VLAN.
- Kiểm tra kết nối ra Internet.
- Kiểm tra DNS, web, SMB và RDP.
- Kiểm tra ACL và quy tắc truy cập.
- Kiểm tra định tuyến OSPF và tính dự phòng.
- Kiểm tra khả năng truy cập dịch vụ nội bộ từ các phòng ban khác nhau.
- Kiểm tra tình huống khi một đường liên kết chính bị lỗi hoặc ngắt kết nối.

## Ý nghĩa của dự án

Dự án này không chỉ là một bài tập mô phỏng mạng mà còn là cách để hiểu rõ hơn về cách vận hành của một mạng doanh nghiệp thật. Qua dự án, người học có thể thấy được mối liên hệ giữa lý thuyết và thực tế, từ cách chia subnet, cấu hình router và switch, cho đến cách áp dụng quản trị truy cập và bảo mật.

Đây cũng là một tài liệu hữu ích để trình bày trước giảng viên, vì có thể minh họa được các khái niệm mạng một cách trực quan và dễ hiểu thông qua mô hình GNS3.

## Video demo

Video demo của dự án: https://www.youtube.com/watch?v=-VVIu5X6ANs
