 ```mermaid
graph TB
    Title["**Dispa-SET GAMS Model**"]:::1

    subgraph SG1[" "]
        direction LR
        A("Configuration and Solver Settings"):::3
        B("Definition of the Dataset - related options"):::3
        C("Definition of Sets and Parameters"):::3
        D("Data import"):::3
        E("Definition of Variables"):::3
        F("Assignment of Initial Values"):::3
        G("Declaration and definition of Equations"):::3
        H("Definit of Model"):::3
        I("Solving Loop"):::3
        J("Result Export"):::3
        %%A --- B --- C --- D --- E --- F --- G --- H --- I --- J
    end

    subgraph AA[" "]
        direction TB
    A1([Start]) --> A2[Model Title: UCM model]
    A2 --> A3[Set End-of-Line Comment: //]
    A3 --> A4[Turn Off Empty Sets Display

$offempty]
    
    A4 --> A5{Performance Settings}
    A5 --> A6[Threads = 16

Parallel Processing]
    A5 --> A7[Iteration Limit = 1B

Max Iterations]
    A5 --> A8[Resource Limit = 10B

Max Time/Memory]
    A5 --> A9[Optimal Tolerance = 0.0

Exact Solutions]
    
    A6 --> A10{Output Control}
    A7 --> A10
    A8 --> A10
    A9 --> A10
    
    A10 --> A11[Listing Control

$offlisting]
    A10 --> A12[Log Control

$offlog]
    A10 --> A13[Symbol Cross-Reference

$offsymxref]
    A10 --> A14[Symbol List

$offsymlist]
    
    A11 --> A15[Reduce .lst File Size]
    A12 --> A15
    A13 --> A15
    A14 --> A15
    
    A15 --> A16{Display Options}
    A16 --> A17[limrow = 0

No Equation Listing]
    A16 --> A18[limcol = 0

No Variable Listing]
    A16 --> A19[solprint = off

No Solution Output]
    A16 --> A20[sysout = off

No System Output]
    
    A17 --> A21{Solver Selection}
    A18 --> A21
    A19 --> A21
    A20 --> A21
    
    A21 --> A22[Solver = Gurobi

Commercial Optimizer]
    
    A22 --> A23([End])
end

    subgraph BB[" "]
        direction TB
    B1([Start]) --> B2{Input File

InputFileName}
    B2 -->|Default| B3[Input.gdx]
    B2 -->|Alternative| B4[Inputs.gdx]
    
    B3 --> B5{LP Formulation

LPFormulation}
    B4 --> B5
    
    B5 -->|1| B6[Linear Programming

Mode]
    B5 -->|0| B7[Mixed Integer Programming

Mode]
    
    B6 --> B8{Multi Time Scale

MTS}
    B7 --> B8
    
    B8 -->|1| B9[MTS Activated]
    B8 -->|0| B10[MTS Deactivated]
    
    B9 --> B11{Retrieve Status

RetrieveStatus}
    B10 --> B11
    
    B11 -->|1| B12[Status Retrieval ON]
    B11 -->|0| B13[Status Retrieval OFF]
    
    B12 --> B14{Flexible Demand

ActivateFlexibleDemand}
    B13 --> B14
    
    B14 -->|1| B15[Flexible Demand ON]
    B14 -->|0| B16[Flexible Demand OFF]
    
    B15 --> B17{Advanced Reserves

ActivateAdvancedReserves}
    B16 --> B17
    
    B17 -->|1| B18[Advanced Reserves ON]
    B17 -->|0| B19[Advanced Reserves OFF]
    
    B18 --> B20{Frequency Constrained

FC}
    B19 --> B20
    
    B20 -->|1| B21[FC-UC/OD Mode

Frequency Constrained]
    B20 -->|0| B22[Standard UC/OD Mode]
    
    B21 --> B23([End])
    B22 --> B23
    end

    subgraph CC[" "]
        direction TB
        C0([Start]) --- C1[Definition of Sets]:::process
        
        %% Sets Definition
        C1 --> C2[Markets, Units, Fuels, Technologies]:::assignment
        C2 --> C3[Nodes and Lines]:::assignment
        C3 --> C4[Simulation Options]:::assignment
        C4 --> C5[Aliases]:::assignment
        
        %% Main Parameters
        C5 --> C6[Definition of Parameters]:::process
        C6 --> C7[Basic Operational & Economic Parameters]:::assignment
        C7 --> C8[Boundary Sector Parameters]:::assignment
        C8 --> C81{%MTS% == 0?}:::condition
        C81 -- Yes --> C82[SectorXStorageInitial Parameters]:::assignment
        C81 -- No --> C9[Storage & Charging Parameters]:::assignment
        C82 --> C9
        
        %% Storage Parameters
        C9 --> C10[Flexible Demand & Warm-Start Parameters]:::assignment
        
        %% Conditional Parameters - RetrieveStatus
        C10 --> C11[Conditional Parameters Based on Flags]:::process
        C11 --> C12{%RetrieveStatus% == 1?}:::condition
        C12 -- Yes --> C13[Unit Commitment Status]:::assignment
        C12 -- No --> C14[Reserve & Frequency Parameters]:::assignment
        C13 --> C14
        
        %% Conditional Parameters - MTS for Frequency
        C14 --> C15{%MTS% == 0?}:::condition
        C15 -- Yes --> C16[Frequency & Reserve Parameters]:::assignment
        C15 -- No --> C17["Network Data (PTDF)"]:::assignment
        C16 --> C17
        
        %% Loop Parameters
        C17 --> C18[Dynamic Limits & Costs]:::assignment
        C18 --> C19{%MTS% == 0?}:::condition
        C19 -- Yes --> C20[SectorXStorageFinalMin Parameters]:::assignment
        C19 -- No --> C21[Flexible Demand Parameters]:::assignment
        C20 --> C21
        
        %% Final Parameters
        C21 --> C22[Scalars & Constants]:::assignment
        
        C22 --> C99([End])
    end

    Title --- SG1
    A --- AA
    B --- BB
    C --- CC
    D --- DD
    E --- EE
    F --- FF
    G --- GG
    H --- HH
    I --- II
    J --- JJ

classDef 1 fill:#004C99,stroke:#004C99,stroke-width:2px,color:greew,font-weight:bold,font-size:32px;
classDef 2 fill:#004C99,stroke:#CCCCCC,stroke-width:2px,color:black;
classDef 3 fill:#003366,stroke:#003366,stroke-width:2px,color:greew,font-weight:bold,font-size:25px
classDef 4 fill:#003366,stroke:#003366,stroke-width:2px,color:greew,font-weight:bold,font-size:15px

class SG1 2;
class AA 2;
class BB 2;
class CC 2;