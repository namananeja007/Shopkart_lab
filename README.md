# 🛒 ShopKart

A full-stack e-commerce web application built with **React** and **Node.js/Express**, featuring product browsing, authentication, wishlist, cart management, and Razorpay payment integration.

![ShopKart](https://img.shields.io/badge/ShopKart-E--Commerce-blueviolet?style=for-the-badge)
![Node.js](https://img.shields.io/badge/Node.js-Backend-339933?style=for-the-badge&logo=node.js&logoColor=white)
![React](https://img.shields.io/badge/React-Frontend-61DAFB?style=for-the-badge&logo=react&logoColor=black)
![MongoDB](https://img.shields.io/badge/MongoDB-Database-47A248?style=for-the-badge&logo=mongodb&logoColor=white)

---

## 📋 Table of Contents

- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
- [API Endpoints](#-api-endpoints)
- [Environment Variables](#-environment-variables)
- [Screenshots](#-screenshots)

---

## ✨ Features

| Feature | Description |
|---------|-------------|
| 🔐 **Authentication** | Register, Login, Logout with JWT & HttpOnly cookies |
| 📦 **Products** | Browse, search, filter by category, sort by price |
| ❤️ **Wishlist** | Add/remove products to personal wishlist |
| 🛒 **Cart** | Add to cart, update quantity, remove items |
| 💳 **Payments** | Razorpay payment gateway integration |
| 📋 **Orders** | Order history with detailed order view |
| ⚙️ **Settings** | Update profile name and password |

---

## 🛠 Tech Stack

### Frontend
- **React 19** — UI library
- **React Router v7** — Client-side routing
- **Axios** — HTTP client
- **Vite 8** — Build tool & dev server

### Backend
- **Node.js** — Runtime
- **Express 5** — Web framework
- **MongoDB Atlas** — Cloud database
- **Mongoose 9** — ODM
- **JWT** — Authentication tokens
- **bcrypt** — Password hashing
- **Razorpay** — Payment gateway
- **cookie-parser** — HttpOnly cookie handling

---

## 📁 Project Structure

```
ShopKart_Lab/
├── front-end/
│   └── vite-project/
│       ├── src/
│       │   ├── components/
│       │   │   ├── Navbar.jsx
│       │   │   ├── ProductCard.jsx
│       │   │   └── SearchBar.jsx
│       │   ├── context/
│       │   │   └── CartContext.jsx
│       │   ├── pages/
│       │   │   ├── Login.jsx
│       │   │   ├── Register.jsx
│       │   │   ├── Products.jsx
│       │   │   ├── ProductDetails.jsx
│       │   │   ├── Wishlist.jsx
│       │   │   ├── Cart.jsx
│       │   │   ├── Checkout.jsx
│       │   │   ├── MyOrders.jsx
│       │   │   ├── OrderDetail.jsx
│       │   │   └── Settings.jsx
│       │   ├── services/
│       │   │   └── api.js
│       │   ├── App.jsx
│       │   └── App.css
│       └── vite.config.js
│
├── server/
│   ├── controllers/
│   │   ├── product.controller.js
│   │   ├── customer.controller.js
│   │   ├── wishlist.controller.js
│   │   ├── cart.controller.js
│   │   └── order.controller.js
│   ├── models/
│   │   ├── product.model.js
│   │   ├── customer.model.js
│   │   └── order.model.js
│   ├── routes/
│   │   ├── product.routes.js
│   │   ├── customer.routes.js
│   │   ├── wishlist.routes.js
│   │   ├── cart.routes.js
│   │   └── order.routes.js
│   ├── middlewares/
│   │   └── auth.middleware.js
│   ├── utils/
│   │   └── generateToken.js
│   ├── index.js
│   ├── seed.js
│   └── .env
│
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites

- **Node.js** (v18+)
- **npm**
- **MongoDB Atlas** account (or local MongoDB)

### 1. Clone the repository

```bash
git clone https://github.com/your-username/ShopKart_Lab.git
cd ShopKart_Lab
```

### 2. Setup the Backend

```bash
cd server
npm install
```

Create a `.env` file in the `server/` directory:

```env
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret_key
RAZORPAY_KEY_ID=your_razorpay_key_id
RAZORPAY_KEY_SECRET=your_razorpay_key_secret
```

Seed the database with sample products:

```bash
node seed.js
```

Start the server:

```bash
node index.js
```

> Server runs on **http://localhost:5000**

### 3. Setup the Frontend

```bash
cd front-end/vite-project
npm install
npm run dev
```

> Frontend runs on **http://localhost:5173**

---

## 📡 API Endpoints

### 🔐 Authentication (`/customers`)

| Method | Endpoint | Description | Auth |
|--------|----------|-------------|------|
| POST | `/customers/register` | Register new customer | ❌ |
| POST | `/customers/login` | Login customer | ❌ |
| GET | `/customers/me` | Get logged-in profile | ✅ |
| POST | `/customers/logout` | Logout customer | ✅ |
| PUT | `/customers/settings` | Update profile | ✅ |

### 📦 Products (`/products`)

| Method | Endpoint | Description | Auth |
|--------|----------|-------------|------|
| GET | `/products` | Get all products (search, filter, sort) | ❌ |
| GET | `/products/:id` | Get single product | ❌ |
| POST | `/products` | Create a product | ❌ |

### ❤️ Wishlist (`/wishlist`)

| Method | Endpoint | Description | Auth |
|--------|----------|-------------|------|
| GET | `/wishlist` | Get user's wishlist | ✅ |
| POST | `/wishlist/:productId` | Add to wishlist | ✅ |
| DELETE | `/wishlist/:productId` | Remove from wishlist | ✅ |

### 🛒 Cart (`/cart`)

| Method | Endpoint | Description | Auth |
|--------|----------|-------------|------|
| GET | `/cart` | Get user's cart | ✅ |
| POST | `/cart/:productId` | Add to cart | ✅ |
| PATCH | `/cart/:productId` | Update cart item quantity | ✅ |
| DELETE | `/cart/:productId` | Remove from cart | ✅ |

### 💳 Orders (`/orders`)

| Method | Endpoint | Description | Auth |
|--------|----------|-------------|------|
| POST | `/orders/create-payment-order` | Create Razorpay payment order | ✅ |
| POST | `/orders/verify-payment` | Verify payment & place order | ✅ |
| GET | `/orders` | Get user's order history | ✅ |
| GET | `/orders/:id` | Get single order details | ✅ |

---

## 🔑 Environment Variables

| Variable | Description |
|----------|-------------|
| `MONGO_URI` | MongoDB Atlas connection string |
| `JWT_SECRET` | Secret key for JWT token signing |
| `RAZORPAY_KEY_ID` | Razorpay API Key ID |
| `RAZORPAY_KEY_SECRET` | Razorpay API Key Secret |

---

## 🧪 Test Payment (Razorpay Test Mode)

Use these test credentials in Razorpay's payment modal:

| Field | Value |
|-------|-------|
| Card Number | `4111 1111 1111 1111` |
| Expiry | Any future date |
| CVV | Any 3 digits |
| OTP | Click **Skip OTP** |

---

## 👨‍💻 Author

**Naman Aneja**

---

## 📄 License

This project is for educational purposes.
