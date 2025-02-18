# System Architecture Diagrams for Autonomous Driving Models

This document presents system architecture diagrams for three autonomous driving models: **QCNet, DrivingDiffusion, and EMMA**. The diagrams are created using **Mermaid** syntax.

## 1. QCNet: Query-Centric Trajectory Prediction

```mermaid
graph TD
    A[Agent States, Map Data] --> B(Query-Centric Encoder)
    B --> C(Factorized Attention)
    C --> D[Temporal Attention]
    C --> E[Agent-Map Attention]
    C --> F[Social Attention]
    D --> G
    E --> G
    F --> G(Caching Mechanism)
    G --> H(Query-Based Trajectory Decoder)
    H --> I(Anchor-Free Trajectory Proposal)
    
    subgraph Refinement
        I --> J[Mode2Scene Attention]
        I --> K[Mode2Mode Self-Attention]
        J --> L
        K --> L(Recurrent Generation)
        L --> M(Anchor-Based Refinement)
    end

    M --> N[Trajectory Offset Prediction]
    N --> O[Likelihood Estimation]
    O --> P(Output: K Future Trajectories)
```

## 2. DrivingDiffusion: Multi-View Video Generation

```mermaid
graph TD
    A[3D Layout, Text Descriptions] --> B(Multi-View Single-Frame Image Generation)
    B --> C[3D Layout Controller]
    C --> D(Cross-View Attention)
    
    subgraph Temporal Processing
        D --> E(Local Prompt Module)
        E --> F(Single-View Temporal Model)
        F --> G[Key-Frame Controller]
        G --> H[Optical Flow Prior]
    end
    
    H --> I(Post-Processing)
    I --> J[Fine-Tune Multi-View Model]
    J --> K(Sliding Window)
    K --> L(Output: Multi-View Video)
```

## 3. EMMA: End-to-End Multimodal Model for Autonomous Driving

```mermaid
graph TD
    A[Surround-View Cameras, Router Command, Ego Vehicle Status] --> B(Gemini-based EMMA)
    B --> C[Vision Encoding]
    B --> D[Text Encoding]
    C --> F
    D --> F
    B --> E(Chain-of-Thought Reasoning - Optional)
    E --> F(Task-Specific Output Generation)
    F --> G[Motion Planning]
    F --> H[3D Object Detection]
    F --> I[Road Graph Estimation]
    F --> J[Scene Understanding]
    G --> K
    H --> K
    I --> K
    J --> K(Output: Trajectories, Objects, Road Graph)
```
