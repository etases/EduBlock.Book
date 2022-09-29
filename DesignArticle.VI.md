---
title: "Design Article (VI)"
subtitle: "Bước đầu thực hiện số hóa hoàn toàn học bạ ở Việt Nam"
---

## Giới thiệu

Các tổ chức lớn hiện đang áp dụng các thành tựu hiện đại của duy trì hồ sơ điện tử, tuy vậy hầu hết các tổ chức học thuật chủ yếu là các tổ chức học thuật thuộc nhà nước vẫn còn dựa vào các quy trình thủ công để lưu trữ và chuyển giao hồ sơ như bảng điểm và chứng chỉ giữa các cơ sở và cho các nhà tuyển dụng tiềm năng. Ngay cả học sinh khi có nhu cầu được xem xét học bạ thì quy trình cũng đã có thể đến vài ngày, vậy nên việc chuyển trường điển hình của một học sinh thì sẽ mất khoảng tầm vài tuần cho đến tháng, nghiêm trọng hơn những sai sót có thể xảy ra và những yêu cầu phúc khảo có thể kéo dài vài tháng với thời gian xử lý và gửi bằng phương pháp giấy được áp dụng rộng rãi. Ngoài ý nghĩa thời gian chờ đợi và cơ hội cho thiệt hại vật chất hoặc mất mát hồ sơ trong quá trình lưu trữ trình, vận chuyển cũng có nguy cơ bị giả mạo thông tin xác thực bởi các bên lừa đảo. Việc lưu trữ và vận chuyển bằng hồ sơ vật lý cũng đi kèm với chi phí cao liên quan đến thời gian xử lý, nỗ lực làm việc thủ công, phí bưu điện và chuyển tuyến. 

Các giải pháp mới ra đời chủ yếu dựa vào Email based solutions, PDF record transfers trong khi vẫn tồn tại các giới hạn nationality barriers, riêng tư và bảo mật. Mặc dù Blockchain nổi lên như một trào lưu về các ứng dụng trong lĩnh vực tài chính qua sự phổ biến của đồng BitCoin và các tiền điện tử, NFT, lĩnh vực này đa dạng hơn nhiều cả về kỹ thuật và về các lĩnh vực ứng dụng được giải quyết [1]. Tuy , các ứng dụng phân tán ngày càng được áp dụng vào nhiều lĩnh vực khác nhau như lưu trữ dữ liệu including handling medical records and healthcare [2,5]), Cloud and Grid Computing [3], e-vote [4], Service for IoT[6], Banking system[7] and foremost is the field of Education. Các mô hinh giải pháp lưu trữ và chống gian lận bằng cấp online cũng đã được lên ý tưởng mang lại những lợi ích ban đầu của việc áp dụng công nghệ Blockchain [8][9]. While these solutions provide a more modern approach to the storage and the transfer of academic records, there are still limitations in terms of widespread adoption, auditability, and scalability. Các tổ chức học thuật có thể được hưởng lợi từ blockchain công nghệ để cung cấp một sổ cái phi tập trung và bất biến để xác nhận tính toàn vẹn của hồ sơ học tập [10]. Một giải pháp lưu trữ và trao đổi học bạ điện tử thành công sẽ bao gồm tính Security and Privacy, Scalability và đồng thời hưởng lợi từ các ưu điểm của công nghệ blockchain Sự phân tán, Sự minh bạch, further described in Section II.

Mục tiêu của hệ thống được đề xuất của chúng tôi là giải quyết những hạn chế của các giải pháp hiện có bằng cách cung cấp một phương pháp bảo mật, có thể xác minh và truy vết nhằm chống giả mạo để lưu trữ,truy cập, quản lý và trao đổi học bạ điện tử giữa các tổ chức sử dụng công nghệ blockchain. Phần II thảo luận về các công nghệ liên quan. Giải pháp và thiết kế  đề xuất của chúng tôi được trình bày trong Phần III. Cuối cùng, Phần IV đưa ra những nhận xét kết luận.


## Công nghệ

