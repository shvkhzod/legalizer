# 🚀 Railway Deployment Guide

This guide will help you deploy both the frontend (SvelteKit) and backend (Fastify + PostgreSQL) to Railway.

## Prerequisites

- Railway account (Hobby plan or higher)
- GitHub repository with your code
- Basic understanding of environment variables

---

## 📦 Step 1: Push Your Code to GitHub

1. Initialize git (if not already done):
```bash
git init
git add .
git commit -m "Ready for Railway deployment"
```

2. Create a GitHub repository and push:
```bash
git remote add origin <your-github-repo-url>
git branch -M main
git push -u origin main
```

---

## 🛤️ Step 2: Create Railway Project

1. Go to [Railway.app](https://railway.app)
2. Click **"New Project"**
3. Select **"Deploy from GitHub repo"**
4. Choose your repository

---

## 🗄️ Step 3: Add PostgreSQL Database

1. In your Railway project dashboard
2. Click **"+ New"**
3. Select **"Database"** → **"Add PostgreSQL"**
4. Railway will automatically create and connect the database

---

## ⚙️ Step 4: Configure Backend Service

Railway should auto-detect your backend. If not, add it manually:

1. Click **"+ New"** → **"GitHub Repo"**
2. Select `/server` as the root directory
3. Add environment variables:

### Required Environment Variables for Backend:

```env
# Railway provides DATABASE_URL automatically
# Add these manually:

JWT_ACCESS_SECRET=<generate-a-strong-random-secret>
JWT_ACCESS_EXPIRY=15m
JWT_REFRESH_EXPIRY_DAYS=7
NODE_ENV=production

# CORS - update with your frontend URL after deployment
CORS_ORIGIN=https://your-frontend-url.up.railway.app,http://localhost:5173
```

**To generate a secure JWT secret:**
```bash
node -e "console.log(require('crypto').randomBytes(64).toString('hex'))"
```

4. **Add Build Command** (if needed):
   - Build Command: `npm run build`
   - Start Command: `npm start`

5. **Run Database Migration:**
   - After first deployment, go to the backend service
   - Click **"Settings"** → **"Deploy"** → **"Custom Start Command"**
   - Temporarily change to: `npm run migrate && npm start`
   - Redeploy, then change back to just `npm start`

---

## 🎨 Step 5: Configure Frontend Service

1. Click **"+ New"** → **"GitHub Repo"**
2. Select the root directory (or leave as default)
3. Add environment variables:

### Required Environment Variables for Frontend:

```env
# Update with your backend URL from Railway
PUBLIC_API_URL=https://your-backend-url.up.railway.app/api

NODE_ENV=production
```

4. Railway should auto-detect SvelteKit and use:
   - Build Command: `npm run build`
   - Start Command: `node build`

---

## 🔗 Step 6: Update CORS

1. Once frontend is deployed, copy its URL
2. Go to backend service → **Variables**
3. Update `CORS_ORIGIN` to include your frontend URL:
```env
CORS_ORIGIN=https://your-frontend-url.up.railway.app
```
4. Redeploy backend service

---

## ✅ Step 7: Verify Deployment

1. Visit your frontend URL
2. Try registering a new account
3. Test the scan functionality
4. Check backend logs for any errors

---

## 🔒 Security Checklist

- [ ] Change JWT_ACCESS_SECRET to a strong random value
- [ ] Update CORS_ORIGIN with actual frontend URL
- [ ] Remove any default passwords
- [ ] Enable Railway's built-in monitoring
- [ ] Set up domain (optional but recommended)

---

## 📊 Monitoring

Railway provides:
- **Logs**: Click on each service to view real-time logs
- **Metrics**: CPU, Memory, Network usage
- **Deployments**: Track all deployments and rollback if needed

---

## 💰 Cost Estimation (Hobby Plan)

- **Base**: $5/month credit
- **Typical usage**: 
  - Frontend: ~$3/month
  - Backend: ~$3/month  
  - PostgreSQL: ~$5/month
- **Total**: ~$11/month (after free credit)

---

## 🆘 Troubleshooting

### Database Connection Errors
- Verify `DATABASE_URL` is set by Railway
- Check PostgreSQL service is running
- Ensure migration ran successfully

### CORS Errors
- Update `CORS_ORIGIN` with correct frontend URL
- Include both HTTP and HTTPS if testing locally

### Build Failures
- Check logs for specific errors
- Verify all dependencies are in `package.json`
- Ensure Node version compatibility

### Migration Issues
```bash
# SSH into backend service and run:
npm run migrate
```

---

## 🔄 Updating Your App

1. Push changes to GitHub:
```bash
git add .
git commit -m "Your changes"
git push
```

2. Railway automatically deploys from `main` branch
3. Monitor deployment in Railway dashboard

---

## 🌐 Custom Domain (Optional)

1. In Railway service → **Settings** → **Domains**
2. Click **"Generate Domain"** for Railway subdomain
3. Or **"Custom Domain"** for your own domain
4. Update DNS settings as instructed

---

## 📝 Quick Reference

### Backend URLs
- Health Check: `https://your-backend.railway.app/health`
- API Base: `https://your-backend.railway.app/api`

### Frontend URL
- App: `https://your-frontend.railway.app`

### Environment Variables Summary

**Backend:**
- `DATABASE_URL` (auto-provided)
- `JWT_ACCESS_SECRET`
- `CORS_ORIGIN`
- `NODE_ENV`

**Frontend:**
- `PUBLIC_API_URL`
- `NODE_ENV`

---

## 🎉 You're Done!

Your application is now live on Railway with:
- ✅ Responsive design (mobile, tablet, desktop)
- ✅ PostgreSQL database
- ✅ Automatic HTTPS
- ✅ CD/CD from GitHub
- ✅ Professional hosting

**Support:** If you encounter issues, check Railway docs or community forums.
