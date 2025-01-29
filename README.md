# API Documentation

## Base URL
```
https://bolt.visitoai.com/api/v1.0
```

---

## Authorization
To use this API, you must obtain a token and include it in the request headers as follows:

```
Authorization: Bearer ${token}
```

---

## 1. Templates

### 1.1 List Templates
**Endpoint:**
```
GET /templates
```

**Example Response:**
```json
{
    "success": true,
    "data": [
        {
            "id": "67991fd32a22ff",
            "active": true,
            "templates": [
                {
                    "language": "en",
                    "components": [
                        {
                            "type": "BODY",
                            "text": "Hi {{1}}, we are excited to welcome you!",
                            "parameters": [
                                {
                                    "type": "text",
                                    "text": "username"
                                }
                            ]
                        },
                        {
                            "type": "BUTTONS",
                            "buttons": [
                                {
                                    "type": "URL",
                                    "text": "Check-in"
                                }
                            ],
                            "parameters": [
                                {
                                    "type": "text",
                                    "text": "url"
                                }
                            ]
                        }
                    ]
                }
            ]
        }
    ]
}
```

---

### 1.2 Send Templates
**Endpoint:**

```
POST /templates/{id}/send
```

**Request Body:**
```json
{
    "to": "525512345678",
    "language": "en",
    "parameters": [
        {
            "type": "BODY",
            "name": "username",
            "value": "Juan Perez"
        },
        {
            "type": "BUTTONS",
            "name": "url",
            "value": "https://check-in.hotel/123451234"
        }
    ]
}

**Example Success Response:**
```json
{
    "success": true,
    "data": {
        "message": {
            "id": "679a4c5dc26e774f4a438e85",
            "waId": "wamid.HBgNNTIxNTU4NTY1NTQ3OBUCABEYEjdGRkFBMTNENTAxNkIzQ0E1RQA="
        }
    }
}
```
