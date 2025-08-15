```python

```

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

```python

```

 ```mermaid
graph TB
    Title(["Start<br>Configuration and Solver Settings"]):::A
    subgraph SG1[" "]
        direction LR
    A2[Model Title:<br>UCM model]:::C
    A2 --> A3[Set End-of-Line Comment:<br>//]:::C
    A3 --> A4[Turn Off Empty Sets Display<br>\$offempty]:::C

    A4 --> A5{Performance<br>Settings}:::C
    A5 --> A6[Threads = 16<br>Parallel Processing]:::C
    A5 --> A7[Iteration Limit = 1B<br>Max Iterations]:::C
    A5 --> A8[Resource Limit = 10B<br>Max Time/Memory]:::C
    A5 --> A9[Optimal Tolerance = 0.0<br>Exact Solutions]:::C

    A6 --> A10{Output<br>Control}:::C
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

    A15 --> A16{Display<br>Options}:::C
    A16 --> A17[limrow = 0<br>No Equation Listing]:::C
    A16 --> A18[limcol = 0<br>No Variable Listing]:::C
    A16 --> A19[solprint = off<br>No Solution Output]:::C
    A16 --> A20[sysout = off<br>No System Output]:::C

    A17 --> A21{Solver<br>Selection}:::C
    A18 --> A21
    A19 --> A21
    A20 --> A21

    A21 --> A22[Solver = Gurobi<br>Commercial Optimizer]:::C


end

    Title --> A2
        A22 --> A23([End]):::C
    
classDef A fill:#004C99,stroke:#004C99,stroke-width:2px,color:none,font-weight:bold,font-size:20px;
classDef B fill:#004C99,stroke:#004C99,stroke-width:2px,color:none;
classDef C fill:#003366,stroke:#003366,stroke-width:2px,color:none,font-weight:bold,font-size:10px
classDef D fill:#003366,stroke:#003366,stroke-width:2px,color:none,font-weight:bold,font-size:10px

class SG1 B;
```


```python

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

    B9 --> B11{Retrieve Status}:::C
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
classDef C fill:#003366,stroke:#003366,stroke-width:2px,color:none,font-weight:bold,font-size:10px
classDef D fill:#003366,stroke:#003366,stroke-width:2px,color:none,font-weight:bold,font-size:10px

class SG1 B;
class AA B;
class BB B;
class CC B;

%% Style the edge labels
linkStyle 0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28 color:#none,stroke:#none,stroke-width:1px;
```


```python

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
    C7 --> C8{MTS = 0?}:::C
    C8 -- Yes --> C9[SectorXStorageInitial]:::C
    C8 -- No --> C10[Storage & Charging Parameters]:::C
    C9 --> C10
    
    %% Storage & Charging
    C10 --> C11[Flexible Demand & Warm-Start Parameters]:::C
    
    %% Conditional RetrieveStatus
    C11 --> C12{RetrieveStatus<br>= 1?}:::C
    C12 -- Yes --> C13[CommittedCalc Parameters]:::C
    C12 -- No --> C14[Reserve & Frequency Parameters]:::C
    C13 --> C14
    
    %% Conditional MTS for Reserve
    C14 --> C15{MTS = 0?}:::C
    C15 -- Yes --> C16[Frequency Parameters]:::C
    C15 -- No --> C17[Network Data Section]:::C
    C16 --> C17
    
    %% Network Data (PTDF)
    C17 --> C18[Power Transfer Distribution Factors:<br>PTDF Matrix]:::C
    
    %% Loop Parameters
    C18 --> C19[Parameters Used Within Loop]:::C
    
    %% Conditional MTS for Loop Parameters
    C19 --> C20{MTS = 0?}:::C
    C20 -- Yes --> C21[SectorXStorageFinalMin]:::C
    C20 -- No --> C22[Flexible Demand Parameters]:::C
    C21 --> C22
    
    %% Final Scalars
    C22 --> C23[Scalars for Simulation Control]:::C
    end
    
    C23 --> C24([End]):::C
    
classDef A fill:#004C99,stroke:#004C99,stroke-width:2px,color:none,font-weight:bold,font-size:20px;
classDef B fill:#004C99,stroke:#004C99,stroke-width:2px,color:none;
classDef C fill:#003366,stroke:#003366,stroke-width:2px,color:none,font-weight:bold,font-size:10px
classDef D fill:#004C99,stroke:#none,stroke-width:2px,color:none,font-weight:bold,font-size:10px

class SG1 B;
class SG2 B;
class SG3 D;
class CC B;

%% Style the edge labels
linkStyle 0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25 color:#none,stroke:#none,stroke-width:1px;
```


```python

```

 ```mermaid
flowchart TD
    D1([Start<br>Data Import]):::A --> D2[$gdxin %inputfilename%]:::B


    %% Sets Loading
    D2 --> D3["Load Core Sets"]:::B
    D3 --> D6["Load Economic Parameters"]:::C
    
            subgraph SG1[" "]
        direction TB
    %% Basic Parameters

    D6 --> D7["Load Technical Parameters:"]:::C
    
    D7 --> D8["Load Network & Location"]:::C
    
    %% Boundary Sector Parameters
    D8 --> D10["Load Boundary Sector<br>(SECTOR X)"]:::C
    
    %% First Conditional Load
    D10 --> D11{MTS ==0?}:::C
    D11 -- Yes --> D12[Load SectorXStorageInitial]:::C
    D11 -- No --> D13[Load SectorXStorageProfile]:::C
    D12 --> D13
    
    %% Second Conditional Load
    D13 --> D14{RetrieveStatus = 1?}:::C
    D14 -- Yes --> D15[Load CommittedCalc]:::C

    %% Network Data
    D14 -- No --> D17[Load PTDF Matrix]:::C
    D15 --> D17
    
    
    %% Reserve & Frequency Parameters (Conditional)
    D17 --> D19{MTS = 0?}:::C
    D19 -- Yes --> D20["Load Frequency Parameters"]:::C

        end
    D19 -- No --> D21([End]):::C
    D20 --> D21
    
classDef A fill:#004C99,stroke:#004C99,stroke-width:2px,color:none,font-weight:bold,font-size:20px;
classDef B fill:#004C99,stroke:#004C99,stroke-width:2px,color:none,font-weight:bold,font-size:10px;
classDef C fill:#003366,stroke:#003366,stroke-width:2px,color:none,font-weight:bold,font-size:10px
classDef D fill:#004C99,stroke:#none,stroke-width:2px,color:none,font-weight:bold,font-size:10px

class SG1 B;
class SG2 B;
class SG3 D;
class CC B;

%% Style the edge labels
linkStyle 0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17 color:#none,stroke:#none,stroke-width:1px;
```



