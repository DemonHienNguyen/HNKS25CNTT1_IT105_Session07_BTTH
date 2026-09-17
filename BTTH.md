## Nhiệm vụ 1: Nhận diện lớp và khai báo Cấu trúc 3 ngăn

+ 4 Đối tượng quản lý của QuickBite: Khách hàng, Đơn hàng, Món ăn, Nhân viên

## Nhiệm vụ 2:

+ Lớp Customer:
  + get_full_name(): String
  + set_full_name(name): String
  + get_phone_number(): String
  + get_address(): String
+ Lớp Employee:
  + call_customer(customer_id): String
  + get_email(): String
  + set_email(email): String
  + get_full_name(): String

## Nhiệm vụ 3 phân tích và lựa chọn Mối quan hệ giữa các lớp

+ Cặp quan hệ giữa Category và OrderItem (Aggregation) vì nếu như mà một id của category mà xóa thì phần OrderItem chỉ sửa lại phần category_id thành null chứ sẽ không xóa luôn phần OrderItem
+ Cặp quan hệ giữa OrderItem với Order sẽ là (Composition) vì sẽ để nếu có một đơn hàng bị xóa thì sẽ xóa cả bên orderitem cũng sẽ bị xóa theo, không thể tồn tại độc lập được
+ Cặp quan hệ giữa Employee với Shipper là (Genralization) thì shipper cũng sẽ kết thừa các thuộc tính từ Employee cũng như Shipper cũng sẽ có các phương thức riêng của Shipper

## Nhiệm vụ 4: 

+ Customer - Order: 1 - 0..*: Một Người có thể chưa tạo đơn nào hoặc nhiều đơn, một Order mải thuộc về đúng người đó
+ Order - OrderItem: 1 - 1..*: Một Order ít nhất phải có 1 OrderItem hoặc nhiều hơn, Một hoặc nhiều OrderItem chỉ thuộc về 1 Order
+ Order - Voucher: * - 0..1: Môt Order không dùng voucher hoặc dùng tối đa 1 voucher, 1 voucher có thể sử dụng nhiều trên nhiều Order

++ Bội số 1..* giữa Order và OrderItem: Dùng để chặn lỗi đặt/ Tạo đơn hàng, gây lỗi tính toán doanh thu và lãng phí tài nguyen

++ Bội số 0..1 giữa Order và Voucher: sẽ khóa chặt quy tắc kinh doanh, đảm bảo mỗi đơn hàng chỉ được giảm giá bằng tối đa 1 mã voucher

## Nhiệm vụ 5: Chuyển đổi kịch bản đặc tả Use Case sang Class Diagram

| Từ loại  | Từ ngữ trong kịch bản                          | Lớp / Thuộc tính / Phương thức                               |
| ---------- | -------------------------------------------------- | ------------------------------------------------------------------ |
| Danh từ   | Đơn hàng, Mã đơn hàng, Tổng tiền          | Lớp Order                                                         |
| Danh từ   | Chi tiết đơn, Món ăn, Số lượng             | Lớp OrderItem                                                     |
| Danh từ   | Giao dịch thanh toán, phương thức thanh toán | Lớp Payment                                                       |
| Danh từ   | Hóa đơn, Ngày xuất                            | Lớp Receipt                                                       |
| Động từ | Xử lý thanh toán, Trả về kết quả            | Phương thức processPaymen(),verifyTransaction() trong Payment |
| Động từ | Xuất hóa đơn                                   | Phương thức generateReceipt() trong Receipt                   |

Phác thảo cấu trúc 4 lớp trích xuất và phần 6 sẽ thuộc BTTH_01 - 02 .drawio
