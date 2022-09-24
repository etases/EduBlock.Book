---
title: "Design Article (VI)"
subtitle: "Bước đầu thực hiện số hóa hoàn toàn học bạ ở Việt Nam"
---

## Giới thiệu

Hiện nay công nghệ đang phát triển. Ngành giáo dục Việt Nam cũng đã chuyển đổi số rất nhiều bộ phận như áp dụng công nghệ trong giảng dạy cho giáo viên, trang thông tin liên lạc trực tuyến giữa nhà trường và phụ huynh, hình thức học trực tuyến, etc. Tuy nhiên, trong khi đang phát triển công nghệ ở nhiều mặt trong ngành và cố gắng giảm bớt gánh nặng với các công việc ngoài lề cho giáo viên thì vẫn có nhiều vấn đề khi cố gắng áp dụng công nghệ vào một số bộ phận. Một trong số đó là vấn đề về học bạ và số hóa học bạ.

Học bạ là một sổ theo dõi quá trình học tập của học sinh. Nó chứa thông tin sơ lược về lí lịch, quá trình và kết quả học tập từng năm, đồng thời có lời nhận xét và chữ kí của giáo viên chủ nhiệm của từng năm. Việc ghi học bạ hiện nay ở Việt Nam sử dụng học bạ giấy, theo một quy trình chặt chẽ, có tính pháp lí để đảm bảo tính trung thực và nghiêm minh khi đánh giá. Sơ lược thì sau mỗi học kì, giáo viên chủ nhiệm sẽ thu thập điểm số tổng kết của từng môn học từ các giáo viên bộ môn, sau đó ghi vào học bạ của từng học sinh, đồng thời ghi nhận xét và kí tên. Nhưng có bất cập với học bạ giấy như việc giáo viên phải ghi đúng điểm của từng học sinh, học bạ có thể bị mất, etc.

Hiện nay đã có một số địa phương đang số hóa học bạ, hay còn được gọi là áp dụng học bạ điện tử. Nhưng việc triển khai không đồng bộ, nửa vời đã làm tăng khối lượng công việc ngoài của giáo viên lên gấp đôi, khi họ vừa phải ghi thông tin lên học bạ giấy, vừa phải nhập thông tin đó lên hệ thống học bạ điện tử của trường. Ngoài ra còn có một số vấn đề về tính minh bạch, trung thực và độ an toàn của dữ liệu trên các hệ thống đó.

Bài báo này được đăng lên để phân tích những bất cập trong các hệ thống học bạ điện tử hiện nay, đồng thời đề xuất giải pháp để bước đầu thực hiện số hóa hoàn toàn học bạ ở Việt Nam.

## Về các hệ thống hiện tại

## Giải pháp & Thiết kế

### Hệ thống cơ 

```{.plantuml caption="System architecture without BlockChain"}
@startuml

left to right direction

component "Trusted Record Service" as TRS #Gold

component "Request Server 1" as RS1 #Lime
component "Frontend Server 1" as FS1
FS1 -- RS1

component "Request Server 2" as RS2 #Lime
component "Frontend Server 2" as FS2
FS2 -- RS2

component "Request Server 3" as RS3 #Lime
component "Frontend Server 3" as FS3
FS3 -- RS3

RS1 -- TRS
RS2 -- TRS
RS3 -- TRS

@enduml
```

### Hệ thống có áp dụng công nghệ dữ liệu phân tán

```{.plantuml caption="System architecture with BlockChain"}
@startuml

left to right direction

component "Chain Node 1" as CN1 #Aqua
component "Request Server 1" as RS1 #Lime
component "Frontend Server 1" as FS1
RS1 - CN1
FS1 - RS1

component "Chain Node 2" as CN2 #Aqua
component "Request Server 2" as RS2 #Lime
component "Frontend Server 2" as FS2
RS2 - CN2
FS2 - RS2

component "Chain Node 3" as CN3 #Aqua
component "Request Server 3" as RS3 #Lime
component "Frontend Server 3" as FS3
RS3 - CN3
FS3 - RS3

component ".." as E1 #Aqua
component ".." as E2 #Aqua

CN1 -- CN2
CN2 -- CN3

E1 -- CN1
CN3 -- E2

@enduml
```

## Kết thúc

## Nguồn tham khảo

- [Giáo viên khốn khổ vì học bạ giấy](https://vnexpress.net/giao-vien-khon-kho-vi-hoc-ba-giay-4442649.html)
- [Học bạ giấy thời 4.0](https://vnexpress.net/hoc-ba-giay-thoi-4-0-4444060.html)
- [Có học bạ điện tử sao còn làm khó GV khi yêu cầu "bản sao học bạ công chứng"](https://giaoduc.net.vn/co-hoc-ba-dien-tu-sao-con-lam-kho-gv-khi-yeu-cau-ban-sao-hoc-ba-cong-chung-post226595.gd)