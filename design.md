# GramSutra AI – System Design Document

## 1. System Architecture

The system follows a Microservices Architecture.

Frontend → API Gateway → Backend Services → AI Engine → Database

---

## 2. High-Level Architecture Components

1. Mobile App (React Native)
2. Web App (Next.js)
3. API Gateway (FastAPI)
4. AI Microservices (Python, TensorFlow, PyTorch)
5. Database (PostgreSQL + PostGIS)
6. Cache (Redis)
7. Object Storage (AWS S3)
8. Voice Integration (Twilio + Web Speech API)

---

## 3. Frontend Design

### 3.1 UI Principles

- Large buttons
- Minimal UI
- Voice-first design
- Offline caching support
- Multi-language support

---

### 3.2 Main Screens

1. Login Page
   - Mobile number input
   - OTP verification
   - Language selection

2. Dashboard
   - Sustainability score card
   - Weather alert widget
   - Market price snapshot
   - Water advisory

3. Crop Planner
   - Input form
   - Recommendation result page

4. Analytics Page
   - Water usage graph
   - Income forecast graph
   - Carbon impact

---

## 4. Backend Architecture

### 4.1 API Layer (FastAPI)

Endpoints:

POST /auth/login
POST /auth/verify-otp
GET /weather/{location}
POST /crop/recommend
GET /market/prices
POST /sustainability/score
POST /voice/query

---

### 4.2 AI Services

1. Crop Recommendation Model
   - Random Forest Classifier
2. Yield Prediction
   - LSTM Model
3. Price Forecasting
   - Time-Series LSTM / Prophet
4. Water Demand Prediction
   - Regression Model
5. Sustainability Scoring Engine
   - Weighted scoring algorithm

AI services run as independent microservices.

---

## 5. Database Schema (Simplified)

### Users Table
- id
- name
- mobile
- role
- language
- created_at

### Farm Profile Table
- user_id
- land_size
- soil_type
- irrigation_type
- location

### Crop Recommendations Table
- user_id
- crop_name
- predicted_yield
- sustainability_score
- risk_score
- created_at

### Weather Data Table
- location
- temperature
- rainfall
- humidity
- timestamp

### Market Prices Table
- crop_name
- mandi_name
- price
- date

---

## 6. Data Flow

1. User logs in.
2. User inputs farm details.
3. API sends request to AI service.
4. AI processes:
   - Climate data
   - Soil data
   - Water model
   - Market data
5. Sustainability engine calculates score.
6. Results returned to frontend.

---

## 7. Deployment Architecture

- Docker containerized services.
- Hosted on AWS EC2 or Azure VM.
- PostgreSQL on managed RDS.
- S3 for storage.
- CI/CD via GitHub Actions.
- Nginx reverse proxy.

---

## 8. Scalability Strategy

- Stateless backend services.
- Load balancer.
- Horizontal scaling.
- Redis caching.
- API throttling.

---

## 9. Monitoring & Logging

- Prometheus for metrics.
- Grafana dashboards.
- Centralized logging (ELK stack).

---

## 10. Disaster Recovery

- Daily automated backups.
- Multi-zone deployment.
- Failover database replication.

---

## 11. Future System Expansion

- IoT sensor integration.
- Satellite imagery integration.
- Blockchain layer for traceability.
- Carbon marketplace module.

