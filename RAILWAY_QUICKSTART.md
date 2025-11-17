# 🚂 Railway Quick Start Guide

## 1️⃣ Prerequisites
- [ ] Push code to GitHub
- [ ] Railway account (Hobby plan)

## 2️⃣ Deploy in 5 Minutes

### Step 1: Create Project
1. Go to railway.app
2. **New Project** → **Deploy from GitHub**
3. Select your repository

### Step 2: Add PostgreSQL
1. Click **+ New** → **Database** → **PostgreSQL**
2. Done! DATABASE_URL is auto-configured

### Step 3: Configure Backend
Add these environment variables in the **backend service**:

```
JWT_ACCESS_SECRET=<run: node -e "console.log(require('crypto').randomBytes(64).toString('hex'))">
CORS_ORIGIN=https://your-frontend.railway.app
NODE_ENV=production
```

### Step 4: Run Migration (One Time)
1. Backend service → **Settings** → **Deploy**
2. Custom Start Command: `npm run migrate && npm start`  
3. Deploy once
4. Change back to: `npm start`

### Step 5: Configure Frontend  
Add this environment variable in the **frontend service**:

```
PUBLIC_API_URL=https://your-backend.railway.app/api
```

### Step 6: Update CORS
1. Copy frontend URL from Railway
2. Update backend `CORS_ORIGIN` variable
3. Redeploy backend

## ✅ Done!

Visit your frontend URL and test the app!

---

## 🆘 Common Issues

**Database connection failed?**
- Check PostgreSQL service is running
- Verify `DATABASE_URL` exists in backend variables

**CORS errors?**
- Update `CORS_ORIGIN` with your exact frontend URL
- Include `https://` prefix

**Build failed?**  
- Check build logs
- Verify `package.json` has all dependencies

---

## 📱 Your App Features

✅ Responsive design (works on mobile, tablet, desktop)
✅ Automatic HTTPS
✅ PostgreSQL database  
✅ Auto-deploy from GitHub
✅ Professional hosting

**Cost:** ~$11/month after $5 credit
