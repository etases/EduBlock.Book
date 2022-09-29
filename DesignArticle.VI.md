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

Xét về các giải pháp số hóa học bạ, thì những năm gần đây đã có các giải pháp để quản lý và lưu trữ học bạ trực tuyến. Bất lợi lớn nhất của các giải pháp trên là sự tập trung của dữ liệu nên sẽ ảnh hưởng lớn nếu hệ thống bị sập dẫn đến mất dữ liệu, ngoài ra còn độ tin cậy của dữ liệu học bạ khi học bạ đó được một bên thứ ba lưu trữ.

Một trong những thành tựu của ngành lưu trữ trực tuyến là việc phát minh ra BlockChain. Đây là một dạng cơ sở dữ liệu phân tán, trong đó dữ liệu được lưu trong một khối và kết nối các khối theo chuỗi bằng cơ chế hashing. Nếu xét riêng về giải pháp số hóa học bạ, BlockChain có những ưu điểm sau:

- Sự phân tán: Dữ liệu được bảo toàn ở nhiều máy thành viên tham gia mạng lưới BlockChain. Khi bị mất dữ liệu thì có thể khôi phục từ các máy thành viên.

- Sự minh bạch: Cơ chế hashing giúp dữ liệu trong một khối sẽ được xác minh bởi các khối khác, tạo nên sự không thể bị thay đổi của dữ liệu. Cho nên, dữ liệu trên mạng lưới BlockChain là dữ liệu đã được xác minh, không thể bị phá hủy, không thể bị làm giả, nên có sự rõ ràng minh bạch và có thể tin tưởng.

- Không can thiệp của bên thứ ba: Dữ liệu được xác minh và lưu trữ bởi các thành viên tham gia mạng lưới, khác với các giải pháp truyền thông khi phải phụ thuộc vào một bên thứ ba để tin tưởng làm nơi lưu trữ.

Để các giao dịch diễn ra trên mạng BlockChain, ta có cơ chế Smart Contract. Đây là một bộ quy tắc được lập trình sẵn để quy định các điều kiện và trình tự thực thi một giao dịch trên mạng BlockChain, được kí bởi các bên liên quan, xác minh bởi các thành viên trong mạng lưới và không có sự can thiệp của bên thứ ba. Nó được dùng để xử lí dữ liệu trên mạng lưới, đồng thời cũng đặt điều kiện giới hạn việc thực thi thao tác trên dữ liệu trên mạng lưới. Nó là một chương trình tự chạy trên mạng BlockChain nên nó có tính minh bạch.

Một đặc điểm quan trọng khác của một hệ thống quản lí học bạ là sự riêng tư của lý lịch học sinh trên học bạ, điều này buộc các hệ thống phải có tính năng phân quyền để chỉ những người được cấp quyền mới được xem thông tin học sinh trên học bạ. Với BlockChain, có một số dự án mã nguồn mở để thực hiện xây dựng các tính chất trên. Một trong số đó là Hyperledger Fabric. Đây là một dự án mã nguồn mở (từ chuỗi dự án Hyperledger) về BlockChain riêng tư (Private) và có phân quyền (Permissioned). Khác với các BlockChain mở như BitCoin hay Etherium, khi mà ai cũng có thể tham gia và thực hiện giao dịch, các thành viên trong mạng lưới Fabric được đăng kí xác nhận từ Nhà cung cấp dịch vụ thành viên (Membership Service Provider) và cơ chế Smart Contract của Fabric có thể mở rộng để giới hạn quyền truy cập và xử lí dữ liệu của các thành viên được đăng kí trong mạng lưới. Một ví dụ về việc áp dụng Hyperledger Fabric trong lưu trữ có thể nói là [Sony Global Education](https://www.hyperledger.org/wp-content/uploads/2017/12/Hyperledger_CaseStudy_Sony.pdf) khi họ chọn để thực hiện hệ thống lưu trữ bằng cấp, mà có thể giới hạn quyền truy cập dữ liệu cho các bên liên quan. Với giải pháp số hóa học bạ, ta có thể gửi thông tin cá nhân và học bạ của học sinh lên mạng lưới và giới hạn quyền truy cập và sửa chữa học bạ cho chỉ trường chứa học sinh đó. Ta cũng có thể tạo một tính năng chỉ xuất điểm từ các học bạ được lưu trên mạng lưới để thực hiện việc thống kê và phân tích.

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
actor "Requester" as Requester
participant "Frontend Server" as Frontend
participant "Request Server" as Backend
participant "Trusted Record Service" as Record

== Get student record ==

Requester -> Frontend: Send request with conditions
activate Frontend
Frontend -> Backend: Send request with conditions
activate Backend
Backend -> Record: Send request
activate Record
Record --> Backend: Response with relevant records
deactivate Record
Backend -> Backend: Filter records by conditions
Backend --> Frontend: Response with records
deactivate Backend
Frontend --> Requester: Display records on user interface
deactivate Frontend

== Request to edit records ==
Requester -> Frontend: Send request
activate Frontend
Frontend -> Backend: Send request
activate Backend
alt Valid request
  Backend -> Backend: Save as pending request
  Backend --> Frontend: Successful response
  Frontend --> Requester: Successful response
else Invalid request
  Backend --> Frontend: Invalid response
  Frontend --> Requester: Invalid response
end
deactivate Backend
deactivate Frontend
@enduml
```

```{.plantuml caption="Người xác minh" id="fig-rs-workflow-validator"}
@startuml
actor "Validator" as Validator
participant "Frontend Server" as Frontend
participant "Request Server" as Backend
participant "Trusted Record Service" as Record

== Get pending requests to edit records ==
Validator -> Frontend: Send request with conditions
activate Frontend
Frontend -> Backend: Send request with conditions
activate Backend
Backend -> Backend: Get from local database & Filter by conditions
Backend --> Frontend: Response with edit requests
deactivate Backend
Frontend --> Validator: Display edit requests in user interface
deactivate Frontend
== Validate requests to edit records ==
Validator -> Frontend: Send validation for edit request
activate Frontend
Frontend -> Backend: Send validation for edit request
activate Backend
Backend -> Backend: Remove request from local database
alt Accepted request
  Backend -> Backend: Save as validated request
end
Backend --> Frontend: Successful response 
deactivate Backend
Frontend --> Validator: Successful response
deactivate Frontend

loop times to upload to Record Service
activate Backend
Backend -> Backend: Create records from validated edit requests
Backend -> Record: Send records
Record --> Backend: Successful response
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
- [Sony Global Education](https://www.hyperledger.org/wp-content/uploads/2017/12/Hyperledger_CaseStudy_Sony.pdf)
- [BlockChain là gì?](https://topdev.vn/blog/blockchain-la-gi/)
- [The blockchain: State-of-the-art and research challenges](https://sci-hub.ru/https://www.sciencedirect.com/science/article/pii/S2452414X19300019)
- [What is Hyperledger Fabric](https://hyperledger-fabric.readthedocs.io/en/release-2.2/blockchain.html#what-is-hyperledger-fabric)