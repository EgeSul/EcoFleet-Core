# EcoFleet-Core: Environmental Vehicle Tracking & Fleet Management

![Python](https://img.shields.io/badge/Python-3.11+-blue.svg)
![FastAPI](https://img.shields.io/badge/Framework-FastAPI-009688.svg)
![Frontend](https://img.shields.io/badge/Map-Leaflet.js-brightgreen.svg)
![License](https://img.shields.io/badge/License-MIT-yellow.svg)

An eco-conscious fleet management and live vehicle tracking architecture developed for Muğla Water and Sewerage Administration (MUSKİ). Engineered to monitor real-time geolocation data, prevent idle fuel consumption, and optimize field operations to reduce the institutional carbon footprint.

---

## 🏗️ System Architecture & Real-Time Data Flow

```mermaid
flowchart TD
    subgraph Mobile Client ["Driver's Phone (Mobile Web / PWA)"]
        GPS[HTML5 Geolocation API]
        Sender[Async Fetch POST]
        GPS -->|Lat, Lng, VehicleID, Speed| Sender
    end

    subgraph Backend Engine ["Python API (FastAPI)"]
        Receiver[REST Endpoint: /api/track]
        Processor[Data Validation & Structuring]
        Sender -->|JSON Payload every 5s| Receiver
        Receiver --> Processor
    end

    subgraph Operations Center ["Dashboard (Leaflet.js)"]
        Map[Live Map UI]
        Processor -->|WebSocket / Polling| Map
    end
```
## 🚀 3-Day MVP Features

 * Real-Time Geolocation Tracking: Streams live GPS coordinates from the driver's smartphone directly to the backend.
 * Eco-Metrics & Idle Detection: Baseline architecture designed to monitor unnecessary engine idling and route deviations.
 * Work Order Integration Ready: Modular data structure prepared for upcoming task assignment features.
 * Hardware-Free: Relies entirely on the drivers' existing mobile devices without requiring costly OBD2 GPS trackers.

## 📂 Quick Start

 * Clone the repository: ``` git clone https://github.com/YourUsername/EcoFleet-Core.git ```

 * Install dependencies: ``` pip install fastapi uvicorn pydantic ```

 * Boot the backend engine: ``` uvicorn main:app --reload ```
