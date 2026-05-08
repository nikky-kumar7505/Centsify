# Centsify

Centsify is a **full-stack personal finance management app** built with **React (frontend), Node.js/Express (backend), MongoDB (database)**, and enhanced with **Google Gemini AI for OCR-based receipt scanning**. It helps users track income, expenses, receipts, and visualize financial analytics via charts.

## Features

* **Authentication** – JWT-based login & signup
* **Transactions Management** – Add income and expenses with categories
* **Analytics & Charts** – Visual breakdown by category, income/expense trends
* **Receipt Management** – Upload receipts and automatically extract expense details using **Google Gemini OCR**
* **Full-Stack Deployment Ready** – Configured for deployment on various hosting platforms
* **Account Settings** – View your profile and delete your account permanently from the app.

## Tech Stack:-

**Frontend:**

* React + Vite
* React Router
* Axios
* TailwindCSS

**Backend:**

* Node.js + Express
* MongoDB + Mongoose
* JWT Authentication
* Multer (for file uploads)
* Google Gemini AI SDK (for OCR)

**Dev Tools:**

* Nodemon
* dotenv

**Hosting:**

* Frontend → Any static hosting platform (Netlify, Vercel, etc.)
* Backend → Any Node.js hosting platform (Render, Heroku, Railway, etc.)
* Database → MongoDB Atlas or self-hosted MongoDB

### Project Structure

```
.
├── backend/
│ ├── server.js # Express app entry
│ ├── package.json
│ ├── config/
│ │ └── db.js
│ ├── routes/
│ │ ├── authRoutes.js
│ │ ├── transactionRoutes.js
│ │ ├── receiptRoutes.js
| | └── userRoutes.js
│ ├── middleware/
│ ├── controllers/
│ ├── models/
│ └── uploads/ # static served files (receipts)
│
├── docs/
│ ├── openapi.yaml
│
├── frontend/
│ ├── src/
│ │ ├── pages/
│ │ ├── components/
│ │ ├── contexts/
│ │ └── api/
│ │ └── config/
│ │ └── hooks/
│ ├── App.jsx
│ ├── main.jsx
│ ├── package.json
│ ├── vite.config.js
│ ├── tailwindcss.config.js
│
└── README.md
```

## Getting Started

### Prerequisites

* Node.js (v16 or higher)
* MongoDB (MongoDB Atlas or local instance)
* npm or yarn

### Clone the repository

```bash
git clone https://github.com/nikky-kumar7505/Centsify.git
cd centsify
```

### Backend Setup

```bash
cd backend
npm install   
```

Create a **`.env`** file in the `backend/` folder:

```env
PORT=5000
MONGO_URI=your-mongodb-atlas-uri
JWT_SECRET=your-secret-key
GEMINI_API_KEY=your-gemini-api-key
KEEP_ALIVE_URL=http://localhost:5000
```

Start the backend:

```bash
npm run dev
```

Backend will run on → `http://localhost:5000`

### Frontend Setup

```bash
cd frontend
npm install
```

Create a **`.env`** file in the `frontend/` folder:

```env
VITE_API_URL=http://localhost:5000/api
```

Start the frontend:

```bash
npm run dev
```

Frontend will run on → `http://localhost:5173`

## API Documentation

The full API reference is defined in **OpenAPI 3.0** format.

See the file → [`docs/openapi.yaml`](./docs/openapi.yaml)

You can:

* Open it in [Swagger Editor](https://editor.swagger.io/)
* Import into **Postman** or **Insomnia**

## Core API Endpoints

### Auth

* `POST /api/auth/signup` → Register new user
* `POST /api/auth/login` → Login user
* `GET /api/auth/me` → Fetch logged-in user profile

### Transactions

* `GET /api/transactions` → Get all transactions (paginated)
* `POST /api/transactions` → Create a new transaction
* `GET /api/transactions/summary` → Get income, expense, balance, and recent transactions
* `GET /api/transactions/charts` → Get data for dashboard charts
* `GET /api/transactions/categories/expense` → Get unique expense transaction categories
* `GET /api/transactions/categories/income` → Get unique income transaction categories
* `DELETE /api/transactions/category` → Delete a custom category

### Analytics

* `GET /api/analytics/summary` → Income vs Expense summary
* `GET /api/analytics/categories` → Expense breakdown by category

### Receipts

* `POST /api/receipts/upload` → Upload receipt, trigger Gemini OCR, and create a transaction in one step

### Users

* `DELETE /api/users/account` → Delete the authenticated user account permanently

## Deployment

### Backend Deployment

* Configure **Start Command**: `npm start`
* Add environment variables in your hosting platform's dashboard
* Ensure your MongoDB connection string is properly configured

### Frontend Deployment

* Build Command: `npm run build`
* Publish Directory: `dist`
* Set Environment Variable: `VITE_API_URL=<your-backend-url>/api`