# 🛡️ CyberKeris Digital
<p align="center">
  <img src="public/assets/images/logo.png" alt="CyberKeris Logo" width="120">
</p>

<p align="center">
  <strong>Enterprise-Grade Cybersecurity Platform</strong><br>
  Advanced threat detection, AI-powered security operations, and comprehensive vulnerability management
</p>

<p align="center">
  <a href="#features">Features</a> •
  <a href="#tech-stack">Tech Stack</a> •
  <a href="#installation">Installation</a> •
  <a href="#deployment">Deployment</a> •
  <a href="#api-documentation">API</a>
</p>

---

## 🚀 Features

### Security Applications Suite
| Application | Description |
|-------------|-------------|
| **Threat Intelligence** | Real-time threat feeds, IOC management, predictive analytics |
| **Vulnerability Scanner** | Automated scanning, risk prioritization, remediation tracking |
| **Penetration Testing** | Expert-led security assessments, attack simulation |
| **Incident Response** | 24/7 rapid response, investigation, remediation |
| **Compliance & GRC** | SOC2, ISO 27001, GDPR, HIPAA compliance management |
| **Asset Management** | IT asset discovery, inventory, lifecycle management |
| **Dark Web Monitoring** | Credential leak detection, brand monitoring |
| **Security Metrics** | KPI dashboards, executive reporting |
| **Red Team Operations** | Adversary simulation, purple team exercises |
| **Threat Hunting** | Proactive threat detection, hypothesis-driven hunting |
| **API Security** | API vulnerability scanning, authentication testing |
| **Security Training** | Awareness programs, phishing simulations |

### Core Platform Features
- 🤖 **AI-Powered Assistant** - Security chatbot with threat analysis capabilities
- 🔐 **Social Login** - Google, Facebook, TikTok OAuth integration
- 👤 **Admin Approval Workflow** - New user verification system
- 🏢 **Multi-tenant Architecture** - Organization-based access control
- 📊 **Real-time Dashboards** - Live security metrics and alerts
- 🔄 **JWT Authentication** - Secure access & refresh token system

---

## 🛠️ Tech Stack

### Frontend
- **HTML5/CSS3** - Modern, responsive design
- **JavaScript (ES6+)** - Interactive UI components
- **Font Awesome 6** - Professional iconography
- **Inter & JetBrains Mono** - Typography

### Backend
- **Node.js** - Runtime environment
- **Express.js** - Web framework
- **SQLite** - Database (PostgreSQL ready)
- **JWT** - Authentication tokens
- **Bcrypt** - Password hashing
- **Nodemailer** - Email services
- **OpenAI API** - AI assistant integration

### DevOps
- **PM2** - Process management
- **Nginx** - Reverse proxy & SSL
- **Docker** - Containerization
- **GitHub Actions** - CI/CD pipeline

---

## 📁 Project Structure

```
cyberkeris-site/
├── backend/
│   ├── server.js           # Main Express application
│   ├── package.json        # Dependencies
│   ├── ecosystem.config.js # PM2 configuration
│   ├── routes/
│   │   ├── admin.js        # Admin endpoints
│   │   ├── api-security.js # API security module
│   │   ├── assets.js       # Asset management
│   │   ├── compliance.js   # Compliance module
│   │   ├── dark-web.js     # Dark web monitoring
│   │   ├── metrics.js      # Security metrics
│   │   ├── projects.js     # Project management
│   │   ├── red-team.js     # Red team operations
│   │   ├── security-apps.js# App router
│   │   ├── tasks.js        # Task management
│   │   ├── threat-hunting.js# Threat hunting
│   │   └── training.js     # Security training
│   ├── services/
│   │   └── email.js        # Email service
│   └── db/
│       └── users.db        # SQLite database
├── public/
│   ├── index.html          # Homepage
│   ├── login.html          # Login page
│   ├── signup.html         # Registration page
│   ├── dashboard.html      # User dashboard
│   ├── admin.html          # Admin console
│   ├── ai-assistant.html   # AI chatbot interface
│   ├── terms.html          # Terms of service
│   ├── css/
│   │   └── styles.css      # Main stylesheet
│   ├── js/
│   │   └── main.js         # Frontend JavaScript
│   ├── apps/               # Security application pages
│   │   ├── threat-intel.html
│   │   ├── vuln-scanner.html
│   │   ├── pentest.html
│   │   └── ... (12 apps)
│   └── assets/
│       └── images/
│           └── logo.png
├── config/
│   └── nginx/
│       └── cyberkeris.conf # Nginx configuration
├── scripts/
│   ├── deploy.sh           # Deployment script
│   └── setup.sh            # Initial setup
├── docker-compose.yml      # Docker configuration
└── README.md
```