```python

```

 ```mermaid
flowchart TD
    E1([Start<br>Definitions of Variables]):::A
    E1 --> E3[Integer / Binary<br>Variables  ]:::C
    
        subgraph S2[ ]
        %% Binary/Integer Variables
            E3 --> E6{Unit<br>Operations}:::C
                subgraph S2a[ ]
                    E6 --> E7["Unit<br>commitment<br>status"]:::C
                    E6 --> E8["Unit<br>start-up"]:::C
                    E6 --> E9["Unit<br>shut-down"]:::C
                end
                subgraph S2b[ ]
                    E7 --> E10{LP<br>Formulation?}:::C
                    E8 --> E10
                    E9 --> E10
                    E10 -->|LPFormulation = 1| E11["Unit commitment status = POSITIVE<br>Unit commitment Upper Bound = 1"]:::C
                    E10 -->|LPFormulation ≠ 1| E12["All Unit Operations Vatiables = INTEGER<br>All Unit Operations Bounds = Units Number"]:::C 
                end
            end

        subgraph S3[ ]
        %% Positive Variables
            E11 --> E4[Positive<br>Variables]:::C
            E12 --> E4  
            E4 --> E13{Power<br>&<br>Flow}:::C
                
                subgraph S3a[ ]
                    E13 --> E14["Power<br>output"]:::C
                    E13 --> E15["Boundary<br>flow"]:::C
                    E13 --> E16["Line<br>flow"]:::C
                end
    
                subgraph S3b[ ]
                    E14 --> E17{Storage<br>Systems}:::C
                    E15 --> E17
                    E16 --> E17
                    E17 --> E18["Storage<br>Charging<br>input"]:::C
                    E17 --> E19["Storage<br>level"]:::C
                    E17 --> E20["Boundary<br>sector<br>storage<br>Level"]:::C
                    E17 --> E21["Reservoir<br>spillage"]:::C
                end

                subgraph S3c[ ]
                            E18 --> E22{Reserve<br>Services}:::C
                            E19 --> E22
                            E20 --> E22
                            E21 --> E22
                    E22 --> E23["Spinning<br>reserve<br>up"]:::C
                    E22 --> E24["Spinning<br>reserve<br>down"]:::C
                    E22 --> E25["Non-spinning<br>reserve"]:::C
                end

                subgraph S3d[ ]
                            E23 --> E26{Cost Variables}:::C
                            E24 --> E26
                            E25 --> E26
                    E26 --> E27["Start-up<br>cost"]:::C
                    E26 --> E28["Ramping<br>Up/Down<br>costs"]:::C
                    E26 --> E29["Hourly<br>system<br>cost"]:::C
                end

                subgraph S3e[ ]
                            E27 --> E30{Load<br>Loss<br>Variables}:::C
                            E28 --> E30
                            E29 --> E30
                    E30 --> E31["Load<br>shedding"]:::C
                    E30 --> E32["Power<br>curtailment"]:::C
                    E30 --> E33["Max power deficit<br>/<br>Max Lost Load in Energy"]:::C
                    E30 --> E34["Reserve deficits<br>/<br>Lost Spinning Reserve Up<br>Lost Spinning Reserve Down<br>Lost Non-Spinning Reserve Up"]:::C
                end

                subgraph S3f[ ]
                            E31 --> E35{Flexible<br>Demand}:::C
                            E32 --> E35
                            E33 --> E35
                            E34 --> E35
                    E35 --> E36["Boundary Sector<br>Flexible demand"]:::C
                    E35 --> E37["Boundary Sector<br>Flexible supply"]:::C
                    E35 --> E38["Accumulated<br>oversupply<br>/<br>Deferred Demand"]:::C
                end
        
                subgraph S3g[ ]
                            E36 --> E40{MTS = 0?}:::C
                            E37 --> E40
                            E38 --> E40
                    E40 -->|Yes| E41a[Frequency Stability]:::C 
                    E41a --- E41["System Inertia<br>Primary Reserve Available<br>System Gain<br>Fast Frequency Reserve Available<br>Fast Frequency Reserve Gain"]:::C
                    E40 -->|No| E42a[Boundary Sector]:::C
                    E42a--- E42["Boundary Sector Initial state of charge<br>Boundary Sector Minimum allowed state of charge"]:::C
                end
        end

        subgraph S4[ ]
    %% Free Variables
            E41 --> E5
            E42 --> E5
            E5[Free<br>Variables]:::C --> E43{System Level}:::C
            
                subgraph S4a[ ]
            E43 --> E44[Total<br>System<br>Cost]:::C
            E43 --> E45["Objective<br>function"]:::C
            E43 --> E46["Optimality<br>gap"]:::C
                end
                
                subgraph S4b[ ]
            E44 --> E47{Power<br>Balance}:::C
            E45 --> E47
            E46 --> E47
            E47 --> E48["Demand<br>flexibility"]:::C
            E47 --> E49["Boundary<br>sector<br>power"]:::C
            E47 --> E50["Residual<br>load"]:::C
            E47 --> E51["Injected<br>power"]:::C
                end
        end
    E48 --> E52
    E49 --> E52
    E50 --> E52
    E51 --> E52([End]):::C

classDef A fill:#004C99,stroke:#004C99,stroke-width:2px,color:none,font-weight:bold,font-size:30px;
classDef B fill:#004C99,stroke:#004C99,stroke-width:2px,color:none,font-weight:bold,font-size:15px;
classDef C fill:#003366,stroke:#003366,stroke-width:2px,color:none,font-weight:bold,font-size:15px
classDef D fill:#004C99,stroke:#none,stroke-width:2px,color:none,font-weight:bold,font-size:15px

class S2 B;
class S3 B;
class S4 B;
class S2a D;
class S2b D;
class S3a D;
class S3b D;
class S3c D;
class S3d D;
class S3e D;
class S3f D;
class S3g D;
class S4a D;
class S4b D;

%% Style the edge labels
linkStyle 0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,30,31,32,33,34,35,36,37,38,39,40,41,42,43,44,45,46,47,48,49,50,51,52,53,54,55,56,57,58,59,60,61,62,63,64,65,66,67,68,69,70,71,72,73 color:#none,stroke:#none,stroke-width:1px;
```


```python

```

 ```mermaid
flowchart TD

        E1(["Start<br>Assignment of Initial Values"]):::A --> E2{{"Set Initial<br>Commitment Status"}}:::C
    
    subgraph S1[" "]
        E2 --> E3["All Units: Set as OFF by Default"]:::C
        E2 --> E4["Units with Initial Power > 0: Set as ON"]:::C
    end
    
    subgraph S2[" "]
        E3 --> E5{{"Calculate<br>Power Parameters"}}:::C
        E4 --> E5
        E5 --> E6["Calculate Minimum<br>Stable Power"]:::C
        E5 --> E7["Calculate Maximum<br>Load Availability"]:::C
    end
    
    subgraph S3[" "]
        E6 --> E8{{"Check Quick<br>Start Capability"}}:::C
        E7 --> E8
        E8 --> E9{"Can Ramp Up<br>Fast Enough?"}:::C
        E9 -->|Yes| E10["Quick Start Power<br>=<br>Full Capacity"]:::C
        E9 -->|No| E11["Quick Start Power<br>=<br>Zero"]:::C
    end
    
    subgraph S4[" "]
        E10 --> E12{{"Calculate<br>Ramp Limits"}}:::C
        E11 --> E12
        E12 --> E13["Set Start-Up<br>Ramp Limit"]:::C
        E12 --> E14["Set Shut-Down<br>Ramp Limit"]:::C
    end
    
    subgraph S5[" "]
        E13 --> E15{{"Determine<br>Must-Run Status"}}:::C
        E14 --> E15
        E15 --> E16["Standard Must-Run<br>=<br>Minimum Stable Power"]:::C
        E15 --> E17["Special Must-Run<br>for<br>Certain Technologies"]:::C
    end
    
    subgraph S6[" "]
        E16 --> E18{{"Set<br>Reserve Parameters"}}:::C
        E17 --> E18
        E18 --> E19["Reserve Share from<br>Offline Quick Start Units"]:::C
    end
    
    subgraph S7[" "]
        E19 --> E20{{"Configure<br>Flexible Demand"}}:::C
        E20 --> E21["Find Maximum<br>Flexible Demand"]:::C
        E20 --> E22["Set Maximum<br>Oversupply Allowed"]:::C
        E20 --> E23["Initialize Accumulated<br>Oversupply to Zero"]:::C
    end
    
    subgraph S8[" "]
        E21 --> E24{{"Set Time<br>Configuration"}}:::C
        E22 --> E24
        E23 --> E24
        E24 --> E25["Define Simulation<br>Time Step"]:::C
    end
    

        E25 --> E26(["End"]):::C

classDef A fill:#004C99,stroke:#004C99,stroke-width:2px,color:none,font-weight:bold,font-size:20px;
classDef B fill:#004C99,stroke:#004C99,stroke-width:2px,color:none,font-weight:bold,font-size:10px;
classDef C fill:#003366,stroke:#003366,stroke-width:2px,color:none,font-weight:bold,font-size:10px
classDef D fill:#004C99,stroke:#none,stroke-width:2px,color:none,font-weight:bold,font-size:10px

class S1 B;
class S2 B;
class S3 B;
class S4 B;
class S5 B;
class S6 B;
class S7 B;
class S8 B;
class S9 B;


%% Style the edge labels
linkStyle 0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,30 color:#none,stroke:#none,stroke-width:1px;
```


