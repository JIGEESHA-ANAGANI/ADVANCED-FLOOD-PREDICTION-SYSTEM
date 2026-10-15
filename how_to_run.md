
# Flood Detection Project – Implementation Guide


## Prerequisites

Ensure the following are installed:

- Python **3.10 or higher**
- Node.js **v18+**
- npm
- MySQL Server running on **localhost:3306**

## 1. Create MySQL Database

Open your MySQL client and run the following command:

```sql
CREATE DATABASE flood;
```

---

## 2. Configure Environment Variables

Open the `.env` file in the project.

Replace the password placeholder with your **actual MySQL password**.



## 3. Open Two Terminals

Split your terminal into two windows.

Terminal 1 path:

```
PS C:\Users\....\flood detection\frontend>
```

Terminal 2 path:

```
PS C:\Users\....\flood detection>
```

⚠️ Note:  
`....` represents the **actual path on your system**. It is only shown as an example.

---



# Backend Setup

Run the following commands inside:

```
PS C:\Users\....\flood detection>
```

---

## Step 1 – Create Virtual Environment

```
python -m venv venv
```

---

## Step 2 – Install Python Dependencies

```
pip install -r requirements.txt

python -m ml.training.centralized_trainer   ##executing takes time

python -m ml.training.federated_trainer   ##executing takes time

```


## Step 3 – Run Backend Server

Run the backend using:

```
python -m uvicorn backend.main:app --host 0.0.0.0 --port 8000
```

---

# Frontend Setup

Run the following commands inside:

```
PS C:\Users\....\flood detection\frontend>
```

## Step 1 – Install Node Dependencies

```
npm install
```

---

## Step 2 – Run Frontend

```
npm run dev
```

---

# Project Execution Summary

1. Create MySQL database `flood`
2. Update `.env` with MySQL password
3. Open two terminals
4. Start backend server
5. Start frontend server
6. Access the application in your browser
