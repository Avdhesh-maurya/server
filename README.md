# RentMyCar Server

Backend API for the RentMyCar application built with Node.js, Express, and MongoDB.

## Features
- User authentication with JWT
- Owner/Admin functionality
- Booking management
- Image upload with ImageKit
- CORS enabled for frontend integration

## Tech Stack
- **Runtime**: Node.js 20.x
- **Framework**: Express.js
- **Database**: MongoDB
- **Authentication**: JWT (jsonwebtoken)
- **Password Hashing**: bcrypt
- **Image Management**: ImageKit
- **File Upload**: Multer
- **Security**: CORS

## Installation

1. Clone the repository:
```bash
git clone https://github.com/YOUR_USERNAME/rentmycar-server.git
cd rentmycar-server
```

2. Install dependencies:
```bash
npm install
```

3. Create a `.env` file with the following variables:
```bash
cp .env.example .env
```

4. Fill in your environment variables in `.env`

## Running Locally

Development mode (with hot reload):
```bash
npm run server
```

Production mode:
```bash
npm start
```

Server runs on `http://localhost:3000`

## API Routes

- **User Routes**: `/api/user`
- **Owner Routes**: `/api/owner`
- **Booking Routes**: `/api/bookings`

## Deployment

### Deploy to Vercel

1. Push your code to GitHub
2. Go to [vercel.com](https://vercel.com)
3. Click "New Project"
4. Import your GitHub repository
5. Set environment variables in Vercel settings
6. Deploy

**Note:** The project uses Node.js 20.x as specified in `package.json`. This setting takes precedence over any Node.js version configured in Vercel Project Settings.

See [DEPLOYMENT.md](./DEPLOYMENT.md) for detailed CLI deployment instructions.

## Environment Variables

| Variable | Description | Example |
|----------|-------------|---------|
| `MONGODB_URI` | MongoDB connection string | `mongodb+srv://...` |
| `JWT_SECRET` | Secret key for JWT | `your_secret_key` |
| `IMAGEKIT_PRIVATE_KEY` | ImageKit private key | - |
| `IMAGEKIT_PUBLIC_KEY` | ImageKit public key | - |
| `IMAGEKIT_URL_ENDPOINT` | ImageKit URL endpoint | `https://ik.imagekit.io/...` |
| `CLIENT_URL` | Frontend application URL | `https://frontend.com` |
| `PORT` | Server port | `3000` |
| `NODE_ENV` | Environment | `production` or `development` |

## Project Structure

```
├── configs/           # Configuration files (DB, ImageKit)
├── controllers/       # Route controllers
├── middleware/        # Custom middleware (auth, multer)
├── models/           # MongoDB schemas
├── routes/           # API routes
├── server.js         # Entry point
├── package.json      # Dependencies
├── .env.example      # Environment variables template
└── vercel.json       # Vercel configuration
```

## License

ISC

## Author

Avdhesh Maurya
