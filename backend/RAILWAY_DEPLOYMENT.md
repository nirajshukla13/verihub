# Railway Deployment Guide for VeriHub Backend

## Prerequisites
- Railway account (https://railway.app)
- GitHub repository connected to Railway
- Environment variables ready

## Deployment Steps

### 1. Connect to Railway
1. Go to https://railway.app
2. Click "New Project"
3. Select "Deploy from GitHub repo"
4. Choose your VeriHub repository
5. Railway will auto-detect the backend directory

### 2. Configure Environment Variables
Add these variables in Railway dashboard (Settings → Variables):

```
MONGODB_URL=mongodb+srv://username:password@cluster.mongodb.net/
DATABASE_NAME=your_database_name
SECRET_KEY=your-super-secret-key-here
ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=30
PORT=8000
CLOUDINARY_CLOUD_NAME=your-cloud-name
CLOUDINARY_API_KEY=your-api-key
CLOUDINARY_API_SECRET=your-api-secret
CLOUDINARY_SECURE=true
GOOGLE_API_KEY=your-google-api-key
SERPAPI_API_KEY=your-serpapi-key
```

### 3. Configure Build Settings
Railway will automatically:
- Detect Python project
- Install dependencies from `requirements.txt`
- Use the start command from `railway.json`

### 4. Deploy
1. Push your code to GitHub
2. Railway will automatically deploy
3. You'll get a public URL like: `https://your-app.railway.app`

## Important Files Created
- `Procfile` - Process file for deployment
- `railway.json` - Railway-specific configuration
- `runtime.txt` - Python version specification

## Post-Deployment
1. Test your API at: `https://your-app.railway.app/`
2. Update frontend API URL to point to Railway backend
3. Monitor logs in Railway dashboard

## Troubleshooting
- Check Railway logs for errors
- Verify all environment variables are set
- Ensure MongoDB is accessible from Railway's IP
- Check if all dependencies are in requirements.txt

## Notes
- The app uses Python 3.11
- Uvicorn server runs on the PORT environment variable
- CORS is configured for all origins (update for production)
