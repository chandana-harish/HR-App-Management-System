# HR Management System with Express.js

A comprehensive HR management system built with Node.js, Express.js, and MongoDB, featuring employee management, leave tracking, attendance monitoring, grievance handling, and an AI chatbot assistant.asdfasefs

## 🚀 Quick Start with Docker

### Prerequisites
- Docker and Docker Compose installed on your system
- Git (to clone the repository)

### Setup Instructions

1. **Clone the repository** (if not already done):
   ```bash
   git clone <repository-url>
   cd live_with_express
   ```

2. **Environment Configuration**:
   ```bash
   cp .env.example .env
   ```
   Edit `.env` file with your desired configuration.

3. **Start the application**:
   ```bash
   # Start all services
   docker-compose up -d

   # Or start with database management interface
   docker-compose --profile dev up -d
   ```

4. **Access the application**:
   - **Main Application**: http://localhost:3000
   - **MongoDB Express** (if using dev profile): http://localhost:8081
     - Username: `admin`
     - Password: `admin123`

### Available Services

| Service | Port | Description |
|---------|------|-------------|
| HR Application | 3000 | Main web application |
| MongoDB | 27017 | Database server |
| Mongo Express | 8081 | Database management interface |

## 📁 Project Structure

```
live_with_express/
├── public/                 # Frontend files (HTML, CSS, JS)
│   ├── *.html             # Web pages
│   └── script.js          # Client-side JavaScript
├── mongo-init/            # MongoDB initialization scripts
│   └── init.js           # Database setup script
├── server.js             # Main Express.js server
├── package.json          # Node.js dependencies
├── Dockerfile            # Docker container configuration
├── docker-compose.yaml   # Multi-container setup
├── .dockerignore        # Docker build ignore patterns
├── .env.example         # Environment variables template
└── README.md            # This file
```

## 🎯 Features

- **Employee Management**: Registration, login, profile management
- **Leave Management**: Apply for leave, track leave balance, admin approval workflow
- **Attendance Tracking**: Check-in/check-out functionality with admin monitoring
- **Grievance System**: Submit and track grievances with admin responses
- **Hiring Process**: Job postings and hiring feedback collection
- **AI Chatbot**: HR policy assistant with natural language processing
- **Admin Dashboard**: Comprehensive admin interface for HR operations
- **Analytics**: HR metrics and reporting dashboard

## 🔧 Docker Commands

### Basic Operations
```bash
# Start services
docker-compose up -d

# Stop services
docker-compose down

# View logs
docker-compose logs -f hr-app

# Rebuild and restart
docker-compose up --build -d

# Start with development tools
docker-compose --profile dev up -d
```

### Development Commands
```bash
# Execute commands in the app container
docker-compose exec hr-app npm install

# Access MongoDB shell
docker-compose exec mongodb mongosh hr_system

# View container status
docker-compose ps

# Remove all data (careful!)
docker-compose down -v
```

## 🔐 Default Login Credentials

### Employee Login
- Employee ID: `EMP001`
- Password: `password123`

### Admin Login
- Admin ID: `admin`
- Password: `admin123`

> **Security Note**: Change these default credentials in production!

## 🔧 Environment Variables

Key environment variables (see `.env.example`):

```bash
# Application
NODE_ENV=production
PORT=3000

# Database
MONGO_URI=mongodb://mongodb:27017
DB_NAME=hr_system

# Admin Credentials (change in production!)
DEFAULT_ADMIN_ID=admin
DEFAULT_ADMIN_PASSWORD=admin123
```

## 📊 API Endpoints

### Employee APIs
- `POST /api/signup` - Employee registration
- `POST /api/login` - Employee login
- `POST /api/leave/apply` - Apply for leave
- `GET /api/leave/balance/:empId` - Get leave balance
- `POST /api/attendance/checkin` - Check-in attendance
- `POST /api/attendance/checkout` - Check-out attendance
- `POST /api/grievance` - Submit grievance
- `POST /api/chatbot` - Chat with AI assistant

### Admin APIs
- `POST /api/admin/login` - Admin login
- `GET /api/admin/employees` - Get all employees
- `GET /api/admin/leaves` - Get all leave requests
- `PUT /api/admin/leaves/:id` - Approve/reject leave
- `GET /api/admin/attendance` - Get attendance records
- `GET /api/admin/analytics` - Get HR analytics

## 🛠️ Development

### Local Development Setup
```bash
# Install dependencies
npm install

# Start MongoDB (if not using Docker)
# Make sure MongoDB is running on localhost:27017

# Start the application
npm start
```

### Database Management
The MongoDB initialization script (`mongo-init/init.js`) automatically:
- Creates required collections
- Sets up indexes for performance
- Creates default admin user
- Inserts sample employees

## 🔒 Security Considerations

⚠️ **Important for Production**:
1. Change default passwords
2. Implement password hashing (bcrypt)
3. Add JWT authentication
4. Set up HTTPS
5. Configure MongoDB authentication
6. Add rate limiting
7. Sanitize user inputs
8. Set up proper logging and monitoring

## 🐛 Troubleshooting

### Common Issues

1. **Port already in use**:
   ```bash
   docker-compose down
   # Or change ports in docker-compose.yaml
   ```

2. **Database connection errors**:
   ```bash
   # Check if MongoDB container is running
   docker-compose ps
   
   # Restart services
   docker-compose restart
   ```

3. **Permission errors**:
   ```bash
   # On Linux/Mac, you might need to adjust file permissions
   chmod +x mongo-init/init.js
   ```

## 📝 License

This project is licensed under the ISC License.

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📞 Support

For support and questions, please create an issue in the repository.
