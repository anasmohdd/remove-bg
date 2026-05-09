# CutOut — AI Background Remover

A polished, full-stack SaaS web app for removing image backgrounds with AI.
Built with **React + Vite** (frontend) and **Node.js + Express** (backend).

---

## ✦ Features

- **AI Background Removal** — powered by remove.bg API
- **Crop Tool** — select any part of the processed image
- **Background Color Picker** — transparent, preset colors, or custom hex
- **Before / After Preview** — compare original vs result
- **PNG Download** — full-quality with transparency
- **Secure** — API key lives only on the server, never exposed to the browser
- **Graceful error handling** — friendly messages for all API errors
- **Responsive** — works on desktop, tablet, and mobile

---

## 📁 Folder Structure

```
bgremover/
├── client/                      # React + Vite frontend
│   ├── public/
│   ├── src/
│   │   ├── components/
│   │   │   ├── Header.jsx       # Navigation bar
│   │   │   ├── Hero.jsx         # Landing hero section
│   │   │   ├── UploadZone.jsx   # Drag-and-drop upload + preview
│   │   │   ├── Editor.jsx       # Crop tool + background color picker
│   │   │   ├── ResultPreview.jsx# Before/after + download
│   │   │   ├── Toast.jsx        # Notification component
│   │   │   └── Footer.jsx       # Footer
│   │   ├── App.jsx              # Main app + state management
│   │   ├── main.jsx             # Entry point
│   │   └── index.css            # Global styles + design tokens
│   ├── index.html
│   ├── vite.config.js           # Vite config with API proxy
│   └── package.json
│
├── server/                      # Node.js + Express backend
│   ├── routes/
│   │   └── remove.js            # POST /api/remove-bg route
│   ├── index.js                 # Server entry point
│   ├── .env.example             # Environment variable template
│   └── package.json
│
└── README.md
```

---

## 🚀 Quick Start

### Step 1 — Get a free remove.bg API key

1. Go to [https://www.remove.bg/api](https://www.remove.bg/api)
2. Sign up for a free account (50 API calls/month, no credit card)
3. Copy your API key from the dashboard

---

### Step 2 — Set up the backend

```bash
# Navigate to server folder
cd bgremover/server

# Install dependencies
npm install

# Create .env file from example
cp .env.example .env

# Open .env and add your API key
# REMOVE_BG_API_KEY=your_actual_key_here

# Start the server
npm run dev
```

The server will start on **http://localhost:4000**

---

### Step 3 — Set up the frontend

```bash
# Open a new terminal
cd bgremover/client

# Install dependencies
npm install

# Start the dev server
npm run dev
```

The app will open on **http://localhost:5173**

---

## 🔧 Environment Variables

| Variable             | Required | Default                     | Description                        |
|----------------------|----------|-----------------------------|------------------------------------|
| `REMOVE_BG_API_KEY`  | ✅ Yes    | —                           | Your remove.bg API key             |
| `PORT`               | No        | `4000`                      | Express server port                |
| `CLIENT_URL`         | No        | `http://localhost:5173`     | Allowed CORS origin (for frontend) |

---

## 🏗️ How It Works

```
User uploads image
      ↓
Frontend sends file to  POST /api/remove-bg  (multipart/form-data)
      ↓
Express receives file in memory (multer)
      ↓
Server calls remove.bg API with API key (secure — never sent to browser)
      ↓
remove.bg returns processed PNG (binary)
      ↓
Server converts to base64 data URL and sends to frontend
      ↓
Frontend displays result in editor (crop + color)
      ↓
User downloads final PNG
```

---

## 📦 Production Build

```bash
# Build frontend
cd client
npm run build
# Output: client/dist/

# For production, serve dist/ with a static file server or CDN
# and run the Express server with: npm start
```

---

## 🎨 Tech Stack

| Layer     | Technology         |
|-----------|--------------------|
| Frontend  | React 18, Vite 5   |
| Styling   | Pure CSS (no Tailwind) |
| Crop Tool | react-easy-crop    |
| HTTP      | Axios              |
| Backend   | Node.js, Express 4 |
| File upload | Multer           |
| BG removal| remove.bg API      |

---