```python

```

 ```mermaid
flowchart TD
    A0([Start<br>Equation Definitions]):::A --> A2

    subgraph S1[" "]
        A2{"LP Formulation = 1?"}:::C
        A3["EQ_SystemCost<br>Linear programming cost calculation<br>(relaxed commitment)"]:::C
        A4["EQ_SystemCost<br>Integer programming cost calculation<br>(full unit commitment)"]:::C
        A2 -->|Yes| A3
        A2 -->|No| A4
        A3 & A4 --- A1["EQ_Objective_function<br>Minimizes total system cost"]:::C
    end

    subgraph S2[" "]
        A1 --> A5{{"Commitment Constraints"}}:::C
        A5 --> A6["EQ_MinUpTime<br>Enforces minimum uptime duration<br>after unit startup"]:::C
        A5 --> A7["EQ_MinDownTime<br>Enforces minimum downtime duration<br>after unit shutdown"]:::C
        A5 --> A8["EQ_RampUp_TC<br>Limits maximum power increase<br>between time steps"]:::C
        A5 --> A9["EQ_RampDown_TC<br>Limits maximum power decrease<br>between time steps"]:::C
    end

    subgraph S3[" "]
        A6 & A7 & A8 & A9 --> A10a{{"Cost Equations"}}:::C
        A10a --- A10["EQ_CostStartUp<br>Calculates startup costs<br>per unit per hour"]:::C
        A10a --> A11["EQ_CostShutDown<br>Calculates shutdown costs<br>per unit per hour"]:::C
        A10a --> A12["EQ_CostRampUp<br>Calculates ramping up costs<br>for power increases"]:::C
        A10a --> A13["EQ_CostRampDown<br>Calculates ramping down costs<br>for power decreases"]:::C
    end

    subgraph S4[" "]
        A10 & A11 & A12 & A13 --> A14{"Retrieve Initial<br>Commitment Status = 1?"}:::C
        A14 -->|Yes| A15["EQ_CommittedCalc<br>Retrieves commitment status<br>from previous solution"]:::C
        A14 -->|No| A16[SkipRetrieve]:::C
    end

    subgraph S5[" "]
        A15 & A16 --> A17a{{"Power Balance"}}:::C
        A17a --- A17["EQ_Residual_Load<br>Calculates net load after<br>accounting for injections"]:::C
        A17a --> A18["EQ_Demand_balance_DA<br>Ensures generation matches<br>day-ahead demand"]:::C
    end

    subgraph S6[" "]
        A17 & A18 --> A19{"Flexible Demand Active<br>=1?"}:::C
        A19 -->|Yes| A20["EQ_Flexible_Demand<br>Models demand flexibility<br>as virtual storage"]:::C
        
            subgraph S6a[" "]
                A20 --> A21["EQ_Flexible_Demand_max<br>Limits total flexible demand<br>capacity"]:::C
                A21 --> A22["EQ_Flexible_Demand_Modulation_Min<br>Minimum downward demand adjustment"]:::C
                A22 --> A23["EQ_Flexible_Demand_Modulation_max<br>Maximum upward demand adjustment"]:::C
            end
        A19 -->|No| A24["EQ_No_Flexible_Demand<br>Disables flexible demand<br>when inactive"]:::C
            
    end

    subgraph S7[" "]
        A23 & A24 --> A25a{{"Reserve Markets"}}:::C
        A25a --- A25["EQ_Demand_balance_2U<br>Spinning reserve<br>up requirement"]:::C
        A25a --> A26["EQ_Tot_Demand_2U<br>System-wide spinning<br>reserve sum"]:::C
        A25a --> A27["EQ_Demand_balance_3U<br>Non-spinning<br>reserve requirement"]:::C
        A25a --> A28["EQ_Demand_balance_2D<br>Spinning reserve<br>down requirement"]:::C
        A25a --> A29["EQ_Curtailed_Power<br>Accounts for renewable<br>energy curtailment"]:::C
        A25a --> A30["EQ_Reserve_2U_capability<br>Unit spinning<br>reserve up capacity"]:::C
        A25a --> A31["EQ_Reserve_2D_capability<br>Unit spinning<br>reserve down capacity"]:::C
        A25a --> A32["EQ_Reserve_3U_capability<br>Unit non-spinning<br>reserve capacity"]:::C
    end

    subgraph S8[" "]
        A25 & A26 & A27 & A28 & A29 & A30 & A31 & A32 --> A33{"MTS = 0?"}:::C
        A33 -->|Yes| A34a
        A33 -->|Yes| A36a
        A33 -->|Yes| A38a
        A33 -->|Yes| A44a
        A33 -->|No| A35[Skip MTS]:::C
        
                A34a{{"Power Tracking"}}:::C
                A34["EQ_PowerLoss<br>Tracks maximum power loss<br>for stability analysis"]:::C

                A36a{{"Inertia Constraints"}}:::C
                A36["EQ_SysInertia<br>Calculates system inertia<br>from committed units"]:::C
                A37["EQ_Inertia_limit<br>Enforces minimum system<br>inertia requirement"]:::C

                A38a{{Primary Reserve}}:::C
                A38["EQ_SystemGain<br>Calculates frequency response<br>capability"]:::C
                A39["EQ_SystemGain_limit<br>Limits frequency response<br>capability"]:::C
                A40["EQ_PrimaryReserve_Available<br>Primary reserve provision"]:::C
                A41["EQ_PrimaryReserve_Capability<br>Unit primary reserve capacity"]:::C
                A42["EQ_PrimaryReserve_Boundary<br>Primary reserve limits"]:::C
                A43["EQ_Demand_balance_PrimaryReserve<br>Primary reserve requirement"]:::C

                A44a{{"Fast Frequency Reserve"}}:::C
                A44["EQ_FFRGain<br>Fast frequency response<br>capability"]:::C
                A45["EQ_FFRGain_limit<br>FFR capability limits"]:::C
                A46["EQ_FFR_Available<br>Fast frequency reserve provision"]:::C
                A47["EQ_FFR_Capability<br>Unit FFR capacity"]:::C
                A48["EQ_FFR_Boundary<br>FFR provision limits"]:::C
                A49["EQ_Demand_balance_FFR<br>FFR requirement"]:::C
                
            subgraph S8a[" "]
                A34a --> A34
            end
            subgraph S8b[" "]
                A36a --> A36
                A36 --> A37
                
            end
            subgraph S8c[" "]
                A38a --> A38
                A38 --> A39
                A39 --> A40
                A40 --> A41
                A41 --> A42
                A42 --> A43
                
            end
            subgraph S8d[" "]
                A44a --> A44
                A44 --> A45
                A45 --> A46
                A46 --> A47
                A47 --> A48
                A48 --> A49
            end
    end

    subgraph S9[" "]
        A35 & A34 & A37 & A43 & A49 --> A50a{{"Core Constraints"}}:::C
        A50a --> A50["EQ_Power_must_run<br>Minimum stable<br>generation level"]:::C
        A50a --> A51["EQ_Power_available<br>Maximum<br>available capacity"]:::C
        A50a --> A52["EQ_Storage_minimum<br>Minimum<br>storage level"]:::C
        A50a --> A53["EQ_Storage_alert<br>Storage alert level<br>with violation"]:::C
        A50a --> A54["EQ_Storage_flood_control<br>Maximum<br>storage level"]:::C
        A50a --> A55["EQ_Storage_level<br>Storage<br>capacity limit"]:::C
        A50a --> A56["EQ_Storage_input<br>Storage<br>charging limit"]:::C
        A50a --> A57["EQ_Storage_MaxDischarge<br>Maximum<br>discharge rate"]:::C
        A50a --> A58["EQ_Storage_MaxCharge<br>Maximum<br>charging rate"]:::C
        A50a --> A59["EQ_Storage_balance<br>Storage<br>energy conservation"]:::C
        A50a --> A60["EQ_Storage_boundaries<br>Final<br>storage level"]:::C
        A50a --> A61["EQ_Storage_Cyclic<br>Cyclic<br>storage conditions"]:::C
    end

    subgraph S10[" "]
        A50 & A51 & A52 & A53 & A54 & A55 & A56 & A57 & A58 & A59 & A60 & A61 --> A62a{{"Network Equations"}}:::C
        A62a --- A62["EQ_Emission_limits<br>Pollution emission caps"]:::C
        A62a --> A63["EQ_DC_Power_Flow<br>Linearized power flow model"]:::C
        A62a --> A64["EQ_Total_Injected_Power<br>Node injection balance"]:::C
        A62a --> A65["EQ_Flow_limits_lower<br>Minimum line flow"]:::C
        A62a --> A66["EQ_Flow_limits_upper<br>Maximum line flow"]:::C
        A62a --> A67["EQ_BS_Flow_limits_lower<br>Minimum boundary flow"]:::C
        A62a --> A68["EQ_BS_Flow_limits_upper<br>Maximum boundary flow"]:::C
        A62a --> A69["EQ_BS_Spillage_limits_upper<br>Boundary sector spillage limit"]:::C
    end

    subgraph S11[" "]
        A62 & A63 & A64 & A65 & A66 & A67 & A68 & A69 --> A69a{{"Operational Constraints"}}:::C
        A69a --> A70["EQ_Force_Commitment<br>Mandatory unit commitment"]:::C
        A69a --> A71["EQ_Force_DeCommitment<br>Mandatory unit decommitment"]:::C
        A69a --> A72["EQ_LoadShedding<br>Emergency load reduction limits"]:::C
    end

    subgraph S12[" "]
        A70 & A71 & A72 --> A73a{{"CHP Equations"}}:::C
        A73a --> A73["EQ_CHP_extraction<br>Extraction CHP power-heat coupling"]:::C
        A73a --> A74["EQ_CHP_extraction_Pmax<br>Extraction CHP maximum power"]:::C
        A73a --> A75["EQ_CHP_backpressure<br>Backpressure CHP operation"]:::C
        A73a --> A76["EQ_CHP_max_heat<br>CHP maximum heat output"]:::C
    end

    subgraph S13[" "]
        A73 & A74 & A75 & A76 --> A77a{{"Boundary Sector"}}:::C
        A77a --> A77["EQ_Power_Balance_of_P2X_units<br>Power-to-X conversion balance"]:::C
        A77a --> A78["EQ_Power_Balance_of_X2P_units<br>X-to-Power conversion balance"]:::C
        A77a --> A79["EQ_Max_Power_Consumption_of_BS_units<br>Boundary sector power limits"]:::C
        A77a --> A80["EQ_BS_Demand_balance<br>Boundary sector energy balance"]:::C
    end

    subgraph S14[" "]
        A77 & A78 & A79 & A80 --> A81a{{"Boundary Sector<br>Flex and Conversion"}}:::C
        A81a --> A81["EQ_Tot_Flex_Demand_BS<br>Total boundary<br>flex demand"]:::C
        A81a --> A82["EQ_Max_Flex_Capacity_BS<br>Boundary flex<br>demand limits"]:::C
        A81a --> A83["EQ_BS_Flex_Demand<br>Boundary sector<br>flexible demand"]:::C
        A81a --> A84["EQ_Tot_Flex_Supply_BS<br>Total boundary<br>flex supply"]:::C
        A81a --> A85["EQ_Max_Flex_Supply_BS<br>Boundary flex<br>supply limits"]:::C
        A81a --> A86["EQ_P2X_Power_Balance<br>Power-to-X<br>balance equation"]:::C
        A81a --> A87["EQ_X2P_Power_Consumption<br>X-to-Power<br>consumption"]:::C
        A81a --> A88["EQ_Max_Power_Consumption<br>Maximum<br>conversion capacity"]:::C
    end
    A81 --- A89([End]):::C
    A82 --- A89
    A83 --- A89
    A84 --- A89
    A85 --- A89
    A86 --- A89
    A87 --- A89
    A88 --- A89

classDef A fill:#004C99,stroke:#004C99,stroke-width:2px,color:none,font-weight:bold,font-size:20px;
classDef B fill:#004C99,stroke:#004C99,stroke-width:2px,color:none,font-weight:bold,font-size:10px;
classDef C fill:#003366,stroke:#003366,stroke-width:2px,color:none,font-weight:bold,font-size:10px
classDef D fill:#004C99,stroke:#none,stroke-width:2px,color:none,font-weight:bold,font-size:10px

class S1 B;
class S2 B;
class S3 B;
class S4 B;
class S5 B;
class S6 B;
class S6a D;
class S7 B;
class S8 B;
class S8a D;
class S8b D;
class S8c D;
class S8d D;
class S9 B;
class S10 B;
class S11 B;
class S12 B;
class S13 B;
class S14 B;

%% Style the edge labels
linkStyle 0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,30,31,32,33,34,35,36,37,38,39,40,41,42,43,44,45 color:#none,stroke:#none,stroke-width:1px;
```

