# 🏢 Kolte-Patil Project Portal (V4 Prototype)

This repository contains the prototype implementation of the **Kolte-Patil Portal**, designed specifically to run locally for management review. The application architecture features a decoupled Next.js (React) administrative frontend and a Node.js (Express) backend powered by a PostgreSQL database.

---

## 🛑 Prerequisites for Local Execution
To run this application locally on your machine, you must have the following installed:
1. **Node.js** (v18.x or higher)
2. **PostgreSQL** (Running locally on default port `5432`)
3. **Git**

---

## 🛠️ Step 1: Database Setup
Before starting the servers, you need to create a local PostgreSQL database for the portal to store its properties.
1. Open your terminal or PGAdmin.
2. Create an empty PostgreSQL database named **`kolte_patil_portal`**.
*(Ensure the database is actively running in the background).*

---

## ⚙️ Step 2: Backend API Configuration
The backend server handles all database transactions, API requests, and physical image uploads.

1. Open your terminal and navigate to the backend folder:
   ```bash
   cd backend
   ```
2. Install all required Node.js dependencies:
   ```bash
   npm install
   ```
3. Create a `.env` file inside the `/backend` folder. You must provide your local PostgreSQL credentials here. Example:
   ```env
   DATABASE_URL="postgresql://postgres:YOUR_PASSWORD@localhost:5432/kolte_patil_portal?schema=public"
   JWT_SECRET="prototype_secret_key"
   PORT=3001
   ```
   *(Be sure to replace `YOUR_PASSWORD` with your actual local Postgres password).*
4. Sync the 16-parameter V4 database schema into your newly created database:
   ```bash
   npx prisma generate
   npx prisma db push
   ```
5. Start the backend Node server:
   ```bash
   npx ts-node src/index.ts
   ```
*If successful, the terminal will display: `Kolte Patil Backend API Server running on port 3001`.*

---

## 🌐 Step 3: Frontend Dashboard Configuration
The frontend is the visual administrative framework built using Next.js. Leave your backend terminal running and open a **new** terminal window.

1. Navigate to the frontend folder:
   ```bash
   cd admin-portal
   ```
2. Install the React dependencies:
   ```bash
   npm install
   ```
3. Start the Next.js development server:
   ```bash
   npm run dev
   ```

---

## 🚀 Step 4: Access the Live Prototype!
With both the backend (`3001`) and frontend (`3000`) servers actively running on your machine:
1. Open Google Chrome (or any modern graphical browser).
2. Go to: **`http://localhost:3000`**
3. You will be greeted by the Kolte-Patil admin login screen. The dashboard logic is hard-linked directly to your local background server. You can immediately begin creating, archiving, and editing real estate listings!

---

*Note: Any image or physical file attachments uploaded via the "New Project" form will be saved securely to the `/backend/uploads` directory on your hard drive for local testing purposes.*
