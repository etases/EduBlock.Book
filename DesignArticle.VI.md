---
title: "Design Article (VI)"
subtitle: "Bước đầu thực hiện số hóa hoàn toàn học bạ ở Việt Nam"
abstract: "Schools and departments are using modern technologies for storing and managing academic records digitally. However, the implementation is not consistent as many places still rely on traditional ways to proceed transcripts, and it has major problems like being centralized, third-party required, untraceable, untrustworthy, etc. This paper attempts to present an approach to the problem by listing the major characteristics of a reliable system; explain how and which Blockchain technologies, especially Hyperledger Fabric, can be applied to the situation; and provide three concepts: a centralized system, a multi-school network using Blockchain, and a multiple school-department one that expands the multi-school one and gives the storage and management to departments of education. This paper will be used as a foundation for similar topics and products to implement the concepts."
keywords: ["Academic record", "Blockchain", "Hyperledger Fabric"]
---

## Introduction

The number of academic institutions still use manual processes to store and transfer academic records like transcripts and certifications between institutions and to potential organizations, despite the fact that many large institutions are now adopting the modern practice of maintaining electronic academic records.The process can take up to several days, just for students who want to review their own transcripts, so a common transfer for a student can take anywhere from a few weeks to a month. Due to the time required to process and submit appeal requests using the widely used paper method, more serious errors could happen and the process could take several months. In addition to the significant wait time and the possibility of physical damage or loss of records during storage and transportation, there is also the risk of credential tampering by fraudulent parties. The cost of processing time, manual work effort, postage, and transit fees, as well as the storage and shipping of physical records, are also very expensive.

The emerging solutions are primarily based on email-based solutions or the transfer of PDF files while remaining limited by nationality, privacy and security barriers. Although the popularity of cryptocurrencies and NFTs has led to the implementation of Blockchain as a host of applications in the financial sector, the field is more diverse in both technical and application areas [1]. As distributed applications are increasingly applied in various fields such as data storage (including handling medical records and healthcare [2,5]), Cloud and Grid Computing [3], e-vote [4] , Service for IoT [6], Banking system[7] and foremost is the field of Education. Academic institutions can benefit from blockchain technology to provide a decentralized and immutable ledger to confirm the integrity of academic records [10]. Then, solutions for storing and anti-fraud of online electronic degrees have also been conceived to bring the initial benefits of applying Blockchain technology [8][9]. While these solutions provide a more modern approach to the storage and the transfer of academic records, there are still limitations in terms of widespread adoption, auditability, and scalability. A successful solution for storing and exchanging electronic school records will include Security and Privacy, Scalability and at the same time benefit from the advantages of blockchain technology as Distributed, Transparency further described in Section II.

The goal of our proposed system is to address the limitations of existing solutions by utilizing Blockchain technology to provide a secure, verifiable, and tamper-proof method of storing, accessing, managing, and exchanging electronic school records between institutions. Part II will go over the technologies involved. Part III presents our proposed solution and design, and Section IV provides concluding remarks.


## State of the art

In terms of digital solutions, in recent years, there have been technologies to manage and store academic records digitally. The biggest disadvantage of the above solutions is the centralization of data, so it will have a big impact if the system crashes, leading to data loss, in addition to the reliability of the data when it is stored by a third party.

One of the achievements of the online storage industry is the invention of Blockchain. This is a form of distributed database in which data is stored in a block and connects the blocks in a chain by hashing mechanism [11]. If we consider the solution of digitizing academic records alone, Blockchain has the following advantages [12]:

- Decentralized: Data is preserved in many member machines participating in the network. When data is lost, it can be restored from member computers.

- Transparency: The hashing mechanism makes the data in one block verified by other blocks, making the data immutable. Therefore, the data on the Blockchain network is verified, indestructible, and cannot be faked, so it has clarity, transparency, and can be trusted.

- No third party interference: Data is verified and stored by network members, different from traditional solutions when having to depend on a trusted third party as a storage place.

For transactions to take place on the Blockchain network, we have a Smart Contract mechanism. This is a pre-programmed set of rules to regulate the conditions and order of execution of a transaction on the Blockchain network, signed by the parties involved, verified by the members of the network, and without interference of third parties. It is used to process data on the network, and also set conditions that limit the execution of operations on data on the network. It is a self-run program on the Blockchain network so it is transparent [13]. 

Another important feature of a record management system is the privacy of students' personal information, which forces systems to have an authorization feature so that only authorized persons can view student information on transcripts. With Blockchain, there are a number of open source projects to implement the above properties. One of them is Hyperledger Fabric. This is an open-source project from the Hyperledger series about private and permissioned Blockchain. [14]. Unlike public Blockchains like Bitcoin or Etherium, where anyone can participate and make transactions, Fabric network members are registered for attention from a Member Service Provider. The Smart Contract mechanism is extensible to limit the access and data processing rights of members registered in the network. An example of applying Hyperledger Fabric in education storage can be said to be Sony Global Education when they choose to implement a cetification archiving system, which can limit data access for stakeholders [15]. For a solution to digitalize records, we can post a student's personal information and transcripts online and limit access to and edit records to only the school where the student resides. We can also create a feature that only exports grades from records stored on the network for statistics and analysis.

