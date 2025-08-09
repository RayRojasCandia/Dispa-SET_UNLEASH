 ```mermaid
graph TB
    Title["Dispa-SET <br>GAMS Model"]:::A
    subgraph SG1[" "]
        direction LR
        A("Configuration<br>and<br>Solver Settings"):::C
        B("Definition<br>of the<br>Dataset<br>-<br>related options"):::C
        C("Definition<br>of<br>Sets and Parameters"):::C
        D("Data<br>import"):::C
        E("Definition<br>of<br>Variables"):::C
        F("Assignment<br>of<br>Initial Values"):::C
        G("Declaration<br>and<br>definition<br>of<br>Equations"):::C
        H("Definition<br>of<br>Model"):::C
        I("Solving<br>Loop"):::C
        J("Result<br>Export"):::C
        A --> B --> C --> D --> E --> F --> G --> H --> I --> J
    end

    Title --> SG1
    
classDef A fill:#004C99,stroke:#004C99,stroke-width:2px,color:white,font-weight:bold,font-size:30px;
classDef B fill:#004C99,stroke:#004C99,stroke-width:2px,color:white;
classDef C fill:#003366,stroke:#003366,stroke-width:2px,color:white,font-weight:bold,font-size:25px
classDef D fill:#003366,stroke:#003366,stroke-width:2px,color:white,font-weight:bold,font-size:15px

class SG1 B;
```

 ```mermaid
graph TB
    Title(["Start<br>Configuration and Solver Settings"]):::A
    subgraph SG1[" "]
        direction LR
    A2[Model Title:<br>UCM model]:::C
    A2 --> A3[Set End-of-Line Comment:<br>//]:::C
    A3 --> A4[Turn Off Empty Sets Display<br>\$offempty]:::C

    A4 --> A5{Performance Settings}:::C
    A5 --> A6[Threads = 16<br>Parallel Processing]:::C
    A5 --> A7[Iteration Limit = 1B<br>Max Iterations]:::C
    A5 --> A8[Resource Limit = 10B<br>Max Time/Memory]:::C
    A5 --> A9[Optimal Tolerance = 0.0<br>Exact Solutions]:::C

    A6 --> A10{Output Control}:::C
    A7 --> A10
    A8 --> A10
    A9 --> A10

    A10 --> A11[Listing Control<br>\$offlisting]:::C
    A10 --> A12[Log Control<br>\$offlog]:::C
    A10 --> A13[Symbol Cross-Reference<br>\$offsymxref]:::C
    A10 --> A14[Symbol List<br>\$offsymlist]:::C

    A11 --> A15[Reduce .lst File Size]:::C
    A12 --> A15
    A13 --> A15
    A14 --> A15

    A15 --> A16{Display Options}:::C
    A16 --> A17[limrow = 0<br>No Equation Listing]:::C
    A16 --> A18[limcol = 0<br>No Variable Listing]:::C
    A16 --> A19[solprint = off<br>No Solution Output]:::C
    A16 --> A20[sysout = off<br>No System Output]:::C

    A17 --> A21{Solver Selection}:::C
    A18 --> A21
    A19 --> A21
    A20 --> A21

    A21 --> A22[Solver = Gurobi<br>Commercial Optimizer]:::C


end

    Title --> A2
        A22 --> A23([End]):::C
    
classDef A fill:#004C99,stroke:#004C99,stroke-width:2px,color:none,font-weight:bold,font-size:20px;
classDef B fill:#004C99,stroke:#004C99,stroke-width:2px,color:none;
classDef C fill:#003366,stroke:#003366,stroke-width:2px,color:none,font-weight:bold,font-size:15px
classDef D fill:#003366,stroke:#003366,stroke-width:2px,color:none,font-weight:bold,font-size:15px

class SG1 B;
```

 ```mermaid
graph TD
    Title(["Start<br>Definition of the Dataset - related options"]):::A

    subgraph SG1[" "]
        direction TB

    B2 -->|Default| B3[Input.gdx]:::C
    B2 -->|Alternative| B4[Inputs.gdx]:::C

    B3 --> B5{LP Formulation}:::C
    B4 --> B5

    B5 -->|1| B6[Linear Programming<br>Mode]:::C
    B5 -->|0| B7[Mixed Integer Programming Mode]:::C

    B6 --> B8{Mid Term Sheduling<br>MTS}:::C
    B7 --> B8

    B8 -->|1| B9[MTS Activated]:::C
    B8 -->|0| B10[MTS Deactivated]:::C

    B9 --> B11{Retrieve Status<br>RetrieveStatus}:::C
    B10 --> B11

    B11 -->|1| B12[Status Retrieval ON]:::C
    B11 -->|0| B13[Status Retrieval OFF]:::C

    B12 --> B14{Flexible Demand<br>ActivateFlexibleDemand}:::C
    B13 --> B14

    B14 -->|1| B15[Flexible Demand ON]:::C
    B14 -->|0| B16[Flexible Demand OFF]:::C

    B15 --> B17{Advanced Reserves<br>ActivateAdvancedReserves}:::C
    B16 --> B17

    B17 -->|1| B18[Advanced Reserves ON]:::C
    B17 -->|0| B19[Advanced Reserves OFF]:::C

    B18 --> B20{Frequency Constrained<br>FC}:::C
    B19 --> B20

    B20 -->|1| B21[FC-UC/OD Mode<br>Frequency Constrained]:::C
    B20 -->|0| B22[Standard UC/OD Mode]:::C

end

    Title --> B2{Input File<br>InputFileName}:::C
    B21 --> B23([End]):::C
    B22 --> B23
    
classDef A fill:#004C99,stroke:#004C99,stroke-width:2px,color:none,font-weight:bold,font-size:20px;
classDef B fill:#004C99,stroke:#004C99,stroke-width:2px,color:none;
classDef C fill:#003366,stroke:#003366,stroke-width:2px,color:none,font-weight:bold,font-size:15px
classDef D fill:#003366,stroke:#003366,stroke-width:2px,color:none,font-weight:bold,font-size:15px

class SG1 B;
class AA B;
class BB B;
class CC B;

%% Style the edge labels
linkStyle 0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28 color:#none,stroke:#none,stroke-width:1px;
```

 ```mermaid
graph TD
    Title(["Start<br>Definition of Sets and Parameters"]):::A
    Title --> C3[Define Sets]:::C
    
    subgraph SG1[" "]
        direction TB

    %% Sets Section

    C3 --> C3A["Markets<br>Units<br>Fuels<br>Technologies<br>Nodes<br>Lines<br>Simulation"]:::C
    
    C3A--> C4[Create Aliases]:::C
        end
        
    %% Parameters Section Header
        subgraph SG2[" "]
    C4 --> C5[Define Parameters]:::C
    
    %% Basic Operational Parameters
    C5 --> C6[Basic Operational & Economic Parameters]:::C
    
    %% Boundary Sector Parameters
    C6 --> C7[Boundary Sector Parameters]:::C
    
    %% Conditional MTS for Boundary Sector
    C7 --> C8{%MTS% == 0?}:::C
    C8 -- Yes --> C9[SectorXStorageInitial]:::C
    C8 -- No --> C10[Storage & Charging Parameters]:::C
    C9 --> C10
    
    %% Storage & Charging
    C10 --> C11[Flexible Demand & Warm-Start Parameters]:::C
    
    %% Conditional RetrieveStatus
    C11 --> C12{%RetrieveStatus% == 1?}:::C
    C12 -- Yes --> C13[CommittedCalc Parameters]:::C
    C12 -- No --> C14[Reserve & Frequency Parameters]:::C
    C13 --> C14
    
    %% Conditional MTS for Reserve
    C14 --> C15{%MTS% == 0?}:::C
    C15 -- Yes --> C16[Frequency Parameters]:::C
    C15 -- No --> C17[Network Data Section]:::C
    C16 --> C17
    
    %% Network Data (PTDF)
    C17 --> C18[Power Transfer Distribution Factors:<br>PTDF Matrix]:::C
    
    %% Loop Parameters
    C18 --> C19[Parameters Used Within Loop]:::C
    
    %% Conditional MTS for Loop Parameters
    C19 --> C20{%MTS% == 0?}:::C
    C20 -- Yes --> C21[SectorXStorageFinalMin]:::C
    C20 -- No --> C22[Flexible Demand Parameters]:::C
    C21 --> C22
    
    %% Final Scalars
    C22 --> C23[Scalars for Simulation Control]:::C
    end
    
    C23 --> C24([End]):::C
    
classDef A fill:#004C99,stroke:#004C99,stroke-width:2px,color:none,font-weight:bold,font-size:20px;
classDef B fill:#004C99,stroke:#004C99,stroke-width:2px,color:none;
classDef C fill:#003366,stroke:#003366,stroke-width:2px,color:none,font-weight:bold,font-size:15px
classDef D fill:#004C99,stroke:#none,stroke-width:2px,color:none,font-weight:bold,font-size:15px

class SG1 B;
class SG2 B;
class SG3 D;
class CC B;

%% Style the edge labels
linkStyle 0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25 color:#none,stroke:#none,stroke-width:1px;
```