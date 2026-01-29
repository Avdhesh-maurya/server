# Vercel Deployment Guide

## Prerequisites
1. Install Vercel CLI globally:
   ```bash
   npm install -g vercel
   ```

2. Create an account on [Vercel](https://vercel.com) if you don't have one

## Deployment Steps

### Step 1: Authenticate with Vercel
```bash
vercel login
```
This will open a browser to authenticate. Follow the prompts.

### Step 2: Deploy Your Project
From your server directory (`c:\Users\Avdhesh\OneDrive\Desktop\vercel\rentmycar\server`), run:

```bash
vercel --prod
```

The CLI will ask:
- **Project name**: Enter a name (e.g., `rentmycar-server`)
- **Project directory**: Press Enter (current directory)
- **Link to existing project?**: Type `N` (No)
- **Build and Output settings**: Press Enter (default)

### Step 3: Configure Environment Variables
After deployment, set your environment variables on Vercel:

```bash
vercel env add
```

Add these variables (get their values from your `.env` file):
- `MONGODB_URI` - Your MongoDB connection string
- `JWT_SECRET` - Your JWT secret
- `IMAGEKIT_PRIVATE_KEY` - ImageKit private key
- `IMAGEKIT_PUBLIC_KEY` - ImageKit public key
- `IMAGEKIT_URL_ENDPOINT` - ImageKit URL endpoint
- `CLIENT_URL` - Your Render frontend URL

### Step 4: Re-deploy with Environment Variables
After adding environment variables:

```bash
vercel --prod
```

## Update CORS
Update your `CLIENT_URL` environment variable with your Render frontend URL so CORS works properly.

## Troubleshooting

**If you get a database connection error:**
- Ensure your MongoDB connection string is correct in `MONGODB_URI`
- Check MongoDB whitelist includes Vercel IPs

**If API routes return 404:**
- The `vercel.json` is configured to route all requests to the `api/` directory
- Vercel automatically detects `api/index.js` as a serverless function

**If you get "No Output Directory" error:**
- Ensure there is no `build` script in package.json that suggests static site generation
- For serverless-only APIs, Vercel should auto-detect functions in the `api/` directory

**For logs and monitoring:**
```bash
vercel logs
```

## Additional Notes
- The project uses serverless functions with Vercel's automatic detection
- Your `package.json` specifies Node.js 20.x via the `engines` field, which takes precedence over Vercel Project Settings
- `vercel.json` uses `rewrites` to route all requests to the automatically detected serverless function