## Approach & Concept

### Centralized

```{.plantuml caption="A centralized system" id="fig-overview"}
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

@fig-overview is an overview of our solution, represented as a centralized system, including:

*   Trusted Record Service (TRS)
    
    This is the center of the system, which will store the records that have been verified by the schools, and the revision history of each record. This center must be trusted by members of the system.
    
    Only schools participating in the system can access the center to get records, and only schools associated with the record are authorized to get background information and submit a request to update and correct them.

*   Request Server (RS)
    
    Each school in the system will be assigned a server to operate on the TRS, which contains a license indicating the school's identity and the permissions in the TRS.

    This is also the place to save the transcripts being edited and handle correction requests from users (teachers, students, etc.), including verifying the validity and accuracy of such correction requests, generating a complete transcript from valid requests to submit to the TRS with the license.

    Schools may have different ways of verifying the request for editing records, depending on the specificity of each one. Therefore, the Request Server of a school may be different, but the operation on TRS is the same because the verified transcript must be sent with a license from that school.

*   Frontend Server (FS)

  	This is the interactive server for the RS to retrieve, display the school records and send a request to edit the records on an easy-to-see, easy-to-interact interface. It can be part of the management page of the school.

  	Since the RS of each school may be different, the interface of the FS may also be different to adapt to the specifics of that school.

The workflow of the system is shown in @fig-rs-workflow

::: {#fig-rs-workflow layout-ncol=1}

```{.plantuml caption="From requester-view" id="fig-rs-workflow-requester"}
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

```{.plantuml caption="From validator-view" id="fig-rs-workflow-validator"}
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

The sequence diagram of the system
:::
"Requester" is the student or teacher, and "Validator" is the homeroom teacher representing the school associated with the record requested to be edited in the Request Server.

### Decentralized & Multiple schools

```{.plantuml caption="A decentralized system with multiple schools" id="fig-decentralized"}
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

We can extend the system by applying decentralized data technology. Specifically, we can split Trusted Record Service into Chain Nodes and leave Chain Nodes for Schools like @fig-decentralized. Now a Chain Node that receives a request to edit records from the Request Server will not only store it on that Chain Node, but will also send that request to neighboring Chain Nodes for storage.

This level is often used in private school systems that do not follow the formal school procedures according to the Department of Education, so the authority of the schools is equivalent.

A system at this level will ensure the security & persistency of academic record data in case a school's Chain Node goes down. If then, we can use the license from the Request Server to the neighboring Chain Nodes to retrieve the data to restore the collapsed Chain Node. However, the disadvantage is that each Chain Node will have to store a large amount of data from not only the school holding that Chain Node but also the data of neighboring Chain Nodes.

### Mutiple departments

We can level up the system to an inter-departmental scale so that each Chain Node will be maintained by each educational department like @fig-department.

```{.plantuml caption="A inter-departmental decentralized system" id="fig-department"}
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

In this system, the Chain Node will be initilized by a party trusted by the departments (usually the Ministry of Education), and those departments will issue licenses to operate on the Chain Node to the Request Server of schools belonging to that department.

The system at this level can be applied in regular schools, where the update of records follows a strict process from departments to schools. This is also the most trusted system that can be used for online admission to the above schools because records at this level are guaranteed by both the school and the relevant educational department.

## Conclusion 
In this study, we presented a solution for managing and storing electronic academic records as a replacement for the traditional academic record based on distributed storage technology used by Blockchain, where the data is stored in a block and the blocks are connected on a chain by hashing.Our network enables us to manage data in the network using transactions via smart contracts. From there next, we show how to set up a multi-tier network and processes.  Our network enables us to decentralize organizations and system users through arranging chain nodes, verifying transactions with smart contracts, archiving modification history and restoring data of a node using data from other nodes.

From this design, it can be concluded and proposed to organize a Permissioned Blockchain network with a multi-tier design. The main advantage of applying Permissioned Blockchain technology is its resistance to many threats and cyber attacks, rely on the hashing mechanism and the nodes on the Blockchain can prevent data breaches. And moreover, it offers a host of unique features such as improved reliability, better fault tolerance, faster and more efficient operation, and scalability.

And thus, the management of documents for the field of education has the potential to be significantly impacted by the integration of Blockchain, the hyperledger framework, and smart contract technologies across academic records.


## Nguồn tham khảo

[1] M. Walport, Distributed ledger technology: Beyond Blockchain, UK Government Office for Science (2016).

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

