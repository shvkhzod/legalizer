# Repository Structure

## Important: Frontend and Backend are SEPARATE repositories!

### Repository Locations

1. **Main/Root Repository** (`legalizer`)
   - Path: `C:\Another Disk\The FIles\Projects\coding\sveltekit\legalizer`
   - Git: https://github.com/shvkhzod/legalizer.git
   - Branch: `main`
   - Purpose: Documentation and project root (deprecated for code)

2. **Frontend Repository** (`legalizer-frontend`)
   - Path: `C:\Another Disk\The FIles\Projects\coding\sveltekit\legalizer-frontend`
   - Git: https://github.com/shvkhzod/legalizer-frontend.git
   - Branch: `master`
   - Contains: SvelteKit application
   - Key files:
     - `src/lib/api/client.ts` - API client
     - `src/routes/**/*.svelte` - UI pages
     - `.env.example` - Environment variable template

3. **Backend Repository** (`legalizer-backend`)
   - Path: `C:\Another Disk\The FIles\Projects\coding\sveltekit\legalizer-backend`
   - Git: https://github.com/shvkhzod/legalizer-backend.git
   - Branch: `master`
   - Contains: Node.js/Fastify API with PostgreSQL
   - Key files:
     - `src/` - TypeScript source code
     - `migrate.js` - Database migration script
     - `railway.json` - Railway deployment config
     - `nixpacks.toml` - Build configuration

### Railway Deployment

All three repositories are deployed as separate services on Railway:

- **PostgreSQL Database** - Railway managed
- **Backend Service** - Deployed from `legalizer-backend` repo
  - URL: `https://legalizer-backend-production.up.railway.app`
- **Frontend Service** - Deployed from `legalizer-frontend` repo
  - URL: `https://legalizer-frontend-production.up.railway.app`

### When Making Changes

**IMPORTANT:** Always push changes to the correct repository!

- **Frontend changes** (UI, API client, routes):
  ```bash
  cd "C:\Another Disk\The FIles\Projects\coding\sveltekit\legalizer-frontend"
  git add .
  git commit -m "message"
  git push
  ```

- **Backend changes** (API, database, server logic):
  ```bash
  cd "C:\Another Disk\The FIles\Projects\coding\sveltekit\legalizer-backend"
  git add .
  git commit -m "message"
  git push
  ```

### Common Mistake to Avoid

❌ **DON'T** push frontend code to the main `legalizer` repository
❌ **DON'T** push backend code to the frontend repository
✅ **DO** verify which directory you're in before committing and pushing
