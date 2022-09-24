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

### Hệ thống cơ bản 

```{.plantuml caption="Hệ thống cơ bản" id="fig-overview"}
@startuml

left to right direction

component "Trusted Record Service" as TRS #Gold

component "Request Server 1" as RS1 #Lime
component "Frontend Server 1" as FS1
FS1 .. RS1

component "Request Server 2" as RS2 #Lime
component "Frontend Server 2" as FS2
FS2 .. RS2

component "Request Server 3" as RS3 #Lime
component "Frontend Server 3" as FS3
FS3 .. RS3

RS1 -- TRS
RS2 -- TRS
RS3 -- TRS

@enduml
```

@fig-overview là sơ lược về hệ thống được đề xuất, bao gồm:

*   Trusted Record Service (Trung tâm lưu trữ học bạ)
    
    Đây là trung tâm của hệ thống, nơi sẽ lưu trữ các học bạ đã được xác minh bởi các trường, và lịch sử chỉnh sửa của từng học bạ. Trung tâm này phải được sự tin tưởng của các thành viên tham gia hệ thống.
    
    Chỉ có các trường tham gia vào hệ thống mới có thể truy cập vào trung tâm để lấy học bạ, và chỉ có trường liên kết với học bạ đó mới được quyền lấy thông tin lí lịch và gửi yêu cầu cập nhật chỉnh sửa học bạ đó.

*   Request Server (Máy chủ tiếp nhận yêu cầu)
    
    Mỗi trường trong hệ thống sẽ được phát một máy chủ để thao tác trên Trusted Record Service, trong đó có giấy phép của bên Trusted Record Service cho biết định danh của trường và các quyền trong Trusted Record Service.

    Đây cũng là nơi lưu các bản học bạ đang được chỉnh sửa và xử lí các yêu cầu chỉnh sửa từ người dùng (giáo viên, học sinh), bao gồm xác minh tính hợp lệ và tính chính xác của yêu cầu chỉnh sửa đó, tạo một bản học bạ hoàn chỉnh từ các yêu cầu hợp lệ để gửi lên Trusted Record Service kèm với giấy phép được nhận từ Trusted Record Service.

    Mỗi trường sẽ có cách xác minh yêu cầu chỉnh sửa học bạ riêng, tùy đặc thù mỗi trường mà Request Server của trường đó sẽ khác, tuy nhiên phần thao tác trên Trusted Record Service là giống nhau vì phải gửi học bạ đã xác minh kèm với giấy phép của trường đó.

*   Frontend Server (Giao diện tương tác)

	Đây là phần phụ trợ cho Request Server để lấy, hiện các học bạ và gửi yêu cầu chỉnh sửa học bạ trên một giao diện dễ nhìn, dễ tương tác. Nó có thể là một phần trong trang quản lý của từng trường.

	Với việc Request Server của mỗi trường có thể khác nhau, giao diện của Frontend Server ở mỗi trường cũng sẽ khác nhau để thích ứng với đặc thù của từng trường.

Quy trình tương tác với hệ thống được thể hiện trong @fig-rs-workflow

