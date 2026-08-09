# Industrial Safety Intelligence Platform (ISIP)

## Overview

ISIP is an AI-powered industrial safety monitoring system that combines sensor data, computer vision, machine learning, and compliance management to create a comprehensive safety intelligence platform.

### Key Features

✅ **Real-time Risk Assessment** - Compound risk calculation using multiple factors
✅ **Computer Vision Integration** - YOLOv8 for PPE detection and safety monitoring
✅ **Predictive Analytics** - ML-based risk prediction and anomaly detection
✅ **Compliance Assistant** - RAG-powered system for safety regulations
✅ **IoT Integration** - Real-time sensor data processing (temperature, gas, pressure, etc.)
✅ **WebSocket Updates** - Live dashboard updates and alerts
✅ **Multi-role Access** - Admin, Supervisor, Operator, Auditor roles
✅ **Dark Mode UI** - Modern, responsive dashboard

---

## Architecture

```
┌─────────────────────────────────────────────────────┐
│          Frontend (React + Vite)                    │
│  Dashboard | Sensors | Alerts | Incidents | Permits│
│  Analytics | Compliance | Settings                 │
└──────────────────┬──────────────────────────────────┘
                   │ REST API + WebSocket
                   ▼
┌─────────────────────────────────────────────────────┐
│    Backend (FastAPI + SQLAlchemy)                   │
├─────────────────────────────────────────────────────┤
│ Routes: Auth | Dashboard | Sensors | Alerts |       │
│         Incidents | Permits | Predictions | Compliance
└──────────────────┬──────────────────────────────────┘
                   │
        ┌──────────┼──────────┐
        ▼          ▼          ▼
    ┌────────┐ ┌────────┐ ┌────────┐
    │ Risk   │ │Computer│ │ML      │
    │ Engine │ │ Vision │ │ Model  │
    └────────┘ └────────┘ └────────┘
        │          │          │
        └──────────┼──────────┘
                   ▼
┌─────────────────────────────────────────────────────┐
│    AI/ML Modules                                    │
│  Risk Engine | CV Engine | ML Predictor | RAG      │
│  IoT Simulator                                      │
└──────────────────┬──────────────────────────────────┘
                   │
                   ▼
┌─────────────────────────────────────────────────────┐
│    Database (SQLite/PostgreSQL)                     │
│  Users | Sensors | Alerts | Incidents | Permits    │
│  Predictions | Compliance Documents                │
└─────────────────────────────────────────────────────┘
```

---

## Setup & Installation

### Prerequisites

- Python 3.11+
- Node.js 18+
- Docker & Docker Compose (optional)

### Local Setup

#### Backend

```bash
# Navigate to project root
cd industrial-safety-platform

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Run backend
python -m uvicorn backend.app.main:app --reload --host 0.0.0.0 --port 8000
```

#### Frontend

```bash
# In a new terminal, navigate to frontend
cd frontend

# Install dependencies
npm install

# Run frontend
npm run dev
```

Access the application at `http://localhost:5173`

### Docker Setup

```bash
# Build and run with Docker Compose
docker-compose up --build

# Access
# Frontend: http://localhost:5173
# Backend: http://localhost:8000
# API Docs: http://localhost:8000/docs
```

---

## Demo Credentials

| Role | Username | Password |
|------|----------|----------|
| Admin | admin | admin123 |
| Supervisor | supervisor | super123 |
| Operator | operator | operator123 |
| Auditor | auditor | auditor123 |

---

## API Endpoints

### Authentication
- `POST /api/auth/login` - Login
- `POST /api/auth/register` - Register
- `GET /api/auth/me` - Get current user

### Dashboard
- `GET /api/dashboard/stats` - Get dashboard statistics
- `GET /api/dashboard/risk-metrics` - Get risk metrics

### Sensors
- `GET /api/sensors/readings` - Get sensor readings
- `GET /api/sensors/stats` - Get sensor statistics
- `POST /api/sensors/reading` - Create sensor reading

