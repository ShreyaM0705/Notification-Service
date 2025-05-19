

---

# 📬 Notification Service

This project is a **FastAPI-based asynchronous notification service** that supports **Email, SMS, and In-App** notification types using **RabbitMQ** for queueing and **SQLite** for storage.

---

## 🚀 Features

* FastAPI REST API to create and fetch notifications.
* Asynchronous processing of notifications using RabbitMQ.
* SQLite for persistence.
* Retry mechanism with exponential backoff.
* Simulated processing for email, SMS, and in-app messages.

---

## 🛠️ Setup Instructions

### 1. Clone the repository

```bash
git clone <your-repo-url>
cd <your-project-folder>
```

### 2. Set up a virtual environment (Windows)

```bash
python -m venv venv
.\venv\Scripts\activate
```

If PowerShell gives an execution policy error, run:

```powershell
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
```

### 3. Install dependencies

```bash
pip install fastapi uvicorn sqlalchemy pika pydantic
```

### 4. Start RabbitMQ

Make sure RabbitMQ is installed and running on default port (`5672`):

* You can install RabbitMQ via Docker:

```bash
docker run -d --hostname my-rabbit --name some-rabbit -p 5672:5672 rabbitmq:3
```

### 5. Run the FastAPI app

```bash
uvicorn 19610eb6-3ecd-4d98-b7a9-e72d3f71cf2d:app --reload
```

> Make sure the filename matches or rename the file to `main.py` for simplicity.

---

## 🧪 API Usage

### Create a Notification

```http
POST /notifications
```

```json
{
  "user_id": 1,
  "type": "email",
  "content": "Hello from Notification Service!"
}
```

### Get Notifications for a User

```http
GET /users/1/notifications
```

---

## ✅ Assumption
Email, SMS, and in-app delivery** are simulated via logging. Real APIs (SMTP, Twilio, WebSockets) should be integrated in production.
No user authentication** is implemented.
  Single-threaded SQLite** is used for simplicity. Switch to PostgreSQL/MySQL for scalability.
RabbitMQ is running locally** and accessible with default `guest:guest` credentials.



## 🧹 To Do (Future Improvements)

* Add real message sending APIs.
* Implement user authentication.
* Add Docker and `.env` configuration.
* Write tests for API and processing logic.

