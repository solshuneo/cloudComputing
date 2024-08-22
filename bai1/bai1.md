# Bai 1: Review

## Đề bài: 
- Công ty Banna phát triển 2 server xoilac.xxx (172.16.69.0/24) và banhmy.xxx (172.16.96.0/24)
- Cả 2 đều có thể truy cập Internet một cách tự do nhưng người dung internet có thể truy cậ các dịch vụ web do họ cung cấp thông qua internet của bộ định tuyến

## Bài làm:

### Phần 1: tính ip
- x.y.z.y/24 thì sẽ có $2^8 = 256$ IPs
- xoilac.xxx 172.16.69.0 -> 172.16.69.255
    + ip address 172.16.69.2
    + gateway 172.16.69.1
- banhmy.xxx 17216.96.0 -> 172.16.96.255
    + ip address 172.16.96.2
    + gateway 172.16.96.1
### Phần 2: set router
- do route isp là 6.9.6.9/24
- nên đặt ip tại router có thể 6.9.6.1 đến 6.9.6.254 trừ 6.9.6.9
- mình sẽ chọn là 6.9.6.10 cho địa chỉ ip của route mà kết nối với 2 switch kết nối với 2 server trên
- mình sẽ set là 6.9.6.10/24
```bash
route(config)# interface [gate]
route(config-if)# ip address 6.9.6.10 255.255.255.0
```
- mình sẽ định tuyến từ route này đến isp
```bash
route(config)# ip route 0.0.0.0 0.0.0.0 6.9.6.9
```
- mình sẽ ping route này đến isp
```bash
route(config)# ping 6.9.6.9
```
- tiếp tục ping đến server
```bash
route(config)# ping 8.8.8.8
route(config)# ping 8.8.8.10
route(config)# ping 8.8.8.11
```
- khi nào 5/5 100% thì thôi