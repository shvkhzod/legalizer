# 🔧 Railway Deployment - Step by Step

## The Correct Way to Deploy

Railway needs to deploy **backend** and **frontend** as **separate services**.

---

## 🗑️ Step 1: Delete Current Service (if you created one)

1. In Railway dashboard, click on the service you created
2. Go to **Settings** → **Danger** → **Delete Service**
3. Confirm deletion

---

## 🛤️ Step 2: Create New Project (Fresh Start)

1. Railway Dashboard → **New Project**
2. **Empty Project** (don't use "Deploy from GitHub" yet)
3. Name it: "Legal Compliance Checker"

---

## 🗄️ Step 3: Add PostgreSQL Database

1. Click **+ New** in your project
2. Select **Database** → **PostgreSQL**
3. Done! ✓

---

## 🔧 Step 4: Add Backend Service

1. Click **+ New** → **GitHub Repo**
2. Select your repository
3. **Important:** Click **Settings** → **Service Settings**
4. Set **Root Directory:** `server`
5. Add Environment Variables:

```env
JWT_ACCESS_SECRET=<paste-your-generated-secret>
NODE_ENV=production
CORS_ORIGIN=https://your-frontend.railway.app
```

**Generate JWT Secret:**
```bash
node -e "console.log(require('crypto').randomBytes(64).toString('hex'))"
```

6. **Deploy** - Let it build and deploy

---

## 📊 Step 5: Run Database Migration

After backend deploys successfully:

1. Click on **Backend Service**
2. Go to **Settings** → **Variables**
3. Check that `DATABASE_URL` exists (auto-added by Railway)
4. Go to **Deployments** tab
5. Click on the latest deployment → **View Logs**
6. Open a **Custom Shell** (if available) or use deployment settings:
   - Settings → **Deploy** → **Custom Start Command**
   - Change to: `npm run migrate && npm start`
   - **Redeploy**
7. After successful migration, change back to: `npm start`
8. **Redeploy** again

---

## 🎨 Step 6: Add Frontend Service

1. Click **+ New** → **GitHub Repo**  
2. Select the **same repository**
3. **Important:** Keep **Root Directory** as `.` (root)
4. Add Environment Variable:

```env
PUBLIC_API_URL=https://your-backend-service.up.railway.app/api
```

**To get Backend URL:**
- Click on Backend Service
- Go to **Settings** → **Networking** → Copy the public URL

5. **Deploy**

---

## 🔗 Step 7: Update CORS

1. Go to **Backend Service** → **Variables**
2. Update `CORS_ORIGIN` with your frontend URL:
```env
CORS_ORIGIN=https://your-frontend-service.up.railway.app
```
3. **Redeploy** backend service

---

## ✅ Step 8: Test Your Application

1. Click on **Frontend Service** → **Settings** → **Networking**
2. Copy the public URL
3. Open in browser
4. Test:
   - Registration ✓
   - Login ✓
   - Scan functionality ✓
   - Reports ✓

---

## 📝 Summary of Services You'll Have:

1. **PostgreSQL** - Database (auto-configured)
2. **Backend Service** - API at `/server` directory
   - Build: `npm run build`
   - Start: `npm start`
3. **Frontend Service** - SvelteKit app at root
   - Build: `npm run build`
   - Start: `node build`

---

## 🆘 Still Having Issues?

### Backend Won't Start?
- Check logs for errors
- Verify `DATABASE_URL` exists
- Ensure migration ran successfully

### Frontend Can't Connect to Backend?
- Verify `PUBLIC_API_URL` is set correctly
- Check CORS settings in backend
- Both services should have `https://` URLs

### Database Migration Failed?
Run it manually:
1. Backend Service → **Settings** → **Variables**
2. Add temporary variable: `RUN_MIGRATION=true`
3. Update start command: `npm run migrate && npm start`
4. Deploy
5. Remove after success

---

## 💰 Cost Check

With 3 services (DB + Backend + Frontend):
- Free: $5 credit/month
- After credit: ~$11/month total

---

## 🎉 Next Steps

Once deployed:
- [ ] Test all functionality
- [ ] Add custom domain (optional)
- [ ] Set up monitoring
- [ ] Commit and push changes to auto-deploy

Good luck! 🚀
