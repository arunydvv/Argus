<!-- All routes would be listed here -->
## 🌐 API Routes

Argus exposes REST endpoints to manage monitors, check status, and retrieve reliability metrics.

### Base URL

```
http://localhost:4000/api

```

----------

## 🩺 Health & System

### **GET /health**

Check if Argus service is running.

**Response**

```json
{
  "status": "ok",
  "timestamp": "2026-02-23T10:00:00Z"
}

```

----------

## 🔍 Monitors

### **POST /monitors**

Create a new endpoint monitor.

**Body**

```json
{
  "name": "Auth Service",
  "url": "https://api.example.com/auth/health",
  "method": "GET",
  "interval": 60
}

```

**Response**

```json
{
  "id": "mon_123",
  "status": "created"
}

```

----------

### **GET /monitors**

Retrieve all configured monitors.

**Response**

```json
[
  {
    "id": "mon_123",
    "name": "Auth Service",
    "url": "https://api.example.com/auth/health",
    "status": "up"
  }
]

```

----------

### **GET /monitors/:id**

Get details of a specific monitor.

----------

### **PUT /monitors/:id**

Update monitor configuration.

----------

### **DELETE /monitors/:id**

Remove a monitor.

----------

## 📊 Status & Metrics

### **GET /status/:id**

Get current uptime status.

**Response**

```json
{
  "monitorId": "mon_123",
  "status": "up",
  "lastChecked": "2026-02-23T09:59:00Z"
}

```

----------

### **GET /metrics/:id**

Retrieve latency and reliability metrics.

**Response**

```json
{
  "avgResponseTime": 120,
  "uptime": "99.98%",
  "lastDowntime": "2026-02-20T03:21:00Z"
}

```

----------

## 🚨 Alerts (Optional Integration)

### **POST /alerts/test**

Trigger a test alert.

### **POST /alerts/webhook**

Receive failure notifications.

----------

## 🧪 Example Curl

```bash
curl -X POST http://localhost:4000/api/monitors \
-H "Content-Type: application/json" \
-d '{"name":"Main API","url":"https://api.example.com/health"}'

```

----------

## 📌 Status Codes

    Code			Meaning

    200				Success

    201				Created

    400				Bad Request

    404				Not Found

    500 			Server Error