```python

```

 ```mermaid
flowchart TD
    F1([Start<br>Definition of the Model]):::A --> F3["Hourly System Cost<br><br>EQ_SystemCost"]:::C
    subgraph S0["Objective & Cost"]
        F3 --> F4{"LP<br>Formulation =1?"}:::C
        F4 -->|No| F5["Startup & Shutdown Costs<br><br>EQ_CostStartUp<br>EQ_CostShutDown"]:::C
        F5 --> F6["Total Optimization Cost<br><br>EQ_Objective_function"]:::C
        F4 -->|Yes| F6
        F3 --> F7["Ramping Costs<br><br>EQ_CostRampUp<br>EQ_CostRampDown"]:::C
        F7 --> F6
    end

    subgraph S1["Commitment Constraints"]
        F6 --> F8["Unit Commitment<br>Ramp Rate Limits<br><br>EQ_Commitment<br>EQ_RampUp_TC<br>EQ_RampDown_TC"]:::C
        F8 --> F9{"LP<br>Formulation =1?"}:::C
        F9 -->|No| F10["Minimum Up & Down Time<br><br>EQ_MinUpTime<br>EQ_MinDownTime"]:::C
        F10 --> F11
        F9 -->|Yes| F11
    end

    subgraph S2["Power & Demand Balance"]
        F11["Residual Load<br><br>EQ_Residual_Load"]:::C --> F12["Day-Ahead Demand Balance<br><br>EQ_Demand_balance_DA"]:::C
        F12 --> F13{"LP<br>Formulation =1?"}:::C
        F13 -->|No| F14["Must-Run Power<br><br>EQ_Power_must_run"]:::C
        F14 --> F15
        F13 -->|Yes| F15
    end

    subgraph S3["Flexible Demand & Boundary Sector"]
        F15{Flexible Demand Active =1?}:::C --> |Yes| F16["Flexible Demand<br>Max Flexibility<br><br>EQ_Flexible_Demand<br>EQ_Flexible_Demand_Max"]:::C
        F15 -->|No| F17["No Flexible Demand<br><br>EQ_No_Flexible_Demand"]:::C
        F16 & F17 --> F18["Boundary Sector Flexibility<br>Max Power Consumption<br><br>EQ_Tot_Flex_Demand<br>EQ_Max_Flex_Demand<br>EQ_Max_Flex_Supply<br>EQ_Max_Power_Consumption_of_BS_units"]:::C
    end

    subgraph S4["Reserves & Curtailment"]
        F18 --> F19["Spinning & Non-Spinning Reserve<br>Total Reserve Demand<br><br>EQ_Demand_balance_2U<br>EQ_Demand_balance_2D<br>EQ_Demand_balance_3U<br>EQ_Tot_Demand_2U"]:::C
        F19 --> F20["Reserve Capability<br>VRES Curtailment<br><br>EQ_Reserve_2U_capability<br>EQ_Reserve_2D_capability<br>EQ_Reserve_3U_capability<br>EQ_Curtailed_Power"]:::C
    end

    subgraph S5["CHP & P2X Equations"]
        F20 --> F21["CHP Operation Limits<br>Heat-to-Power Constraints<br><br>EQ_CHP_extraction_Pmax<br>EQ_CHP_extraction<br>EQ_CHP_backpressure<br>EQ_CHP_max_heat<br>EQ_2U_limit_chp<br>EQ_2D_limit_chp<br>EQ_3U_limit_chp"]:::C
        F21 --> F22["P2X Power Balance<br>X2P Consumption<br>Max P2X Load<br><br>EQ_P2X_Power_Balance<br>EQ_X2P_Power_Consumption<br>EQ_Max_Power_Consumption"]:::C
    end

    subgraph S6["Storage & Boundary Storage"]
        F22 --> F23["Storage Limits & Levels<br>Charge/Discharge Balance<br><br>EQ_Storage_minimum<br>EQ_Storage_alert<br>EQ_Storage_flood_control<br>EQ_Storage_level<br>EQ_Storage_input<br>EQ_Storage_balance<br>EQ_Storage_boundaries<br>EQ_Storage_MaxCharge<br>EQ_Storage_MaxDischarge"]:::C
        F23 --> F24{"Rolling Horizon?<br>MTS =1?"}:::C
        F24 -->|Yes| F25["Cyclic Storage (MTS)<br><br>EQ_Storage_Cyclic"]:::C
        F25 --> F26
        F24 -->|No| F26
        F26["Boundary Sector Storage<br>Level, Charge & Discharge<br><br>EQ_Boundary_Sector_Storage_MaxDischarge<br>EQ_Boundary_Sector_Storage_MaxCharge<br>EQ_Boundary_Sector_Storage_PowerMax<br>EQ_Boundary_Sector_Storage_PowerMin<br>EQ_Boundary_Sector_Storage_minimum<br>EQ_Boundary_Sector_Storage_level<br>EQ_Boundary_Sector_Storage_alert<br>EQ_Boundary_Sector_Flood_Control<br>EQ_Boundary_Sector_Storage_balance<br>EQ_Boundary_Sector_Storage_boundaries"]:::C --> F27{"Rolling Horizon?<br>MTS =1?"}:::C
        F27 -->|Yes| F28["Cyclic Boundary Storage<br><br>EQ_Boundary_Sector_Storage_Cyclic"]:::C
        F28 --> F29
        F27 -->|No| F29
    end

    subgraph S7["Network & Operational"]
        F29["Power Availability<br>Load Shedding<br>Flow Limits<br>DC Power Flow<br><br>EQ_Power_available<br>EQ_LoadShedding<br>EQ_Flow_limits_lower<br>EQ_Flow_limits_upper<br>EQ_BS_Flow_limits_lower<br>EQ_BS_Flow_limits_upper<br>EQ_Total_Injected_Power<br>EQ_DC_Power_Flow"]:::C --> F30{"Use Prior Commitment?<br>RetrieveStatus =1?"}:::C
        F30 -->|Yes| F31["Fixed Initial Commitment<br><br>EQ_CommittedCalc"]:::C
        F31 --> F32
        F30 -->|No| F32
    end

    subgraph S8["System Services (MTS = 0)"]
        F32{"Frequency-Constrained Mode?<br>MTS =0?"}:::C -->|Yes| F33["Inertia & Frequency Response<br>Primary & FFR Reserves<br>Power Loss<br><br>EQ_SysInertia<br>EQ_Inertia_limit<br>EQ_SystemGain<br>EQ_SystemGain_limit<br>EQ_PrimaryReserve_Available<br>EQ_PrimaryReserve_Capability<br>EQ_PrimaryReserve_Boundary<br>EQ_Demand_balance_PrimaryReserve<br>EQ_FFRGain<br>EQ_FFRGain_limit<br>EQ_FFR_Available<br>EQ_FFR_Capability<br>EQ_FFR_Boundary<br>EQ_Demand_balance_FFR<br>EQ_PowerLoss"]:::C
        F33 --> F34
        F32 -->|No| F34
    end

    F34([Model Configuration]):::C --> F35([End]):::C

classDef A fill:#004C99,stroke:#004C99,stroke-width:2px,color:none,font-weight:bold,font-size:20px;
classDef B fill:#004C99,stroke:#004C99,stroke-width:2px,color:none,font-weight:bold,font-size:10px;
classDef C fill:#003366,stroke:#003366,stroke-width:2px,color:none,font-weight:bold,font-size:10px
classDef D fill:#004C99,stroke:#none,stroke-width:2px,color:none,font-weight:bold,font-size:10px

class S0 B;
class S1 B;
class S2 B;
class S3 B;
class S4 B;
class S5 B;
class S6 B;
class S7 B;
class S8 B;
class S9 B;
class S10 B;
class S11 B;
class S12 B;
class S13 B;
class S14 B;

%% Style the edge labels
linkStyle 0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,30,31,32,33,34,35,36,37,38,39,40,41 color:#none,stroke:#none,stroke-width:1px;
```