::: {#fig-rs-workflow layout-ncol=1}

```{.plantuml caption="Người yêu cầu" id="fig-rs-workflow-requester"}
@startuml
actor "Người yêu cầu" as Requester
participant "Frontend Server" as Frontend
participant "Request Server" as Backend
participant "Trusted Record Service" as Record

== Lấy thông tin học bạ ==

Requester -> Frontend: Yêu cầu lấy học bạ, kèm điều kiện
activate Frontend
Frontend -> Backend: Yêu cầu lấy học bạ
activate Backend
Backend -> Record: Yêu cầu lấy học bạ
activate Record
Record --> Backend: Gửi học bạ tương ứng
deactivate Record
Backend -> Backend: Lọc học bạ theo điều kiện
Backend --> Frontend: Gửi học bạ tương ứng
deactivate Backend
Frontend --> Requester: Thể hiện trên giao diện người dùng
deactivate Frontend

== Yêu cầu chỉnh sửa học bạ ==
Requester -> Frontend: Yêu cầu chỉnh sửa học bạ
activate Frontend
Frontend -> Backend: Yêu cầu chỉnh sửa học bạ
activate Backend
alt Yêu cầu hợp lệ
  Backend -> Backend: Lưu trữ như một yêu cầu cần xác minh
  Backend --> Frontend: Thông báo thành công
  Frontend --> Requester: Thông báo thành công
else Yêu cầu không hợp lệ
  Backend --> Frontend: Thông báo không hợp lệ
  Frontend --> Requester: Thông báo không hợp lệ
end
deactivate Backend
deactivate Frontend
@enduml
```

```{.plantuml caption="Người xác minh" id="fig-rs-workflow-validator"}
@startuml
actor "Người xác minh" as Validator
participant "Frontend Server" as Frontend
participant "Request Server" as Backend
participant "Trusted Record Service" as Record

== Lấy yêu cầu chỉnh sửa học bạ ==
Validator -> Frontend: Yêu cầu lấy các yêu cầu chỉnh sửa học bạ, kèm điều kiện
activate Frontend
Frontend -> Backend: Lấy các yêu cầu chỉnh sửa học bạ, kèm điều kiện
activate Backend
Backend -> Backend: Lấy từ cơ sở dữ liệu cực bộ và lọc theo điều kiện
Backend --> Frontend: Gửi các yêu cầu chỉnh sửa học bạ
deactivate Backend
Frontend --> Validator: Thể hiện các yêu cầu trên giao diện người dùng
deactivate Frontend
== Xác nhận yêu cầu chỉnh sửa học bạ ==
Validator -> Frontend: Gửi xác nhận yêu cầu chỉnh sửa học bạ
activate Frontend
Frontend -> Backend: Gửi xác nhận yêu cầu chỉnh sửa học bạ
activate Backend
Backend -> Backend: Xóa yêu cầu đang chờ từ cơ sở dữ liệu nội bộ
alt Yêu cầu được chấp nhận
  Backend -> Backend: Lưu yêu cầu được xác thực vào cơ sở dữ liệu nội bộ
end
Backend --> Frontend: Gửi thông báo thành công
deactivate Backend
Frontend --> Validator: Hiện thông báo thành công
deactivate Frontend

loop khi tới lúc cần gửi lên Record Service
activate Backend
Backend -> Backend: Tạo học bạ từ các yêu cầu chỉnh sửa
Backend -> Record: Gửi học bạ kèm giấy phép
Record --> Backend: Thông báo thành công
deactivate Backend
end
@enduml
```

Quy trình tương tác với hệ thống
:::
Trong đó "Người yêu cầu" là học sinh hoặc giáo viên, và "Người xác minh" là giáo viên chủ nhiệm đại diện chính cho học bạ được yêu cầu chỉnh sửa trong Request Server

### Áp dụng công nghệ dữ liệu phân tán

```{.plantuml caption="Hệ thống có áp dụng công nghệ dữ liệu phân tán" id="fig-decentralized"}
@startuml

left to right direction

package "School 1" {
component "Chain Node 1" as CN1 #Aqua
component "Request Server 1" as RS1 #Lime
component "Frontend Server 1" as FS1
RS1 - CN1
FS1 . RS1
}

package "School 2" {
component "Chain Node 2" as CN2 #Aqua
component "Request Server 2" as RS2 #Lime
component "Frontend Server 2" as FS2
RS2 - CN2
FS2 . RS2
}

package "School 3" {
component "Chain Node 3" as CN3 #Aqua
component "Request Server 3" as RS3 #Lime
component "Frontend Server 3" as FS3
RS3 - CN3
FS3 . RS3
}

component ".." as E1 #Aqua
component ".." as E2 #Aqua

CN1 -- CN2
CN2 -- CN3

E1 -- CN1
CN3 -- E2

@enduml
```

Ta có thể mở rộng hệ thống bằng cách áp dụng công nghệ dữ liệu phân tán. Cụ thể, ta có thể tách Trusted Record Service thành các Chain Node và để các Chain Node cho các trường (School) như @fig-decentralized. Lúc này một Chain Node nhận yêu cầu chỉnh sửa học bạ từ Request Server sẽ không chỉ lưu trữ trên Chain Node đó mà còn sẽ gửi yêu cầu đó sang các Chain Node lân cận để cùng lưu trữ.

Cấp độ này thường được sử dụng ở hệ thống các trường tư nhân mà không theo các quy trình của các trường chính quy theo Bộ Giáo Dục, nên quyền hạn của các trường là tương đương nhau.

Hệ thống ở cấp độ này sẽ đảm bảo độ an toàn của dữ liệu học bạ trong trường hợp một Chain Node của một trường bị sập. Khi đó, ta có thể dùng giấy phép từ Request Server lên các Chain Node lân cận để lấy các dữ liệu khôi phục lại Chain Node đã sập. Tuy nhiên có bất lợi là mỗi Chain Node sẽ phải lưu một lượng lớn dữ liệu học bạ từ không chỉ chính trường giữ Chain Node đó mà còn các dữ liệu của các Chain Node lân cận.

### Lên quy mô liên sở

Ta có thể lên cấp độ của hệ thống lên quy mô liên sở, khi đó từng Chain Node sẽ do từng sở giáo dục duy trì như @fig-department.

```{.plantuml caption="Hệ thống có áp dụng công nghệ dữ liệu phân tán" id="fig-department"}
@startuml

skinparam linetype polyline
left to right direction

package "Department 1" {
component "Chain Node 1" as CN1 #Aqua
}

package "Department 2" {
component "Chain Node 2" as CN2 #Aqua
}

package "Department 3" {
component "Chain Node 3" as CN3 #Aqua
}

component ".." as E1 #Aqua
component ".." as E2 #Aqua

CN1 -d- CN2
CN2 -d- CN3

CN1 -u- E1
CN3 -d- E2

package "School 1.1" {
component "Request Server 1.1" as RS11 #Lime
component "Frontend Server 1.1" as FS11
RS11 -r- CN1
FS11 .r. RS11
}

package "School 1.2" {
component "Request Server 1.2" as RS12 #Lime
component "Frontend Server 1.2" as FS12
RS12 -r- CN1
FS12 .r. RS12
}

package "School 1.3" {
component "Request Server 1.3" as RS13 #Lime
component "Frontend Server 1.3" as FS13
RS13 -r- CN1
FS13 .r. RS13
}

package "School 2.1" {
component "Request Server 2.1" as RS21 #Lime
component "Frontend Server 2.1" as FS21
RS21 -r- CN2
FS21 .r. RS21
}

package "School 2.2" {
component "Request Server 2.2" as RS22 #Lime
component "Frontend Server 2.2" as FS22
RS22 -r- CN2
FS22 .r. RS22
}

package "School 2.3" {
component "Request Server 2.3" as RS23 #Lime
component "Frontend Server 2.3" as FS23
RS23 -r- CN2
FS23 .r. RS23
}

package "School 3.1" {
component "Request Server 3.1" as RS31 #Lime
component "Frontend Server 3.1" as FS31
RS31 -r- CN3
FS31 .r. RS31
}

package "School 3.2" {
component "Request Server 3.2" as RS32 #Lime
component "Frontend Server 3.2" as FS32
RS32 -r- CN3
FS32 .r. RS32
}

package "School 3.3" {
component "Request Server 3.3" as RS33 #Lime
component "Frontend Server 3.3" as FS33
RS33 -r- CN3
FS33 .r. RS33
}

@enduml
```

Ở hệ thống này thì Chain Node sẽ do một bên được các sở tin tưởng (thường là Bộ Giáo Dục) để điều hành và thực hiện việc cài đặt Chain Node và chính các sở đó sẽ cấp giấy phép thao tác trên Chain Node cho các Request Server của các trường thuộc sở đó.

Hệ thống ở cấp độ này có thể được áp dụng ở các trường chính quy, khi việc cập nhật học bạ theo một quy trình chặt chẽ từ các sở cho đến trường. Đây cũng là hệ thống được tin cậy nhất để có thể sử dụng cho việc xét tuyển lên các trường trên theo hình thức trực tuyến vì học bạ ở cấp độ này được cả trường và sở giáo dục liên quan đảm bảo.

## Kết thúc

## Nguồn tham khảo

- [Giáo viên khốn khổ vì học bạ giấy](https://vnexpress.net/giao-vien-khon-kho-vi-hoc-ba-giay-4442649.html)
- [Học bạ giấy thời 4.0](https://vnexpress.net/hoc-ba-giay-thoi-4-0-4444060.html)
- [Có học bạ điện tử sao còn làm khó GV khi yêu cầu "bản sao học bạ công chứng"](https://giaoduc.net.vn/co-hoc-ba-dien-tu-sao-con-lam-kho-gv-khi-yeu-cau-ban-sao-hoc-ba-cong-chung-post226595.gd)