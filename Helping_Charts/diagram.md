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