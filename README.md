# Demo

```mermaid
graph TD
    subgraph "User's Device"
        A[📱 Browser]
        B(🔊 Microphone)
    end

    subgraph "Frontend (Hosted on Netlify)"
        C{⚛️ React App UI}
        C_WC[Whistle Counter]
        C_T[Timer]
        C_M[Music Player]
        C_R[Recipe Helper]
        C_H[Dish Horoscope]
        C_Chat[Ask Kunjuttan]
    end

    subgraph "Backend (Hosted on Render)"
        D(⚙️ Node.js Server)
        D_R[/api/ai-recipe]
        D_H[/api/dish-horoscope]
    end

    subgraph "External Services"
        E(🧠 Google AI API)
    end

    %% User Interactions
    A -->|Interacts with| C

    %% Whistle Counter Flow (Frontend Only)
    B -->|Audio Stream| C_WC
    C -->|Controls| C_WC
    style C_WC fill:#fecb2e

    %% Timer & Music Flow (Frontend Only)
    C -->|Controls| C_T
    C -->|Controls| C_M
    style C_T fill:#94e245
    style C_M fill:#9e63f5

    %% AI-Powered Flows (Frontend -> Backend -> AI)
    C -->|Requests Recipe| C_R
    C_R -->|POST Request| D_R
    D_R -->|Sends Prompt| E
    E -->|Returns Recipe JSON| D_R
    D_R -->|Forwards JSON| C_R
    C_R -->|Updates UI| C
    style C_R fill:#4f8eff

    C -->|Requests Horoscope| C_H
    C_H -->|POST Request| D_H
    D_H -->|Sends Prompt| E
    E -->|Returns Horoscope JSON| D_H
    D_H -->|Forwards JSON| C_H
    C_H -->|Updates UI| C
    style C_H fill:#f77062

    %% Chat Flow (Frontend Only)
    C -->|Opens Chat| C_Chat
    style C_Chat fill:#2bd0d0
```
