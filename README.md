# 🌐 God's Eye View

> **A real-time 3D planetary intelligence and situational awareness console running directly in the browser.**

[![Node.js](https://img.shields.io/badge/node-%3E%3D24.13-brightgreen.svg?style=flat-square)](https://nodejs.org/)
[![Vite](https://img.shields.io/badge/vite-6.x-646CFF.svg?style=flat-square&logo=vite)](https://vitejs.dev/)
[![CesiumJS](https://img.shields.io/badge/cesium-1.124-4B9CD3.svg?style=flat-square)](https://cesium.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](LICENSE)

**God's Eye View** fuses global open-source geospatial and telemetry streams into an interactive photorealistic 3D globe powered by **CesiumJS**. It combines real-time air traffic (ADS-B), maritime vessels (AIS), orbital satellite constellations, seismic activity, active thermal wildfires, street-level public surveillance cameras, and conversational AI voice navigation.

---

## ⚡ Quick Start

### 1. Prerequisites
- **Node.js** v24.13.0 or higher
- **npm** v11.0.0 or higher
- A modern browser with **WebGL 2.0** hardware acceleration enabled

### 2. Installation & Running

```bash
# Clone the repository
git clone https://github.com/sourabhkr1100/god-eye.git
cd god-eye

# Install dependencies
npm install

# Start the local development server
npm run dev
```

Open your browser and navigate to:
```
http://localhost:4173/
```

> **Note:** The application starts immediately without any paid API keys using high-resolution keyless fallbacks (Esri World Imagery, OpenSky flight positions, Launch Library 2 space missions, and built-in traffic simulation).

---

## 🛰️ Key Capabilities & Data Layers

| Domain | Source & Provider | Description |
| :--- | :--- | :--- |
| **3D Photorealistic Globe** | CesiumJS, Google 3D Tiles, Esri World Imagery | High-resolution 3D terrain, tilt, orbital camera controls, and custom shaders. |
| **Aviation / Air Traffic** | OpenSky Network, ADSB.lol | Live civilian and military flights with altitude, heading, velocity, and transponder records. |
| **Maritime Traffic** | AISStream | Live global vessel positioning, ship routes, and port traffic over WebSockets. |
| **Space & Satellites** | CelesTrak, Launch Library 2 | Real-time orbital propagation for Starlink, GPS, ISS, and upcoming rocket launches. |
| **Natural Disasters** | USGS, NASA FIRMS | Live global earthquakes, Richter magnitudes, and active thermal wildfire hotspots. |
| **Ground & Urban Intelligence** | Public HLS Streams, Radio Browser, GBFS | Public CCTV feeds, city bikeshare availability, and local regional radio audio. |
| **Conversational AI & Voice** | OpenAI Realtime, Gemini Live, MCP | Natural language hands-free voice control, camera positioning, and situational awareness Q&A. |

---

## 🔑 Environment Variables & Optional Keys

An example configuration file is provided in `.env.example`. You can configure keys either by creating a `.env` file or by using the interactive **POWER UP** button at the bottom-right of the web app:

```env
# Optional: Google Photorealistic 3D Tiles and Places API
GOOGLE_MAPS_API_KEY=
GOOGLE_MAPS_SERVER_API_KEY=

# Optional: Cesium ion token for assets and Cesium World Terrain
CESIUM_ION_TOKEN=

# Optional: Realtime voice control
OPENAI_API_KEY=
GEMINI_API_KEY=

# Optional: Realtime vessel tracking
AISSTREAM_API_KEY=

# Optional: NASA FIRMS active fires
FIRMS_MAP_KEY=

# Optional: TomTom live road traffic
TOMTOM_API_KEY=
```

---

## 🤖 Model Context Protocol (MCP) Integration

God's Eye View includes a built-in MCP server that allows AI assistants (Claude, Cursor, Codex, ChatGPT) to inspect and interact with planetary intelligence data.

To start the MCP server:
```bash
npm run mcp
```

Or connect it to Claude Desktop or Codex:
```json
{
  "mcpServers": {
    "god-eye": {
      "command": "node",
      "args": ["server/mcp/stdio.js", "--api-base", "http://localhost:4173"]
    }
  }
}
```

---

## 🛠️ Project Architecture

```
god-eye/
├── src/
│   ├── app/           # Core application lifecycle & viewer orchestration
│   ├── layers/        # Feeds (flights, vessels, satellites, fires, cctv, etc.)
│   ├── maps/          # Cesium 3D controllers, terrain, imagery catalog
│   ├── ui/            # Cockpit HUD, title bar, controls, and dialog templates
│   ├── voice/         # AI voice commands & realtime sessions
│   └── tools/         # Geospatial query tools & schemas
├── server/
│   ├── providers/     # Local caching and rate-limiting proxies (CORS & Auth)
│   ├── mcp/           # Model Context Protocol stdio & HTTP adapters
│   └── standalone/    # Standalone Vite plugins & middleware
├── public/            # Static 3D models, icons, and textures
└── index.html         # Application HTML entry point
```

---

## 📜 License & Attribution

- **Source Code**: Released under the [MIT License](LICENSE).
- **Maintainer**: [Sourabh](https://github.com/sourabhkr1100).
- **Disclaimer**: God's Eye View is an exploratory visualization platform utilizing public, academic, and commercial data streams. Data may be delayed or modeled. It is not intended for flight navigation, maritime steering, or emergency response.