---

## ⚡ Installation

### Prerequisites
- Node.js 18+ 
- npm or yarn
- SQLite3 (or PostgreSQL for production)

### Quick Start

```bash
# Clone the repository
git clone https://github.com/AtlasTheDev123/cyberkeris-site.git
cd cyberkeris-site

# Install backend dependencies
cd backend
npm install

# Create environment file
cp .env.example .env

# Configure environment variables
nano .env

# Start development server
npm run dev
```

### Environment Variables

Create a `.env` file in the `backend/` directory:

```env
# Server
PORT=3000
NODE_ENV=development

# JWT Configuration
JWT_SECRET=your-super-secret-key-change-in-production
JWT_EXPIRES_IN=15m
JWT_REFRESH_EXPIRES_IN=30d

# Database
DATABASE_URL=./db/users.db

# Email (SMTP)
SMTP_HOST=smtp.gmail.com
SMTP_PORT=587
SMTP_USER=no-reply@cyberkeris.com
SMTP_PASS=your-app-password

# OAuth (Optional)
GOOGLE_CLIENT_ID=your-google-client-id
GOOGLE_CLIENT_SECRET=your-google-secret
FACEBOOK_APP_ID=your-facebook-app-id
FACEBOOK_APP_SECRET=your-facebook-secret

# AI Assistant (Optional)
OPENAI_API_KEY=your-openai-api-key
```

---

## 🚀 Deployment

### Using PM2 (Recommended)

```bash
# Install PM2 globally
npm install -g pm2

# Start application
cd backend
pm2 start ecosystem.config.js

# Enable startup on boot
pm2 startup
pm2 save
```

### Using Docker

```bash
# Build and start containers
docker-compose up -d

# View logs
docker-compose logs -f
```

### Nginx Configuration

```nginx
server {
    listen 80;
    server_name cyberkeris.com www.cyberkeris.com;
    return 301 https://$server_name$request_uri;
}

server {
    listen 443 ssl http2;
    server_name cyberkeris.com www.cyberkeris.com;

    ssl_certificate /etc/letsencrypt/live/cyberkeris.com/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/cyberkeris.com/privkey.pem;

    location / {
        proxy_pass http://127.0.0.1:3000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
}
```

---

## 📡 API Documentation

### Authentication

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/api/auth/signup` | POST | Register new user |
| `/api/auth/login` | POST | User login |
| `/api/auth/refresh` | POST | Refresh access token |
| `/api/auth/logout` | POST | User logout |
| `/api/auth/google` | GET | Google OAuth |
| `/api/auth/facebook` | GET | Facebook OAuth |

### Admin

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/api/admin/users/pending` | GET | List pending users |
| `/api/admin/users/:id/approve` | POST | Approve user |
| `/api/admin/users/:id/reject` | POST | Reject user |
| `/api/admin/stats` | GET | Dashboard statistics |

### AI Assistant

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/api/assistant/chat` | POST | Send message to AI |
| `/api/assistant/history` | GET | Get chat history |

### Contact

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/api/contact` | POST | Submit contact form |

---

## 🔐 Security Features

- **Rate Limiting** - Protects against brute force attacks
- **Helmet.js** - HTTP security headers
- **CORS** - Cross-origin resource sharing control
- **Password Hashing** - Bcrypt with salt rounds
- **JWT Tokens** - Stateless authentication
- **Input Validation** - Request sanitization
- **Audit Logging** - User action tracking

---

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

---

## 📄 License

This project is proprietary software owned by CyberKeris Technologies.

---

## 📞 Support

- **Email**: support@cyberkeris.com
- **Documentation**: [docs.cyberkeris.com](https://docs.cyberkeris.com)
- **Status Page**: [status.cyberkeris.com](https://status.cyberkeris.com)

---

<p align="center">
  <strong>⚡ CyberKeris Technologies — Securing the Digital Future ⚡</strong>
</p>
