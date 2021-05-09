## Service Mesh là gì
- Nó là 1 service để quản lý việc các service liên kết với nhau

## Nó giải quyết vấn đề gì?
- Các service liên kết với nhau rất nhiều và có 1 vài vấn đề sẽ xảy ra như:
    + Timeout
    + Security
    + Retries
    + Monitoring

## Nó làm những gì
- Protocol conversion: biến đổi các kiểu liên kết khác nhau về thành cùng 1 kiểu
- Communication security: Mã hóa request
- Authentication: sử dựng authen các request
- Reliability: timeout, retry, health check, circut breaking (ngăn chặn việc fail toàn bộ request khi có 1 service fail)
- Monitoring
- Service Discovery
- Testing
- Load balancing

## Architecture
Mỗi 1 service đứng trước nó sẽ có 1 thằng mesh để handle các việc như là convert protocol, security, rồi tạo circut breaker, rồi timeout handling

Sau đó sẽ có 1 thằng gọi là control plane để manage những thằng mesh đó. Thằng control plane sẽ định nghĩa loại protocol nào dành cho service nào, sercurity nào được sử dụng
![image](https://user-images.githubusercontent.com/45547213/116768401-83d09780-aa60-11eb-878e-42f79acc4dd8.png)

## Các loại của service mesh
- In-process: Là nó nằm trong service cmnl là 1 phần service 
![image](https://user-images.githubusercontent.com/45547213/116768529-64863a00-aa61-11eb-80e0-b564773c50bb.png)

- Sidecar: Nó nằm bên ngoài. Mỗi lần nó gọi ra ngoài nó sẽ gọi thằng mesh service rồi bảo là nó muôn gọi thằng nào thằng mesh serivce sẽ take care phần còn lại
![image](https://user-images.githubusercontent.com/45547213/116768537-74058300-aa61-11eb-85cd-6a0483d80114.png)

- So sánh giữa 2 cái
![image](https://user-images.githubusercontent.com/45547213/116768552-8ed7f780-aa61-11eb-9d3a-0ee10762b9fb.png)

Platform agnostic là gì: có thể chọn loại mesh được thiết kế bởi bất kì công nghệ nào

Code agnostic là gì: Chỉ cần gọi thằng api của mesh thôi và thằng service đ cần care phần còn lại là như nào

## Implementations
- Sidecar: Đừng tự phát triển hãy sử dụng
![image](https://user-images.githubusercontent.com/45547213/116768662-9055ef80-aa62-11eb-8149-13d884809732.png)

## Khi nào dùng service mesh
- Có rất nhiều services
- Các service mà gọi đến nhau nhiều thì sử dụng 2 cái đấy với nhau
- Có complex communication requirement