Xét về các giải pháp số hóa học bạ, thì những năm gần đây đã có các giải pháp để quản lý và lưu trữ học bạ trực tuyến. Bất lợi lớn nhất của các giải pháp trên là sự tập trung của dữ liệu nên sẽ ảnh hưởng lớn nếu hệ thống bị sập dẫn đến mất dữ liệu, ngoài ra còn độ tin cậy của dữ liệu học bạ khi học bạ đó được một bên thứ ba lưu trữ.

Một trong những thành tựu của ngành lưu trữ trực tuyến là việc phát minh ra BlockChain. Đây là một dạng cơ sở dữ liệu phân tán, trong đó dữ liệu được lưu trong một khối và kết nối các khối theo chuỗi bằng cơ chế hashing [11]. Nếu xét riêng về giải pháp số hóa học bạ, BlockChain có những ưu điểm sau [12]:

- Sự phân tán: Dữ liệu được bảo toàn ở nhiều máy thành viên tham gia mạng lưới BlockChain. Khi bị mất dữ liệu thì có thể khôi phục từ các máy thành viên.

- Sự minh bạch: Cơ chế hashing giúp dữ liệu trong một khối sẽ được xác minh bởi các khối khác, tạo nên sự không thể bị thay đổi của dữ liệu. Cho nên, dữ liệu trên mạng lưới BlockChain là dữ liệu đã được xác minh, không thể bị phá hủy, không thể bị làm giả, nên có sự rõ ràng minh bạch và có thể tin tưởng.

- Không can thiệp của bên thứ ba: Dữ liệu được xác minh và lưu trữ bởi các thành viên tham gia mạng lưới, khác với các giải pháp truyền thông khi phải phụ thuộc vào một bên thứ ba để tin tưởng làm nơi lưu trữ.

Để các giao dịch diễn ra trên mạng BlockChain, ta có cơ chế Smart Contract. Đây là một bộ quy tắc được lập trình sẵn để quy định các điều kiện và trình tự thực thi một giao dịch trên mạng BlockChain, được kí bởi các bên liên quan, xác minh bởi các thành viên trong mạng lưới và không có sự can thiệp của bên thứ ba. Nó được dùng để xử lí dữ liệu trên mạng lưới, đồng thời cũng đặt điều kiện giới hạn việc thực thi thao tác trên dữ liệu trên mạng lưới. Nó là một chương trình tự chạy trên mạng BlockChain nên nó có tính minh bạch [13]. 

Một đặc điểm quan trọng khác của một hệ thống quản lí học bạ là sự riêng tư của lý lịch học sinh trên học bạ, điều này buộc các hệ thống phải có tính năng phân quyền để chỉ những người được cấp quyền mới được xem thông tin học sinh trên học bạ. Với BlockChain, có một số dự án mã nguồn mở để thực hiện xây dựng các tính chất trên. Một trong số đó là Hyperledger Fabric. Đây là một dự án mã nguồn mở (từ chuỗi dự án Hyperledger) về BlockChain riêng tư (Private) và có phân quyền (Permissioned) [14]. Khác với các BlockChain mở như BitCoin hay Etherium, khi mà ai cũng có thể tham gia và thực hiện giao dịch, các thành viên trong mạng lưới Fabric được đăng kí xác nhận từ Nhà cung cấp dịch vụ thành viên (Membership Service Provider) và cơ chế Smart Contract của Fabric có thể mở rộng để giới hạn quyền truy cập và xử lí dữ liệu của các thành viên được đăng kí trong mạng lưới. Một ví dụ về việc áp dụng Hyperledger Fabric trong lưu trữ có thể nói là Sony Global Education khi họ chọn để thực hiện hệ thống lưu trữ bằng cấp, mà có thể giới hạn quyền truy cập dữ liệu cho các bên liên quan [15]. Với giải pháp số hóa học bạ, ta có thể gửi thông tin cá nhân và học bạ của học sinh lên mạng lưới và giới hạn quyền truy cập và sửa chữa học bạ cho chỉ trường chứa học sinh đó. Ta cũng có thể tạo một tính năng chỉ xuất điểm từ các học bạ được lưu trên mạng lưới để thực hiện việc thống kê và phân tích.

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

