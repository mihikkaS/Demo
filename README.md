graph TD

%% ==== USER SIDE ====
subgraph "User's Device"
    A[💻 Browser]
    B(🎤 Microphone)
end

%% ==== FRONTEND ====
subgraph "Frontend (Netlify)"
    C{⚛️ React App UI}
    C_WC[🎯 Whistle Counter]
    C_T[⏱️ Timer]
    C_M[🎵 Music Player]
    C_R[🥗 Recipe Helper]
    C_H[🔮 Dish Horoscope]
    C_Chat[💬 Ask Kunjuttan]
end

%% ==== BACKEND ====
subgraph "Backend (Render)"
    D[⚙️ Node.js Server]
    D_R["/api/ai-recipe"]
    D_H["/api/dish-horoscope"]
end

%% ==== EXTERNAL ====
subgraph "External Services"
    E[🧠 Google AI API]
end

%% ==== FLOWS ====

%% User to UI
A -->|Interacts with UI| C
B -->|Audio Stream| C_WC

%% Whistle Counter
C --> C_WC
style C_WC fill:#ffeb99,stroke:#b58900,stroke-width:2px

%% Timer & Music
C --> C_T
C --> C_M
style C_T fill:#b3ffb3,stroke:#228B22,stroke-width:2px
style C_M fill:#d1b3ff,stroke:#6a0dad,stroke-width:2px

%% Recipe Flow
C -->|Request Recipe| C_R
C_R -->|POST| D_R
D_R -->|Send Prompt| E
E -->|Recipe JSON| D_R
D_R --> C_R
C_R -->|Update UI| C
style C_R fill:#99ccff,stroke:#005f99,stroke-width:2px

%% Horoscope Flow
C -->|Request Horoscope| C_H
C_H -->|POST| D_H
D_H -->|Send Prompt| E
E -->|Horoscope JSON| D_H
D_H --> C_H
C_H -->|Update UI| C
style C_H fill:#ffb3b3,stroke:#cc0000,stroke-width:2px

%% Chat Flow
C --> C_Chat
style C_Chat fill:#a7f0f0,stroke:#006666,stroke-width:2px