```python

```

 ```mermaid
flowchart TD
    H1(["Start<br>Solving Loop"]):::A --> H2["Calculate Total Days<br><br>Calculate ndays<br/>ndays = floor(card(h)*TimeStep/24)"]:::C

    subgraph SG1["Validation Phase"]
        H2 --> H3{"Look Ahead<br>Too Long?<br><br>LookAhead<br>><br>ndays-1?"}:::C
        H3 -->|Yes| H4["ABORT: Look ahead period<br>longer than simulation length"]:::C
        H3 -->|No| H5{"Look Ahead Not Compatible with Time Step?<br><br>LookAhead*24 mod TimeStep ≠ 0?"}:::C
        H5 -->|Yes| H6["Abort Execution:<br/>Time Step Mismatch<br><br>ABORT: Look ahead period not multiple of TimeStep"]:::C
        H5 -->|No| H7{"Horizon Length Not Compatible with Time Step?<br><br>Length*24 mod TimeStep ≠ 0?"}:::C
        H7 -->|Yes| H8["Abort Execution:<br/>Horizon Length Mismatch<br><br>ABORT: Rolling horizon length not multiple of TimeStep"]:::C
        H7 -->|No| H9
        H9["Initialize Loop Parameters and Display Configuration<br><br>• Set tmp = {model, solver}<br/>• Parameter status(tmp,h)<br/>• Scalar starttime<br/>• Set days, display parameters"]:::C
    end

    subgraph SG3["Rolling Horizon Optimization Loop"]
        H10["Start Rolling Horizon Loop Through All Days<br><br>FOR day = 1 TO ndays-LookAhead BY RollingHorizon Length"]:::C
        
        subgraph SG3A["Time Window Setup"]
            H11["Calculate Time Windows for Current Optimization<br><br>• FirstHour = (day-1)*24/TimeStep+1<br/>• LastHour = min(card(h), FirstHour + (Length+LookAhead)*24/TimeStep - 1)<br/>• LastKeptHour = LastHour - LookAhead*24/TimeStep"]:::C
            H12["Set Current Optimization Horizon<br><br>• i(h) = no<br/>• i(h) = yes for FirstHour ≤ ord(h) ≤ LastHour<br/>• Display day, FirstHour, LastHour, LastKeptHour"]:::C
        end
        
        subgraph SG3B["Storage Requirements Setup"]
            H13["Define Storage Final Requirements<br><br>• StorageFinalMin(s) = sum(...)<br/>• StorageFinalMin(chp) = sum(...)"]:::C
            H14{"Multi-Time Scale Mode Active?<br><br>MTS = 0?"}:::C
            H15["Set Sector Storage Requirements<br><br>SectorXStorageFinalMin(nx) = sum(...)"]:::C
        end
        
        subgraph SG3C["Model Solving"]

            H17{"Linear Programming Formulation?<br><br>LPFormulation = 1?"}:::C --> |Yes| H18["Solve as Linear Program<br><br>SOLVE UCM_SIMPLE USING LP MINIMIZING SystemCostD"]:::C
            H17 -->|No| H19["Solve as Mixed Integer Program<br><br>SOLVE UCM_SIMPLE USING MIP MINIMIZING SystemCostD"]:::C
            H20["Record Solution Status Information<br><br>• status(model,i) = UCM_SIMPLE.Modelstat<br/>• status(solver,i) = UCM_SIMPLE.Solvestat"]:::C
        end
        
        subgraph SG3D["Results Processing & State Updates"]
            H21["Update Initial Conditions for Next Iteration<br><br>• CommittedInitial(au) = Committed.L at LastKeptHour<br/>• PowerInitial(u) = Power.L at LastKeptHour<br/>• StorageInitial(s,chp) = StorageLevel.L at LastKeptHour"]:::C
            H22{"Multi-Time Scale Mode Active?<br><br>MTS = 0?"}:::C
            H23["Update Sector Storage States<br><br>SectorXStorageInitial(nx) = SectorXStorageLevel.L at LastKeptHour"]:::C
            H24["Update Flexible Demand States<br><br>• SectorXFlexDemandInputInitial(nx)<br/>• SectorXFlexSupplyInputInitial(nx)"]:::C
            H25{"Flexible Demand Activated?<br><br>ActivateFlexibleDemand = 1?"}:::C
            H26["Update Accumulated Oversupply Information<br><br>AccumulatedOverSupply_inital(n) = AccumulatedOverSupply.L at LastKeptHour"]:::C
        end
        
        subgraph SG3E["Results Assignment & Error Calculation"]
            H27["Assign Results to Hourly Arrays<br><br>• StorageSlack.L = Waterslack.L<br/>• StorageLevelViolation_H.L = StorageLevelViolation.L<br/>• SectorXStorageLevelViolation_H.L<br/>• ObjectiveFunction.L = SystemCostD.L"]:::C
            H28["Calculate Total Error Metrics<br><br>Calculate Error.L = Σ(CostLoadShedding*ShedLoad.L + ValueOfLostLoad*(LL_MaxPower + LL_MinPower) + 0.8*ValueOfLostLoad*(LL_2U + LL_2D + LL_3U) + 0.7*ValueOfLostLoad*(LL_RampUp + LL_RampDown))"]:::C
            H29["Calculate Optimality and Error Gaps<br><br>• OptimalityGap.L = objVal - objEst<br/>• OptimizationError.L = Error.L - OptimalityGap.L"]:::C
        end
        
        subgraph SG3F["Loop Control"]
            H30{"More Days to Process?<br><br>More days?"}:::C
        end
    end

    subgraph SG4["Final Results"]
        H31["Display All Final Results<br><br>PowerX.L, Flow.L, Power.L, Committed.L, ShedLoad.L, CurtailedPower.L, StorageLevel.L, SystemCost.L, LL_MaxPower.L, etc."]:::C
        H32(["Loop Complete"]):::C
    end


    H32 --- H33(["End"]):::C
    
    %% Connections between subgraphs
    H9 --> H10
    H10 --> H11
    H11 --> H12
    H12 --> H13
    H13 --> H14
    H14 -->|Yes| H15
    H14 -->|No| H17
    H15 --> H17
    H18 --> H20
    H19 --> H20
    H20 --> H21
    H21 --> H22
    H22 -->|Yes| H23
    H22 -->|No| H24
    H23 --> H24
    H24 --> H25
    H25 -->|Yes| H26
    H25 -->|No| H27
    H26 --> H27
    H27 --> H28
    H28 --> H29
    H29 --> H30
    H30 -->|Yes| H10
    H30 -->|No| H31
    H31 --> H32
    
    %% Error paths
    H4 --> H33
    H6 --> H33
    H8 --> H33


classDef A fill:#004C99,stroke:#004C99,stroke-width:2px,color:none,font-weight:bold,font-size:15px;
classDef B fill:#004C99,stroke:#004C99,stroke-width:2px,color:none,font-weight:bold,font-size:10px;
classDef C fill:#003366,stroke:#003366,stroke-width:2px,color:none,font-weight:bold,font-size:10px
classDef D fill:#004C99,stroke:#none,stroke-width:2px,color:none,font-weight:bold,font-size:10px

class SG1 B;
class SG2 B;
class SG3 B;
class SG3A D;
class SG3B D;
class SG3C D;
class SG3D D;
class SG3E D;
class SG3F D;
class SG4 B;
class SG5 B;
class SG6 B;
class SG7 B;
class SG8 B;
class SG9 B;
class SG10 B;
class SG11 B;
class SG12 B;
class SG13 B;
class SG14 B;

%% Style the edge labels
linkStyle 0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20,21,22,23,24,25,26,27,28,30,31,32,33,34,35,36,37,38 color:#none,stroke:#none,stroke-width:1px;
```

