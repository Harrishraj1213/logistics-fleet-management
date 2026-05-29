# AI-Based Logistics & Fleet Management Platform

## 🚀 Production-Grade MERN Stack with Microservices Architecture

A comprehensive logistics and fleet management solution built with modern technologies, featuring real-time vehicle tracking, AI-powered route optimization, automated billing, and complete fleet analytics.

### ✨ Key Features

#### 1. **Real-Time Vehicle Tracking**
- Live GPS tracking with Google Maps integration
- Vehicle status monitoring
- ETA calculation
- Route history and playback
- Geo-fencing support

#### 2. **AI-Powered Features**
- Route prediction and optimization
- Delivery delay prediction using LSTM
- Traffic analysis
- Fuel consumption forecasting
- Smart route suggestions

#### 3. **Driver Analytics**
- Performance dashboard
- Speed analysis
- Harsh braking detection
- Idle time monitoring
- Safety scoring

#### 4. **Fleet Management**
- Vehicle inventory tracking
- Maintenance scheduling
- Fuel monitoring and anomaly detection
- Mileage reports

#### 5. **Warehouse Management**
- Inventory tracking
- Shipment assignment
- Order management
- Barcode/QR code support

#### 6. **Automated Billing**
- Invoice generation
- GST calculation
- Delivery-based billing
- Subscription plans
- PDF downloads

#### 7. **Payment Integration**
- Razorpay (Mandatory)
- Stripe (Optional)
- Payment history
- Webhook verification

#### 8. **Notifications**
- Real-time WebSocket notifications
- Email notifications
- SMS placeholder
- Push notifications

### 🏗️ System Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                     Frontend (React + Vite)                  │
│            Responsive UI with Dark/Light Mode               │
└──────────────────────┬──────────────────────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────────────────────┐
│              API Gateway (Express.js)                         │
│         Rate Limiting | Auth | Request Routing              │
└──────────────────────┬──────────────────────────────────────┘
                       │
      ┌────────────────┼────────────────┬────────────────┐
      │                │                │                │
      ▼                ▼                ▼                ▼
┌──────────────┐ ┌──────────────┐ ┌──────────────┐ ┌──────────────┐
│ Auth Service │ │Tracking Svc  │ │ Billing Svc  │ │Notification │
│ (Port 3001)  │ │ (Port 3002)  │ │ (Port 3003)  │ │ (Port 3004)  │
└──────────────┘ └──────────────┘ └──────────────┘ └──────────────┘
      │                │                │                │
      │                ▼                │                │
      │         ┌──────────────┐        │                │
      │         │ Redis Cache  │        │                │
      │         └──────────────┘        │                │
      │                                  │                │
      └─────────────────┬────────────────┴────────────────┘
                        │
                        ▼
              ┌──────────────────┐
              │   MongoDB        │
              │  (Multiple DBs)  │
              └──────────────────┘
                        │
                        ▼
              ┌──────────────────┐
              │  AI Service      │
              │  (Python FastAPI)│
              │  Port 8000       │
              └──────────────────┘
```

### 📁 Project Structure

```
logistics-fleet-management/
├── frontend/                          # React + Vite Frontend
│   ├── src/
│   │   ├── components/               # Reusable components
│   │   ├── pages/                    # Page components
│   │   ├── hooks/                    # Custom React hooks
│   │   ├── store/                    # Zustand state management
│   │   ├── services/                 # API services
│   │   ├── types/                    # TypeScript interfaces
│   │   ├── utils/                    # Utility functions
│   │   ├── styles/                   # Tailwind CSS
│   │   └── App.jsx
│   ├── Dockerfile
│   └── package.json
│
├── backend/
│   ├── gateway/                       # API Gateway
│   ├── auth-service/                  # Authentication Service
│   ├── tracking-service/              # Vehicle Tracking Service
│   ├── billing-service/               # Billing & Payment Service
│   ├── notification-service/          # Notification Service
│   └── scripts/
│       └── mongo-init.js
│
├── ai-service/                        # Python FastAPI Service
│   ├── app/
│   │   ├── models/
│   │   ├── routes/
│   │   ├── services/
│   │   └── main.py
│   ├── Dockerfile
│   └── requirements.txt
│
├── .github/workflows/
│   ├── ci.yml
│   └── deploy.yml
│
├── docker-compose.yml
├── nginx.conf
└── README.md
```

### 🛠️ Tech Stack

**Frontend:**
- React 18+
- Vite
- Tailwind CSS
- Zustand (State Management)
- React Query (Data Fetching)
- Socket.IO Client
- Google Maps API

**Backend:**
- Node.js
- Express.js
- MongoDB
- Redis
- Socket.IO
- JWT Authentication

**AI/ML:**
- Python
- FastAPI
- TensorFlow/Keras
- Scikit-learn

**DevOps:**
- Docker
- Docker Compose
- NGINX
- GitHub Actions

### 📋 Prerequisites

- Node.js 18+
- Python 3.9+
- Docker & Docker Compose
- Git

### 🚀 Quick Start

#### 1. Clone Repository
```bash
git clone https://github.com/Harrishraj1213/logistics-fleet-management.git
cd logistics-fleet-management
```

#### 2. Configure Environment
```bash
cp .env.example .env
# Edit .env with your credentials
```

#### 3. Start All Services
```bash
docker-compose up -d
```

#### 4. Access Application
- **Frontend:** http://localhost:5173
- **API Gateway:** http://localhost:3000/api
- **Swagger Docs:** http://localhost:3000/api-docs

### 🔐 Security Features

- JWT authentication with refresh tokens
- Password hashing with bcrypt
- CORS protection
- Rate limiting
- XSS protection (Helmet)
- CSRF protection
- Input validation and sanitization
- Role-Based Access Control (RBAC)

### 📈 Performance Optimizations

- Lazy loading components
- Code splitting with Vite
- Database indexing
- Redis caching
- Pagination
- Compression middleware

### 🐳 Docker Deployment

```bash
docker-compose build
docker-compose up -d
docker-compose logs -f
docker-compose down
```

### 📝 Database Collections

- Users (Authentication)
- Vehicles (Fleet Management)
- Routes (Navigation)
- Deliveries (Orders)
- FuelLogs (Fuel Monitoring)
- Analytics (Performance Data)
- Payments (Billing)
- Warehouses (Inventory)
- Notifications (Real-time)

### 📞 API Endpoints

**Auth Service:**
- `POST /api/v1/auth/register`
- `POST /api/v1/auth/login`
- `POST /api/v1/auth/refresh`
- `POST /api/v1/auth/logout`

**Tracking Service:**
- `GET /api/v1/vehicles`
- `POST /api/v1/vehicles`
- `GET /api/v1/vehicles/:id/location`
- `POST /api/v1/routes`

**Billing Service:**
- `POST /api/v1/payments`
- `GET /api/v1/payments`
- `POST /api/v1/invoices`
- `GET /api/v1/invoices`

**AI Service:**
- `POST /api/v1/ai/predict-route`
- `POST /api/v1/ai/predict-delay`
- `POST /api/v1/ai/predict-fuel`

### 📧 Support

For support, email: support@logisticsplatform.com

---

**Built with ❤️ for efficient logistics management**
