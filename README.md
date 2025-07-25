# 🌱 SmartFarm Management System

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Node.js Version](https://img.shields.io/badge/node-%3E%3D18.0.0-brightgreen)](https://nodejs.org/)
[![React Version](https://img.shields.io/badge/react-%5E18.0.0-blue)](https://reactjs.org/)
[![MongoDB](https://img.shields.io/badge/MongoDB-4EA94B?logo=mongodb&logoColor=white)](https://www.mongodb.com/)
[![Express.js](https://img.shields.io/badge/express.js-%23404d59.svg?logo=express&logoColor=%2361DAFB)](https://expressjs.com/)

> A comprehensive MERN stack application that empowers farmers with data-driven insights, smart crop management, and real-time monitoring capabilities.

![SmartFarm Dashboard](https://via.placeholder.com/800x400/4CAF50/FFFFFF?text=SmartFarm+Dashboard+Screenshot)

## 🚀 Features

### 🌾 **Smart Crop Management**
- Real-time crop monitoring and growth tracking
- Automated planting schedules and harvest predictions
- Pest and disease detection with treatment recommendations
- Yield optimization through data analytics

### 🌤️ **Weather Integration**
- Live weather data and 7-day forecasts
- Weather-based farming recommendations
- Automated irrigation alerts
- Climate trend analysis

### 📊 **IoT Sensor Dashboard**
- Real-time soil moisture, pH, and temperature monitoring
- Automated alerts and notifications
- Historical data visualization
- Predictive analytics for optimal farming conditions

### 💰 **Market Intelligence**
- Real-time crop price tracking
- Market trend analysis and predictions
- Profit optimization recommendations
- Direct buyer-seller connectivity

### 📈 **Advanced Analytics**
- Farm performance metrics
- Cost-benefit analysis
- Seasonal trend predictions
- Custom reporting dashboard

## 🛠️ Tech Stack

### Frontend
- **React 18** with TypeScript
- **Material-UI** for modern, responsive design
- **Redux Toolkit** for state management
- **React Query** for server state management
- **Chart.js** for data visualization
- **Leaflet** for interactive maps

### Backend
- **Node.js** with Express.js
- **MongoDB** with Mongoose ODM
- **JWT** authentication
- **Socket.io** for real-time updates
- **Multer** for file uploads
- **Node-cron** for scheduled tasks

### External Services
- **OpenWeatherMap API** for weather data
- **Cloudinary** for image storage
- **Twilio** for SMS notifications
- **Stripe** for payment processing

## 📁 Project Structure

```
smartfarm-management/
├── 📁 backend/                 # Node.js/Express API
│   ├── 📁 src/
│   │   ├── 📁 controllers/     # Route controllers
│   │   ├── 📁 models/          # MongoDB schemas
│   │   ├── 📁 routes/          # API routes
│   │   ├── 📁 middleware/      # Custom middleware
│   │   ├── 📁 services/        # Business logic
│   │   └── 📁 utils/           # Helper functions
│   ├── 📁 tests/              # Backend tests
│   └── 📄 package.json
│
├── 📁 frontend/               # React application
│   ├── 📁 src/
│   │   ├── 📁 components/     # Reusable components
│   │   ├── 📁 pages/          # Page components
│   │   ├── 📁 store/          # Redux store
│   │   ├── 📁 services/       # API services
│   │   ├── 📁 hooks/          # Custom hooks
│   │   └── 📁 utils/          # Helper functions
│   ├── 📁 public/             # Static assets
│   └── 📄 package.json
│
├── 📁 docs/                   # Documentation
├── 📁 .github/               # GitHub workflows
├── 📄 docker-compose.yml     # Development environment
├── 📄 README.md              # Project documentation
└── 📄 LICENSE                # MIT License
```

## 🚀 Quick Start

### Prerequisites
- Node.js (v18 or higher)
- MongoDB (v5.0 or higher)
- npm or yarn package manager

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/smartfarm-management.git
   cd smartfarm-management
   ```

2. **Install backend dependencies**
   ```bash
   cd backend
   npm install
   ```

3. **Install frontend dependencies**
   ```bash
   cd ../frontend
   npm install
   ```

4. **Environment Setup**
   
   Create `.env` files in both backend and frontend directories:
   
   **Backend (.env)**
   ```env
   NODE_ENV=development
   PORT=5000
   MONGODB_URI=mongodb://localhost:27017/smartfarm
   JWT_SECRET=your-super-secret-jwt-key
   CLOUDINARY_URL=cloudinary://api_key:api_secret@cloud_name
   WEATHER_API_KEY=your-openweathermap-api-key
   TWILIO_ACCOUNT_SID=your-twilio-sid
   TWILIO_AUTH_TOKEN=your-twilio-token
   ```
   
   **Frontend (.env)**
   ```env
   REACT_APP_API_URL=http://localhost:5000/api
   REACT_APP_WEATHER_API_KEY=your-weather-api-key
   REACT_APP_GOOGLE_MAPS_KEY=your-google-maps-key
   ```

5. **Start the development servers**
   ```bash
   # Terminal 1 - Backend
   cd backend
   npm run dev
   
   # Terminal 2 - Frontend
   cd frontend
   npm start
   ```

6. **Access the application**
   - Frontend: http://localhost:3000
   - Backend API: http://localhost:5000/api
   - API Documentation: http://localhost:5000/api-docs

## 🧪 Testing

### Backend Testing
```bash
cd backend
npm test                    # Run all tests
npm run test:watch         # Run tests in watch mode
npm run test:coverage      # Generate coverage report
```

### Frontend Testing
```bash
cd frontend
npm test                   # Run component tests
npm run test:e2e          # Run Cypress E2E tests
```

## 🐳 Docker Development

Run the entire application with Docker:

```bash
docker-compose up --build
```

This will start:
- MongoDB database
- Backend API server
- Frontend React app
- Redis for caching

## 📱 API Documentation

### Authentication Endpoints
```
POST   /api/auth/register     # User registration
POST   /api/auth/login        # User login
GET    /api/auth/profile      # Get user profile
POST   /api/auth/refresh      # Refresh JWT token
```

### Farm Management
```
GET    /api/farms            # Get all farms
POST   /api/farms            # Create new farm
GET    /api/farms/:id        # Get specific farm
PUT    /api/farms/:id        # Update farm
DELETE /api/farms/:id        # Delete farm
```

### Crop Management
```
GET    /api/crops            # Get all crops
POST   /api/crops            # Add new crop
PUT    /api/crops/:id        # Update crop
POST   /api/crops/:id/stage  # Update growth stage
```

For complete API documentation, visit `/api-docs` when running the backend server.

## 🚀 Deployment

### Production Deployment

1. **Backend (Heroku/Railway)**
   ```bash
   # Build and deploy
   npm run build
   git push heroku main
   ```

2. **Frontend (Netlify/Vercel)**
   ```bash
   # Build for production
   npm run build
   
   # Deploy to Netlify
   netlify deploy --prod --dir=build
   ```

3. **Database (MongoDB Atlas)**
   - Create a cluster on MongoDB Atlas
   - Update `MONGODB_URI` in production environment

### Environment Variables for Production
Make sure to set all required environment variables in your deployment platform.

## 🤝 Contributing

We welcome contributions! Please see our [Contributing Guide](CONTRIBUTING.md) for details.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🎯 Roadmap

### Phase 1 ✅
- [x] User authentication and authorization
- [x] Basic farm management
- [x] Crop tracking system
- [x] Weather integration

### Phase 2 🚧
- [ ] IoT sensor integration
- [ ] Mobile app development
- [ ] Advanced analytics dashboard
- [ ] Machine learning crop predictions

### Phase 3 📋
- [ ] Marketplace integration
- [ ] Multi-language support
- [ ] Offline functionality
- [ ] AI-powered farming recommendations

## 📞 Support

If you have any questions or need help getting started:

- 📧 Email: support@smartfarm.com
- 💬 Discord: [Join our community](https://discord.gg/smartfarm)
- 📖 Documentation: [Wiki](https://github.com/yourusername/smartfarm-management/wiki)
- 🐛 Issues: [GitHub Issues](https://github.com/yourusername/smartfarm-management/issues)

## 🙏 Acknowledgments

- [OpenWeatherMap](https://openweathermap.org/) for weather data
- [MongoDB](https://www.mongodb.com/) for database services
- [React Community](https://reactjs.org/) for amazing frontend tools
- All the farmers who provided valuable feedback during development

---

<div align="center">
  <strong>🌱 Happy Farming! 🌱</strong>
  <br><br>
  <a href="#top">Back to Top</a>
</div>
- 
