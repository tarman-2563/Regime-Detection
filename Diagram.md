```mermaid

flowchart TD

%% ---------------- FLOW ----------------

A[User Opens Application] --> B[Upload Time-Series CSV File]

B --> C{Is File Valid?}

C -- No --> D[Show Error Message]
D --> B

C -- Yes --> E[Parse & Sort Data]

E --> F[Display Data Overview]
F --> G[Show Summary Statistics]
F --> H[Show Line Chart Preview]

G --> I[Preprocess Data<br/>Resample, Handle Missing Values]
H --> I

I --> J[Feature Engineering<br/>Raw Values or Log Returns]
J --> K[Standardize Data]

K --> L[User Selects Number of Regimes K]
L --> M[Click "Detect Regimes"]

M --> N[Train Hidden Markov Model]
N --> O[Infer Hidden State Sequence]

O --> P[Apply Regime Labeling Logic]
P --> Q[Compute Regime Statistics]
Q --> R[Generate Transition Insights]

R --> S[Store Results in Database]

S --> T[Display Regime Visualization]

T --> U[Show Color-Coded Time-Series Chart]
T --> V[Show Regime Summary Table]
T --> W[Show Transition Matrix]

U --> X{User Action}
V --> X
W --> X

X -- Change Regime Count --> L
X -- Retrain Model --> M
X -- Compare with Previous Model --> Y[Model Comparison View]
X -- Save Results --> Z[Save Session]
X -- Download Report --> AA[Export Report]
X -- Exit --> AB[End Session]

%% ---------------- STYLING ----------------

classDef user fill:#E3F2FD,stroke:#1565C0,stroke-width:3px,font-size:20px,font-weight:bold;
classDef system fill:#E8F5E9,stroke:#2E7D32,stroke-width:3px,font-size:20px,font-weight:bold;
classDef decision fill:#F3E5F5,stroke:#6A1B9A,stroke-width:3px,font-size:20px,font-weight:bold;

%% User Actions
class A,B,L,M,Y,Z,AA,AB user;

%% System Processing
class D,E,F,G,H,I,J,K,N,O,P,Q,R,S,T,U,V,W system;

%% Decision Points
class C,X decision;

```