```python

```

 ```mermaid
graph TB
    %% General Structure of the Dispa-SET GAMS Model
    %% Main Components
    A([Start<br>Dispa-SET GAMS Model]):::A --> S1 --> S2 --> S3 --> S4 --> S4_5 --> S5 --> S6 --> S7 --> S8 --> S9 --> I([End]):::C

    %% Model Title and Global Settings
    direction LR
    subgraph S1["Model Title and Global Settings"]
        A1{{"Model Title and Global Settings"}}:::C --> |"Define"|A1_1["Title: UCM model"]:::C
        A1 --> |"Set"|A1_2["Global Options"]:::C
    end

    %% Model Configuration Options
    direction LR
    subgraph S2["Model Configuration Options"]
        A2{{"Model Configuration Options"}}:::C --> |"Define"|A2_1["Input File Name"]:::C
        A2 --> |"Set"|A2_2["Formulation Type"]:::C
        A2 --> |"Set"|A2_3["Retrieve Status"]:::C
        A2 --> |"Set"|A2_4["Activate Flexible Demand"]:::C
        A2 --> |"Set"|A2_5["Activate Advanced Reserves"]:::C
        A2 --> |"Set"|A2_6["Frequency Constraints"]:::C
    end

    %% Set Definitions
    direction LR
    subgraph S3["Set Definitions"]
        B{{"Set Definitions"}}:::C --> |"Define sets for"|B1["Markets"]:::C
        B --> |"Define sets for"|B2["Units"]:::C
        B --> |"Define sets for"|B3["Fuels"]:::C
        B --> |"Define sets for"|B4["Technologies"]:::C
        B --> |"Define sets for"|B5["Nodes"]:::C
        B --> |"Define sets for"|B6["Lines"]:::C
    end

    %% Parameter Definitions
    direction LR
    subgraph S4["Parameter Definitions"]
        C{{"Parameter Definitions"}}:::C --> |"Define parameters for"|C1["Operational Parameters"]:::C
        C --> |"Define parameters for"|C2["Economic Parameters"]:::C
        C --> |"Define parameters for"|C3["Storage Parameters"]:::C
        C --> |"Define parameters for"|C4["Flexible Demand Parameters"]:::C
    end

    %% Data Import
    direction LR
    subgraph S4_5["Data Import"]
        D4_5{{"Data Import"}}:::C --> |"Load from"|D4_5_1["$gdxin %inputfilename%"]:::C
        
        D4_5_1 --> |"Load sets"|D4_5_2["Core model dimensions (mk, n, nx, l, etc.)"]:::D
        D4_5_1 --> |"Load parameters"|D4_5_3["Operational & economic inputs"]:::D
        D4_5_1 --> |"Load conditional"|D4_5_4["Boundary sector parameters"]:::D
        D4_5_1 --> |"Load conditional"|D4_5_5["Network data (PTDF)"]:::D
        D4_5_1 --> |"Load conditional"|D4_5_6["Reserve & frequency parameters"]:::D
    end

    %% Variable Definitions
    direction LR
    subgraph S5["Variable Definitions"]
        D{{"Variable Definitions"}}:::C --> |"Define variables for"|D1["Binary Variables"]:::C
        D --> |"Define variables for"|D2["Continuous Variables"]:::C
        D --> |"Define variables for"|D3["Positive Variables"]:::C
    end

    %% Equation Definitions
    direction LR
    subgraph S6["Equation Definitions"]
        E{{"Equation Definitions"}}:::C --> |"Define equations for"|E1["Objective Function"]:::C
        E --> |"Define equations for"|E2["Commitment Constraints"]:::C
        E --> |"Define equations for"|E3["Ramp Constraints"]:::C
        E --> |"Define equations for"|E4["Demand Balance Constraints"]:::C
        E --> |"Define equations for"|E5["Storage Constraints"]:::C
        E --> |"Define equations for"|E6["Reserve Constraints"]:::C
    end

    %% Model Definition
    direction LR
    subgraph S7["Model Definition"]
        F{{"Model Definition"}}:::C --> |"Define model using"|F1["Model Declaration"]:::C
        F --> |"Include equations in"|F2["Model Equations"]:::C
    end

    %% Solve Statement
    direction LR
    subgraph S8["Solve Statement"]
        G{{"Solve Statement"}}:::C --> |"Solve model using"|G1["Solve Using LP / MIP"]:::C
        G --> |"Set optimization options"|G2["Optimization Options"]:::C
    end

    %% Result Export
    direction LR
    subgraph S9["Result Export"]
        H{{"Result Export"}}:::C --> |"Export results to"|H1["Export Results to GDX"]:::C
        H --> |"Display results"|H2["Display Results"]:::C
    end

classDef A fill:#004C99,stroke:#004C99,stroke-width:2px,color:none,font-weight:bold,font-size:25px;
classDef B fill:#004C99,stroke:#004C99,stroke-width:2px,color:none,font-weight:bold,font-size:15px;
classDef C fill:#003366,stroke:#003366,stroke-width:2px,color:none,font-weight:bold,font-size:20px;
classDef D fill:#003366,stroke:#003366,stroke-width:2px,color:none,font-weight:bold,font-size:15px;
classDef E fill:#004C99,stroke:#none,stroke-width:2px,color:none,font-weight:bold,font-size:16px;

class S1 B;
class S2 B;
class S3 B;
class S4 B;
class S4_5 B;
class S5 B;
class S6 B;
class S7 B;
class S8 B;
class S9 B;

linkStyle default stroke:#none,color:#none,stroke-width:1px;
```

