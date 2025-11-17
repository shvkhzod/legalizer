# 🛡️ Legal Compliance Checker

AI-powered compliance scanning platform for non-profit organizations. Built with SvelteKit, Fastify, and PostgreSQL.

## ✨ Features

- 🔍 **Automated Compliance Scanning** - Scan websites for legal compliance issues
- 🤖 **AI-Powered Analysis** - Intelligent detection of compliance violations
- 📊 **Detailed Reports** - Comprehensive compliance reports with recommendations
- 🔐 **Secure Authentication** - JWT-based auth with refresh tokens
- 📱 **Fully Responsive** - Works seamlessly on desktop, tablet, and mobile
- 🎨 **Modern UI** - Beautiful dark theme with smooth animations

## 🏗️ Tech Stack

### Frontend
- **SvelteKit** - Modern web framework
- **TypeScript** - Type-safe development
- **Vite** - Fast build tool
- **Responsive Design** - Mobile-first approach

### Backend
- **Fastify** - High-performance Node.js framework
- **PostgreSQL** - Reliable database
- **JWT** - Secure authentication
- **TypeScript** - End-to-end type safety

## 🚀 Quick Start

### Prerequisites
- Node.js 18+ 
- PostgreSQL 14+
- npm or yarn

### Local Development

1. **Clone the repository**
```bash
git clone <your-repo-url>
cd legalizer
```

2. **Setup Backend**
```bash
cd server
npm install
cp .env.example .env
# Edit .env with your database credentials
npm run db:init
npm run db:schema
npm run dev
```

3. **Setup Frontend** (in new terminal)
```bash
cd ..
npm install
cp .env.example .env
# Edit .env with backend URL
npm run dev
```

4. **Access the app**
- Frontend: http://localhost:5173
- Backend: http://localhost:3001

## 📦 Deployment

Ready to deploy on Railway! See [DEPLOYMENT.md](./DEPLOYMENT.md) for detailed instructions.

**Quick Deploy:**
1. Push to GitHub
2. Create Railway project
3. Add PostgreSQL
4. Configure environment variables
5. Deploy!

See [RAILWAY_QUICKSTART.md](./RAILWAY_QUICKSTART.md) for a 5-minute setup guide.

## 📁 Project Structure

```
legalizer/
├── src/                    # Frontend source
│   ├── lib/
│   │   ├── components/    # Svelte components
│   │   ├── stores/        # State management
│   │   └── api/           # API client
│   └── routes/            # SvelteKit routes
├── server/                # Backend source
│   ├── src/
│   │   ├── config/        # Configuration
│   │   ├── db/            # Database
│   │   ├── middleware/    # Auth middleware
│   │   └── routes/        # API routes
│   └── migrate.js         # Database migration
├── static/                # Static assets
└── DEPLOYMENT.md          # Deployment guide
```

## 🔐 Environment Variables

### Backend (.env)
```env
PORT=3001
DATABASE_URL=postgresql://...  # Or individual DB_ variables
JWT_ACCESS_SECRET=your-secret
CORS_ORIGIN=http://localhost:5173
```

### Frontend (.env)
```env
PUBLIC_API_URL=http://localhost:3001/api
```

## 🧪 Testing

```bash
# Frontend
npm run check

# Backend
npm run build
```

## 📱 Responsive Breakpoints

- **Desktop:** 1024px+
- **Tablet:** 768px - 1024px
- **Mobile:** < 768px
- **Small Mobile:** < 480px

## 🛠️ Available Scripts

### Frontend
- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run preview` - Preview production build

### Backend
- `npm run dev` - Start development server
- `npm run build` - Compile TypeScript
- `npm start` - Start production server
- `npm run migrate` - Run database migrations

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Open a Pull Request

## 📄 License

MIT License - feel free to use this project for your own purposes.

## 🆘 Support

- **Documentation:** See DEPLOYMENT.md and RAILWAY_QUICKSTART.md
- **Issues:** Create an issue on GitHub
- **Questions:** Check Railway community forums

## 🎯 Roadmap

- [ ] Email notifications
- [ ] PDF report exports
- [ ] Scheduled scans
- [ ] Multi-language support
- [ ] API rate limiting
- [ ] Admin dashboard

---

Built with ❤️ for non-profit organizations