### Alerts
- `GET /api/alerts/` - Get alerts
- `GET /api/alerts/{id}` - Get alert details
- `POST /api/alerts/acknowledge/{id}` - Acknowledge alert
- `POST /api/alerts/resolve/{id}` - Resolve alert

### Incidents
- `GET /api/incidents/` - Get incidents
- `POST /api/incidents/` - Create incident
- `PUT /api/incidents/{id}` - Update incident
- `POST /api/incidents/{id}/resolve` - Resolve incident

### Permits
- `GET /api/permits/` - Get permits
- `POST /api/permits/` - Create permit
- `POST /api/permits/{id}/revoke` - Revoke permit

### Predictions
- `GET /api/predictions/predict` - Get risk prediction
- `GET /api/predictions/history` - Get prediction history

### Compliance
- `POST /api/compliance/upload` - Upload compliance document
- `POST /api/compliance/query` - Query compliance (RAG)
- `GET /api/compliance/search` - Search compliance documents

---

## AI/ML Components

### 1. Risk Engine

Compound risk calculation considering:
- Temperature variations
- Gas concentration levels
- Pressure deviations
- Smoke detection
- Helmet compliance rate
- Permit status
- Machine failures
- Worker density

**Risk Levels:**
- 🟢 Green (< 30): Safe
- 🟡 Yellow (30-60): Warning
- 🟠 Orange (60-80): High Risk
- 🔴 Red (> 80): Critical

### 2. Computer Vision

YOLOv8-based detection for:
- Personal protective equipment (PPE)
- Helmet wearing compliance
- Safety vest detection
- Unauthorized zone entry
- Fire and smoke detection
- Worker density monitoring

### 3. Machine Learning Predictor

Random Forest classifier for:
- Risk level prediction (Safe/Warning/Critical)
- Confidence scoring
- Feature importance analysis

### 4. RAG System

Retrieve Augmented Generation for:
- Fire safety procedures
- PPE requirements
- Confined space entry
- Electrical safety
- First aid response
- Incident reporting

### 5. IoT Simulator

Generates realistic sensor data:
- Temperature readings
- Pressure variations
- Gas concentrations
- Humidity levels
- Smoke detection
- Vibration monitoring
- Power usage tracking

---

## Features

### Dashboard
- Real-time risk score gauge
- Active alerts counter
- Incident tracking
- Worker density monitoring
- Machine health status
- Environmental conditions
- Risk heatmap by zone
- Emergency mode activation

### Sensor Management
- Real-time sensor readings
- Multi-zone monitoring (A, B, C, D)
- Sensor status tracking
- Historical data visualization
- Anomaly detection

### Alert System
- Priority-based (Critical, Warning, Info)
- Zone-specific alerts
- Risk score calculation
- Alert acknowledgment
- Resolution tracking
- Automated recommendations

### Incident Management
- Incident creation and tracking
- Severity classification (Low, Medium, High, Critical)
- Status management (Open, In Progress, Resolved, Closed)
- Root cause analysis
- Resolution documentation

### Permit Management
- Hot work permits
- Electrical work permits
- Confined space permits
- Height work permits
- Permit lifecycle tracking
- Expiration alerts

### Analytics & Reporting
- Risk trend analysis
- Incident frequency charts
- Violation statistics
- Compliance metrics
- KPI dashboards

### Compliance Assistant
- AI-powered Q&A system
- Document management
- Regulation search
- Safety procedure lookup
- Multi-document support

---

## File Structure