[1] M. Walport, Distributed ledger technology: Beyond blockchain, UK Government Office for Science (2016).

[2] Duong-Trung, N., Son, H. X., Le, H. T., & Phan, T. T. (2020). Smart Care. Proceedings of the 2020 4th International Conference on Cryptography, Security and Privacy. https://doi.org/10.1145/3377644.3377667 

[3] Liang, Xueping & Shetty, Sachin & Tosh, Deepak & Kamhoua, Charles & Kwiat, Kevin & Njilla, Laurent. (2017). ProvChain: A Blockchain-Based Data Provenance Architecture in Cloud Environment with Enhanced Privacy and Availability. 10.1109/CCGRID.2017.8. 

[4] Vanita Jain, Akanshu Raj & Abhishek Tanwar & Mridul Khurana. “eVote – A Decentralized Voting Platform”. Digital Twin Technology, CRC Press, 2021.

[5] Mettler, M. (2016). Blockchain technology in healthcare: The revolution starts here. 2016 IEEE 18th International Conference on e-Health Networking, Applications and Services (Healthcom). doi:10.1109/healthcom.2016.7749510 

[6] Samaniego, M., & Deters, R. (2016). Blockchain as a Service for IoT. 2016 IEEE International Conference on Internet of Things (iThings) and IEEE Green Computing and Communications (GreenCom) and IEEE Cyber, Physical and Social Computing (CPSCom) and IEEE Smart Data (SmartData). doi:10.1109/ithings-greencom-cpscom-smartdata.2016.102 

[7] Chowdhury, M. , Suchana, K. , Alam, S. and Khan, M. (2021) Blockchain Application in Banking System. Journal of Software Engineering and Applications, 14, 298-311. doi: 10.4236/jsea.2021.147018.

[8] Ghaffar, A., & Hussain, M. (2019). BCEAP - A Blockchain Embedded Academic Paradigm to Augment Legacy Education through Application. Proceedings of the 3rd International Conference on Future Networks and Distributed Systems  - ICFNDS  ’19. doi:10.1145/3341325.3342036 

[9] Vidal, F. R., Gouveia, F., & Soares, C. (2020). Revocation Mechanisms for Academic Certificates Stored on a Blockchain. 2020 15th Iberian Conference on Information Systems and Technologies (CISTI). doi:10.23919/cisti49556.2020.9141088 

[10] M. Sharples and J. Domingue, "The Blockchain and Kudos: A Distributed System for Educational Record, Reputation and Reward," in 11th European Conference on Technology Enhanced Learning, Lyon, France, 2016. 

[11] Nofer, M., Gomber, P., Hinz, O., & Schiereck, D. (2017). Blockchain. Business & Information Systems Engineering, 59(3), 183–187. doi:10.1007/s12599-017-0467-3 

[12] Lu, Y. (2019). The Blockchain: State-of-the-Art and Research Challenges. Journal of Industrial Information Integration. doi:10.1016/j.jii.2019.04.002 

[13] Singh, A., Parizi, R. M., Zhang, Q., Choo, K.-K. R., & Dehghantanha, A. (2019). Blockchain Smart Contracts Formalization: Approaches and Challenges to Address Vulnerabilities. Computers & Security, 101654. doi:10.1016/j.cose.2019.101654  

[14] Androulaki, E., Manevich, Y., Muralidharan, S., Murthy, C., Nguyen, B., Sethi, M., … Laventman, G. (2018). Hyperledger fabric. Proceedings of the Thirteenth EuroSys Conference on   - EuroSys  ’18. doi:10.1145/3190508.3190538 

[15] “Sony Global Education Develops Technology Using Blockchain for Open Sharing of Academic Proficiency and Progress Records”. Sony Group Portal - Sony Global Headquarters, http://www.sony.com/en/SonyInfo/News/Press/201602/16-0222E/index.html.

