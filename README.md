graph LR

%% ====== USER ======
A[User Device 💻/📱] --> B[Browser UI]

%% ====== FRONTEND ======
subgraph FRONTEND["Frontend (React on Netlify)"]
    B --> C1[🎯 Whistle Counter]
    B --> C2[⏱️ Timer]
    B --> C3[🎵 Music Player]
    B --> C4[🥗 Recipe Helper]
    B --> C5[🔮 Dish Horoscope]
    B --> C6[💬 Ask Kunjuttan]
end

%% ====== BACKEND ======
subgraph BACKEND["Backend (Node.js on Render)"]
    D1["/api/ai-recipe"]
    D2["/api/dish-horoscope"]
end

%% ====== EXTERNAL ======
subgraph EXTERNAL["External Service"]
    E[🧠 Google AI API]
end

%% ==== FLOWS ====

%% Recipe Flow
C4 -->|POST Request| D1 -->|Prompt| E -->|Recipe Data| D1 --> C4

%% Horoscope Flow
C5 -->|POST Request| D2 -->|Prompt| E -->|Horoscope Data| D2 --> C5

%% Whistle Counter, Timer, Music, Chat stay frontend only
C1 -.->|Microphone Input| B
C2 --> B
C3 --> B
C6 -->|Local or API Chat| B