```python

```

 ```mermaid
graph TB
    %% Model Title and Global Settings
    direction LR
    subgraph S1["Model Title and Global Settings"]
        A1{{"Model Title and Global Settings"}}:::C --> |"Define"|A1_1["Title: UCM model"]:::C

        A1 --> |"Set"|A1_2["Global Options"]:::C
        %% Global Options Details
        A1_2 --> |"Set"|A1_2_1["Enable 16 parallel threads for computation<br><br>Option threads=16"]:::D
        A1_2 --> |"Set"|A1_2_2["Set iteration limit to 1 billion<br><br>Option IterLim=1000000000"]:::D
        A1_2 --> |"Set"|A1_2_3["Set resource limit to 10 billion units<br><br>Option ResLim=10000000000"]:::D
        A1_2 --> |"Set"|A1_2_4["Use Gurobi as the optimization solver<br><br>Option solver=gurobi"]:::D
        A1_2 --> |"Set"|A1_2_5["Minimize listing file output<br><br>Reduce .lst file size"]:::D

            A1_2_5 ---> |"Turn off"|A1_2_5a["Disable input file listing in output<br><br>$$offlisting"]:::D
            A1_2_5 ---> |"Turn off"|A1_2_5b["Disable log file generation<br><br>$offlog"]:::D
            A1_2_5 ---> |"Turn off"|A1_2_5c["Disable symbol cross-reference listing<br><br>$offsymxref"]:::D
            A1_2_5 ---> |"Turn off"|A1_2_5d["Disable symbol list in output<br><br>$offsymlist"]:::D

        A1_2 --> |"Set"|A1_2_6["Display all equations without row limit<br><br>Option limrow=0"]:::D
        A1_2 --> |"Set"|A1_2_7["Display all variables without column limit<br><br>Option limcol=0"]:::D
        A1_2 --> |"Set"|A1_2_8["Disable solver solution output printing<br><br>Option solprint=off"]:::D
        A1_2 --> |"Set"|A1_2_9["Disable solver system output printing<br><br>Option sysout=off"]:::D
    end

classDef A fill:#004C99,stroke:#004C99,stroke-width:2px,color:none,font-weight:bold,font-size:25px;
classDef B fill:#004C99,stroke:#004C99,stroke-width:2px,color:none,font-weight:bold,font-size:15px;
classDef C fill:#003366,stroke:#003366,stroke-width:2px,color:none,font-weight:bold,font-size:20px;
classDef D fill:#003366,stroke:#003366,stroke-width:2px,color:none,font-weight:bold,font-size:15px;
classDef E fill:#004C99,stroke:#none,stroke-width:2px,color:none,font-weight:bold,font-size:16px;

class S1 B;
```

