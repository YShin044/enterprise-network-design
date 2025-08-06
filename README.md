# Đồ án Thiết kế Mạng Doanh nghiệp

Đây là đồ án cuối kỳ môn học Thiết kế Mạng, trình bày giải pháp xây dựng hệ thống mạng cho Công ty 2 chi nhánh. Dự án tập trung vào việc thiết kế một cơ sở hạ tầng mạng có hiệu năng cao, khả năng mở rộng, độ sẵn sàng và tính bảo mật tốt để đáp ứng nhu cầu hoạt động của doanh nghiệp.

## 📝 Tổng quan dự án

Dự án thực hiện khảo sát và phân tích yêu cầu để thiết kế một hệ thống mạng hoàn chỉnh cho công ty THACO, một doanh nghiệp chuyên sản xuất linh kiện ô tô, với các đặc điểm chính:

- **Quy mô**: 2 chi nhánh tại Quận 7 và Quận 9 (TP.HCM) với 3 tòa nhà, 17 phòng ban.
- **Số lượng người dùng**: Hỗ trợ khoảng 2000 lượt truy cập/ngày.
- **Yêu cầu chính**:
    - Hiệu năng cao và ổn định với kết nối Gigabit đến máy trạm.
    - Độ sẵn sàng cao, có cơ chế dự phòng thiết bị và đường truyền (Redundancy, Failover).
    - Bảo mật đa lớp (Firewall, VLAN, ACLs, VPN).
    - Khả năng quản lý, bảo trì và mở rộng dễ dàng.
- **Ngân sách dự kiến**: Khoảng 8 tỷ VNĐ.

## 🏗️ Kiến trúc & Thiết kế

Hệ thống được thiết kế theo các mô hình và công nghệ hiện đại để đảm bảo hiệu quả và sự linh hoạt.

### 1. Mô hình mạng
- **Mạng phân lớp (Hierarchical Network Model)**: Sử dụng mô hình 3 lớp Core - Distribution - Access để phân chia chức năng, tối ưu luồng dữ liệu và dễ dàng quản lý.
- **Spine-Leaf cho Data Center**: Áp dụng kiến trúc hai tầng Spine-Leaf tại mỗi chi nhánh để tăng băng thông East-West, giảm độ trễ và dễ dàng mở rộng cho các máy chủ.
- **Phân vùng mạng**:
    - **Inside**: Mạng nội bộ cho nhân viên, được chia nhỏ thành các VLAN cho từng phòng ban.
    - **DMZ**: Vùng chứa các máy chủ công cộng (Web/Email) để tách biệt với mạng nội bộ.
    - **Outside**: Kết nối ra Internet.

### 2. Hạ tầng vật lý
- **Hệ thống cáp**:
    - **Cáp đồng**: Sử dụng **Cat6A** cho toàn bộ kết nối từ người dùng cuối về tủ mạng, đảm bảo hỗ trợ tốc độ lên đến 10Gbps.
    - **Cáp quang**: Sử dụng cáp quang Multimode OM4 cho các kết nối trục (backbone) giữa các tòa nhà và đến lớp Core.
- **Kết nối WAN**: Sử dụng VPN IPsec để kết nối an toàn giữa 2 chi nhánh.

## ✨ Các tính năng nổi bật

- **Tính sẵn sàng cao (High Availability)**:
    - Dự phòng đường truyền với EtherChannel (LACP).
    - Dự phòng thiết bị Core/Distribution với công nghệ Stacking (StackWise) hoặc VRRP/HSRP.
    - Dự phòng Firewall/Router.
    - Dự phòng nguồn (Dual Power Supply) và hệ thống UPS.
- **Bảo mật toàn diện**:
    - Tường lửa (Firewall) tại biên mạng để kiểm soát truy cập và phòng chống tấn công (IPS).
    - Phân đoạn mạng bằng VLAN và kiểm soát truy cập giữa các VLAN bằng ACLs.
    - Bảo mật lớp 2: DHCP Snooping, Dynamic ARP Inspection, Port Security.
    - Truy cập từ xa an toàn qua SSL VPN.
- **Dịch vụ mạng đầy đủ**:
    - Dịch vụ nội bộ: Active Directory, DNS, DHCP, File Server.
    - Dịch vụ công cộng: Web Hosting, Email Server.

## 🛠️ Thiết bị đề xuất

Dự án đề xuất sử dụng thiết bị từ các hãng uy tín để đảm bảo hiệu suất và độ tin cậy:

| Lớp mạng | Thiết bị đề xuất |
| :--- | :--- |
| **Core (Spine)** | Cisco Catalyst 9500-24Q |
| **Distribution** | Juniper EX4300-24T |
| **Access (Leaf)** | Cisco Catalyst 9200L-48P-4X (hỗ trợ PoE+) |
| **Server** | Dell PowerEdge R750 |
| **Router** | Juniper MX204 |
| **Firewall** | Juniper SRX320 |
| **Wi-Fi AP** | Aruba AP-515 (Wi-Fi 6) |

---
<em>"Tài liệu chỉ mang tính chất tham khảo"</em>
