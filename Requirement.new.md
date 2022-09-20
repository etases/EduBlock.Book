# SRS

## System Architecture
* Without BlockChain
```{.plantuml caption="System architecture without BlockChain" width=50%}
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

* With BlockChain
```{.plantuml caption="System architecture with BlockChain" width=50%}
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

| Component       | Description                                                                                                                                                                                                                                      |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Chain Node (CN)      | A node of the blockchain. This stores the records and handles the history and transaction requests from the Request Server (Change/View the score, information, etc.)                                                                             |
| Trusted Record Service (TRS) | Similar to Chain Node, but this is a centralized & trusted (by all nodes) service that stores the records and handles requests from the Request Server |
| Request Server  | The off-chain backend of a CN / TRS. This stores the pending requests from the user and is the only way to call a request to the CN / TRS. Each Request Server may have a different way to handle user requests (Voting, Direct Request, etc.) |
| Frontend Server | Provide the UX/UI for interacting with the Request Server                                                                                                                                                                                        |