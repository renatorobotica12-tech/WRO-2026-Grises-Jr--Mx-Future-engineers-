```mermaid
flowchart TD
    A[Start] --> B[Capture Frame]
    B --> C[Detect Object]
    C --> D{Object Detected?}
    
    D -- Yes --> E[Get Object Position]
    E --> F[Calculate Error]
    F --> G[Apply PID Correction]
    G --> H[Adjust Steering]
    H --> I[Move Forward]
    
    D -- No --> J[Maintain Last Steering]
    J --> I
    
    I --> B
```
---
