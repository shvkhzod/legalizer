# ✅ Pre-Deployment Checklist

Use this checklist before deploying to Railway to ensure everything is ready.

## 📋 Code Preparation

- [x] Backend TypeScript compiles without errors
- [x] Frontend builds successfully  
- [x] Railway configuration files added
- [x] SvelteKit adapter-node installed
- [x] Database migration script created
- [x] CORS configured for production
- [x] Environment variable templates created

## 🔐 Security

- [ ] Change default JWT_ACCESS_SECRET
- [ ] Generate strong random secret (use: `node -e "console.log(require('crypto').randomBytes(64).toString('hex'))"`)
- [ ] Remove any hardcoded credentials
- [ ] Update .gitignore to exclude .env files
- [ ] Review CORS settings

## 📦 Repository

- [ ] Code pushed to GitHub
- [ ] .env files NOT committed (check .gitignore)
- [ ] README.md updated
- [ ] All dependencies in package.json
- [ ] Remove node_modules from repo

## 🗄️ Database

- [ ] Database schema tested locally
- [ ] Migration script works  
- [ ] Sample data (if any) removed for production

## 🌐 Railway Setup

- [ ] Railway account created
- [ ] GitHub connected to Railway
- [ ] Project created from repository
- [ ] PostgreSQL database added
- [ ] Backend environment variables set
- [ ] Frontend environment variables set  
- [ ] Migration run successfully

## 🔗 URLs & Configuration

- [ ] Backend URL copied from Railway
- [ ] Frontend URL copied from Railway
- [ ] `PUBLIC_API_URL` set in frontend
- [ ] `CORS_ORIGIN` updated in backend
- [ ] Both services redeployed after URL updates

## 🧪 Testing

- [ ] Health check endpoint working (`/health`)
- [ ] User registration working
- [ ] User login working
- [ ] Scan functionality working
- [ ] Reports displaying correctly
- [ ] Mobile responsive design verified
- [ ] No console errors

## 📊 Monitoring

- [ ] Railway logs checked for errors
- [ ] Database connection verified
- [ ] API endpoints responding
- [ ] Frontend loading correctly

## 💰 Billing

- [ ] Understand Railway pricing
- [ ] Hobby plan activated (if needed)
- [ ] Usage monitoring set up

## 📝 Documentation

- [ ] Deployment guide reviewed
- [ ] Environment variables documented
- [ ] API endpoints documented (if applicable)

---

## 🎉 Ready to Deploy!

Once all items are checked, you're ready to deploy your application to Railway.

**Next Steps:**
1. Follow [RAILWAY_QUICKSTART.md](./RAILWAY_QUICKSTART.md)
2. Or see detailed [DEPLOYMENT.md](./DEPLOYMENT.md)

Good luck! 🚀