```
industrial-safety-platform/
├── backend/
│   ├── app/
│   │   ├── main.py
│   │   ├── core/
│   │   │   ├── config.py
│   │   │   ├── database.py
│   │   │   ├── security.py
│   │   │   └── websocket.py
│   │   ├── models/
│   │   │   ├── user.py
│   │   │   ├── sensor.py
│   │   │   ├── alert.py
│   │   │   ├── incident.py
│   │   │   ├── permit.py
│   │   │   ├── prediction.py
│   │   │   └── compliance.py
│   │   ├── schemas/
│   │   │   ├── auth.py
│   │   │   ├── dashboard.py
│   │   │   ├── sensor.py
│   │   │   ├── alert.py
│   │   │   ├── incident.py
│   │   │   ├── permit.py
│   │   │   ├── prediction.py
│   │   │   └── compliance.py
│   │   └── api/
│   │       └── routes/
│   │           ├── auth.py
│   │           ├── dashboard.py
│   │           ├── sensors.py
│   │           ├── alerts.py
│   │           ├── incidents.py
│   │           ├── permits.py
│   │           ├── predictions.py
│   │           └── compliance.py
│   └── ai/
│       ├── risk_engine.py
│       ├── computer_vision.py
│       ├── ml_predictor.py
│       ├── rag_system.py
│       └── iot_simulator.py
├── frontend/
│   ├── src/
│   │   ├── main.tsx
│   │   ├── App.tsx
│   │   ├── index.css
│   │   ├── services/
│   │   │   └── api.ts
│   │   ├── components/
│   │   │   ├── Layout.tsx
│   │   │   ├── Charts.tsx
│   │   │   ├── AlertBanner.tsx
│   │   │   ├── AlertsPanel.tsx
│   │   │   └── Heatmap.tsx
│   │   └── pages/
│   │       ├── Login.tsx
│   │       ├── Dashboard.tsx
│   │       ├── Sensors.tsx
│   │       ├── Alerts.tsx
│   │       ├── Incidents.tsx
│   │       ├── Permits.tsx
│   │       ├── Analytics.tsx
│   │       ├── Compliance.tsx
│   │       └── Settings.tsx
│   ├── index.html
│   ├── package.json
│   ├── tsconfig.json
│   ├── vite.config.ts
│   ├── tailwind.config.js
│   └── postcss.config.js
├── docker/
│   ├── Dockerfile.backend
│   └── Dockerfile.frontend
├── docker-compose.yml
├── requirements.txt
├── .env.example
└── README.md
```

---

## Tech Stack

### Backend
- **Framework:** FastAPI
- **Database:** SQLAlchemy + SQLite/PostgreSQL
- **AI/ML:** scikit-learn, PyYAML, NumPy, Pandas
- **Computer Vision:** YOLO v8, OpenCV
- **RAG:** LangChain, ChromaDB, Sentence Transformers
- **Authentication:** JWT + bcrypt
- **WebSocket:** python-socketio

### Frontend
- **Framework:** React 19 + TypeScript
- **Build Tool:** Vite
- **Styling:** Tailwind CSS
- **Charts:** Recharts
- **Maps:** React Leaflet
- **State Management:** Zustand
- **HTTP Client:** Axios
- **UI Icons:** Lucide React

### DevOps
- **Containerization:** Docker
- **Orchestration:** Docker Compose
- **Package Manager:** pip (Python), npm (Node)

---

## Performance Optimization

- Real-time data updates via WebSocket
- Efficient sensor data aggregation
- Caching strategy for compliance documents
- Lazy loading for analytics charts
- Database query optimization
- Frontend code splitting

---

## Security Features

- JWT-based authentication
- Password hashing with bcrypt
- CORS middleware
- SQL injection prevention
- Role-based access control
- Secure WebSocket connections

---

## Testing & Deployment

### Local Testing
```bash
pytest backend/tests/
npm test
```

### Production Deployment
```bash
docker-compose -f docker-compose.yml up -d
```

---

## Future Enhancements

- [ ] Real camera feed integration
- [ ] SMS/Email notifications
- [ ] Advanced ML models (LSTM, GRU)
- [ ] Multi-language support
- [ ] Mobile app (React Native)
- [ ] Advanced reporting engine
- [ ] Integration with existing SCADA systems
- [ ] Blockchain for incident audit trail

---

## Contributing

Contributions are welcome! Please follow the code style guide and submit PRs with clear descriptions.

---

## License

MIT License - See LICENSE file for details

---

## Support

For issues, questions, or suggestions:
- Open an issue on GitHub
- Contact: hemanth1921@gmail.com

---

**Built for ET AI Hackathon 2.0**
