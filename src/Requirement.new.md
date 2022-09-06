# System Architecture
```plantuml
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

| Component | Description |
| --- | --- |
| Chain Node | A node of the blockchain. This stores the records and handle the history and transaction requests from the Request Server (Change/View the score, information, etc) |
| Request Server | The off-chain backend of a Chain Node. This stores the pending requests from the user and is the only way to call a request to the Chain Node. Each Request Server may have different ways to handle user requests (Voting, Direct Request, etc) |
| Frontend Server | Provide the UX/UI for interacting with the Request Server |