```python

```

 ```mermaid
graph TB
    %% Model Configuration Options
    direction LR
    subgraph S2["Model Configuration Options"]
        A2{{"Model Configuration Options"}}:::C --> |"Define"|A2_1["Specify input data file name<br><br>set InputFileName Inputs.gdx"]:::D
        A2 --> |"Set"|A2_2["Choose formulation type (0=MIP, 1=LP)<br><br>setglobal LPFormulation 0"]:::D
        A2 --> |"Set"|A2_3["Enable/disable status retrieval (0=No, 1=Yes)<br><br>setglobal RetrieveStatus 0"]:::D
        A2 --> |"Set"|A2_4["Activate flexible demand equations (0=No, 1=Yes)<br><br>setglobal ActivateFlexibleDemand 1"]:::D
        A2 --> |"Set"|A2_5["Activate advanced reserve demand (0=No, 1=Yes)<br><br>setglobal ActivateAdvancedReserves 0"]:::D
        A2 --> |"Set"|A2_6["Enable frequency constrained UC/OD (0=No, 1=Yes)<br><br>setglobal FC 0"]:::D
    end

classDef A fill:#004C99,stroke:#004C99,stroke-width:2px,color:none,font-weight:bold,font-size:25px;
classDef B fill:#004C99,stroke:#004C99,stroke-width:2px,color:none,font-weight:bold,font-size:15px;
classDef C fill:#003366,stroke:#003366,stroke-width:2px,color:none,font-weight:bold,font-size:20px;
classDef D fill:#003366,stroke:#003366,stroke-width:2px,color:none,font-weight:bold,font-size:15px;
classDef E fill:#004C99,stroke:#none,stroke-width:2px,color:none,font-weight:bold,font-size:16px;

class S2 B;
```

```python

```

 ```mermaid
graph TB
    %% Set Definitions
    direction LR
    subgraph S3["Set Definitions"]
        B{{"Set Definitions"}}:::C --> |"Markets"|B1["Represents different energy markets in the model<br><br>mk: Markets"]:::D

        B --> |"Units"|B2["Various types of generation and storage units in the system<br><br>au: All Units<br>u(au): Generation units<br>chp(u): CHP units<br>p2x(au): Power to X<br>x2p(au): X to Power<br>xu(au): Boundary sector only units<br>s(au): Storage Units<br>th(au): Units with thermal storage<br>hu(au): Heat only units<br>cu(au): Conventional units only<br>ba(au): Batteries only"]:::D

        B --> |"Fuels"|B3["Different fuel types used in power generation<br><br>f: Fuel types"]:::D

        B --> |"Technologies"|B4["Classification of generation technologies by type<br><br>t: Generation technologies<br>tr(t): Renewable generation technologies<br>tc(t): Conventional technologies"]:::D

        B --> |"Nodes"|B5["Network nodes including internal and boundary connections<br><br>n: Nodes<br>nx: Boundary sector nodes"]:::D

        B --> |"Lines"|B6["Transmission network components and connections<br><br>l: Lines<br>l_int(l): Lines between internal zones<br>l_RoW(l): Lines to rest of the world<br>lx: Boundary sector lines<br>slx: Boundary sector spillage lines"]:::D

        B --> |"Simulation"|B7["Time-related sets and special unit classifications<br><br>h: Hours<br>i(h): Subset of simulated hours<br>z(h): Subset of every simulated hour<br>wat(au): Hydro technologies"]:::D

        B --> |"Aliases"|B8["Create shortcuts for easier set referencing throughout the model<br><br>Alias(mk,mkmk)<br>Alias(n,nn)<br>Alias(l,ll)<br>Alias(u,uu)<br>Alias(t,tt)<br>Alias(f,ff)<br>Alias(p,pp)<br>Alias(s,ss)<br>Alias(h,hh)<br>Alias(i,ii)"]:::D
    end

classDef A fill:#004C99,stroke:#004C99,stroke-width:2px,color:none,font-weight:bold,font-size:25px;
classDef B fill:#004C99,stroke:#004C99,stroke-width:2px,color:none,font-weight:bold,font-size:15px;
classDef C fill:#003366,stroke:#003366,stroke-width:2px,color:none,font-weight:bold,font-size:20px;
classDef D fill:#003366,stroke:#003366,stroke-width:2px,color:none,font-weight:bold,font-size:15px;
classDef E fill:#004C99,stroke:#none,stroke-width:2px,color:none,font-weight:bold,font-size:16px;

class S3 B;
```

```python

```

 ```mermaid
graph TB
    %% Set Definitions
    direction LR
    subgraph S3["Set Definitions"]
        B{{"Set Definitions"}}:::C --> |"Markets"|B1["Represents different energy markets in the model<br><br>mk: Markets"]:::D

        B --> |"Units"|B2["Various types of generation and storage units in the system<br><br>au: All Units<br>u(au): Generation units<br>chp(u): CHP units<br>p2x(au): Power to X<br>x2p(au): X to Power<br>xu(au): Boundary sector only units<br>s(au): Storage Units<br>th(au): Units with thermal storage<br>hu(au): Heat only units<br>cu(au): Conventional units only<br>ba(au): Batteries only"]:::D

        B --> |"Fuels"|B3["Different fuel types used in power generation<br><br>f: Fuel types"]:::D

        B --> |"Technologies"|B4["Classification of generation technologies by type<br><br>t: Generation technologies<br>tr(t): Renewable generation technologies<br>tc(t): Conventional technologies"]:::D

        B --> |"Nodes"|B5["Network nodes including internal and boundary connections<br><br>n: Nodes<br>nx: Boundary sector nodes"]:::D

        B --> |"Lines"|B6["Transmission network components and connections<br><br>l: Lines<br>l_int(l): Lines between internal zones<br>l_RoW(l): Lines to rest of the world<br>lx: Boundary sector lines<br>slx: Boundary sector spillage lines"]:::D

        B --> |"Simulation"|B7["Time-related sets and special unit classifications<br><br>h: Hours<br>i(h): Subset of simulated hours<br>z(h): Subset of every simulated hour<br>wat(au): Hydro technologies"]:::D

        B --> |"Aliases"|B8["Create shortcuts for easier set referencing throughout the model<br><br>Alias(mk,mkmk)<br>Alias(n,nn)<br>Alias(l,ll)<br>Alias(u,uu)<br>Alias(t,tt)<br>Alias(f,ff)<br>Alias(p,pp)<br>Alias(s,ss)<br>Alias(h,hh)<br>Alias(i,ii)"]:::D
    end

classDef A fill:#004C99,stroke:#004C99,stroke-width:2px,color:none,font-weight:bold,font-size:25px;
classDef B fill:#004C99,stroke:#004C99,stroke-width:2px,color:none,font-weight:bold,font-size:15px;
classDef C fill:#003366,stroke:#003366,stroke-width:2px,color:none,font-weight:bold,font-size:20px;
classDef D fill:#003366,stroke:#003366,stroke-width:2px,color:none,font-weight:bold,font-size:15px;
classDef E fill:#004C99,stroke:#none,stroke-width:2px,color:none,font-weight:bold,font-size:16px;

class S3 B;
```

```python

```

 ```mermaid