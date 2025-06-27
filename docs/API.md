# 🔌 HorecaH Peru API Documentation

## 🚀 Base URL
```
Production: https://api.horecahperu.com/api
Development: http://localhost:8000/api
```

## 🔐 Authentication

HorecaH Peru uses **Laravel Sanctum** for API authentication. Include the token in the Authorization header:

```http
Authorization: Bearer {your-token}
```

### Authentication Endpoints

#### Register User
```http
POST /auth/register
Content-Type: application/json

{
  "name": "Juan Pérez",
  "email": "juan@example.com",
  "password": "password123",
  "password_confirmation": "password123",
  "phone": "+51987654321",
  "business_type": "restaurant"
}
```

#### Login
```http
POST /auth/login
Content-Type: application/json

{
  "email": "juan@example.com",
  "password": "password123"
}
```

**Response:**
```json
{
  "user": {
    "id": 1,
    "name": "Juan Pérez",
    "email": "juan@example.com",
    "verified": true
  },
  "token": "1|abc123..."
}
```

#### Logout
```http
POST /auth/logout
Authorization: Bearer {token}
```

---

## 📦 Products/Listings API

### Get All Products
```http
GET /products?page=1&limit=20&category=furniture&location=lima
```

**Query Parameters:**
- `page` (optional): Page number for pagination
- `limit` (optional): Number of items per page (max 50)
- `category` (optional): Filter by category (`furniture`, `activity`, `franchise`, `supplier`, `consultant`, `entrepreneur`)
- `subcategory` (optional): Filter by subcategory
- `location` (optional): Filter by city/region
- `status` (optional): Filter by status (`sell`, `buy`, `rent`)
- `price_min` (optional): Minimum price filter
- `price_max` (optional): Maximum price filter

**Response:**
```json
{
  "data": [
    {
      "id": 1,
      "title": "Sillas de Restaurante Premium",
      "description": "Juego de 20 sillas para restaurante en excelente estado",
      "price": 2500.00,
      "currency": "PEN",
      "category": "furniture",
      "subcategory": "chairs",
      "status": "sell",
      "condition": "excellent",
      "location": "Lima, Perú",
      "images": [
        "https://storage.horecahperu.com/products/1/chair1.jpg",
        "https://storage.horecahperu.com/products/1/chair2.jpg"
      ],
      "user": {
        "id": 1,
        "name": "Juan Pérez",
        "verified": true
      },
      "created_at": "2024-01-15T10:30:00Z",
      "updated_at": "2024-01-15T10:30:00Z"
    }
  ],
  "meta": {
    "current_page": 1,
    "last_page": 5,
    "per_page": 20,
    "total": 95
  }
}
```

### Create Product
```http
POST /products
Authorization: Bearer {token}
Content-Type: multipart/form-data

{
  "title": "Mesa de Chef Industrial",
  "description": "Mesa de acero inoxidable para cocina industrial",
  "price": 1200.00,
  "category": "furniture",
  "subcategory": "tables",
  "status": "sell",
  "condition": "good",
  "location": "Lima, Perú",
  "phone": "+51987654321",
  "images[]": [file1, file2, file3]
}
```

### Get Product by ID
```http
GET /products/{id}
```

### Update Product
```http
PUT /products/{id}
Authorization: Bearer {token}
```

### Delete Product
```http
DELETE /products/{id}
Authorization: Bearer {token}
```

---

## 👥 Users API

### Get User Profile
```http
GET /user/profile
Authorization: Bearer {token}
```

### Update User Profile
```http
PUT /user/profile
Authorization: Bearer {token}
Content-Type: application/json

{
  "name": "Juan Carlos Pérez",
  "phone": "+51987654321",
  "business_name": "Restaurante El Dorado",
  "business_address": "Av. Principal 123, Lima",
  "current_location": "Lima, Perú"
}
```

### Get User's Products
```http
GET /user/products?status=active
Authorization: Bearer {token}
```

---

## 💬 Messaging API

### Get Chat Rooms
```http
GET /chats/rooms
Authorization: Bearer {token}
```

### Get Messages from Room
```http
GET /chats/rooms/{room_id}/messages?page=1
Authorization: Bearer {token}
```

### Send Message
```http
POST /chats/rooms/{room_id}/messages
Authorization: Bearer {token}
Content-Type: application/json

{
  "message": "Hola, ¿está disponible este producto?",
  "type": "text"
}
```

### Send Image Message
```http
POST /chats/rooms/{room_id}/messages
Authorization: Bearer {token}
Content-Type: multipart/form-data

{
  "type": "image",
  "image": file
}
```

---

## 🏷️ Categories API

### Get All Categories
```http
GET /categories
```

**Response:**
```json
{
  "data": [
    {
      "id": 1,
      "name": "furniture",
      "display_name": "Mobiliario y Equipos",
      "icon": "chair",
      "color": "#3B82F6",
      "subcategories": [
        {
          "id": 1,
          "name": "chairs",
          "display_name": "Sillas"
        },
        {
          "id": 2,
          "name": "tables",
          "display_name": "Mesas"
        }
      ]
    }
  ]
}
```

---

## 💳 Payments API

### Create Payment Intent
```http
POST /payments/intent
Authorization: Bearer {token}
Content-Type: application/json

{
  "amount": 2500.00,
  "currency": "pen",
  "product_id": 1,
  "payment_method": "stripe"
}
```

### Confirm Payment
```http
POST /payments/confirm
Authorization: Bearer {token}
Content-Type: application/json

{
  "payment_intent_id": "pi_abc123...",
  "product_id": 1
}
```

---

## 📊 Admin API

### Get Dashboard Stats
```http
GET /admin/dashboard
Authorization: Bearer {admin-token}
```

### Approve Product
```http
PUT /admin/products/{id}/approve
Authorization: Bearer {admin-token}
```

### Get All Users
```http
GET /admin/users?page=1&status=pending
Authorization: Bearer {admin-token}
```

---

## 🌐 WebSocket Events

Connect to: `ws://localhost:6001` (development)

### Subscribe to Chat Room
```javascript
const socket = io('ws://localhost:6001');

socket.emit('join-room', {
  room_id: 123,
  token: 'bearer-token'
});

socket.on('new-message', (data) => {
  console.log('New message:', data);
});
```

### Real-time Events
- `new-message`: New chat message received
- `user-online`: User comes online
- `user-offline`: User goes offline
- `product-approved`: Product gets approved by admin
- `payment-confirmed`: Payment confirmation

---

## 📱 Mobile-Specific Endpoints

### Upload Product Images
```http
POST /mobile/products/images
Authorization: Bearer {token}
Content-Type: multipart/form-data

{
  "images[]": [file1, file2, file3, file4, file5],
  "product_id": 123
}
```

### SMS Verification
```http
POST /mobile/verify-phone
Content-Type: application/json

{
  "phone": "+51987654321"
}
```

```http
POST /mobile/confirm-phone
Content-Type: application/json

{
  "phone": "+51987654321",
  "code": "123456"
}
```

---

## 🚨 Error Responses

All API endpoints return consistent error responses:

```json
{
  "error": true,
  "message": "Validation failed",
  "errors": {
    "email": ["The email field is required."],
    "password": ["The password must be at least 8 characters."]
  },
  "code": 422
}
```

### Common HTTP Status Codes
- `200` - Success
- `201` - Created
- `400` - Bad Request
- `401` - Unauthorized
- `403` - Forbidden
- `404` - Not Found
- `422` - Validation Error
- `500` - Internal Server Error

---

## 🔄 Rate Limiting

API requests are rate limited:
- **Authenticated users**: 1000 requests per hour
- **Unauthenticated users**: 100 requests per hour
- **Admin users**: 2000 requests per hour

Rate limit headers:
```http
X-RateLimit-Limit: 1000
X-RateLimit-Remaining: 999
X-RateLimit-Reset: 1640995200
```

---

## 📚 SDKs and Libraries

### JavaScript/TypeScript
```bash
npm install @horecahperu/api-client
```

```javascript
import { HorecahClient } from '@horecahperu/api-client';

const client = new HorecahClient({
  baseUrl: 'https://api.horecahperu.com',
  token: 'your-token'
});

const products = await client.products.getAll();
```

### Flutter/Dart
```yaml
dependencies:
  horecah_api: ^1.0.0
```

```dart
import 'package:horecah_api/horecah_api.dart';

final client = HorecahApi(
  baseUrl: 'https://api.horecahperu.com',
  token: 'your-token',
);

final products = await client.products.getAll();
```

---

## 🛠️ Testing

Use our Postman collection for easy API testing:

[![Run in Postman](https://run.pstmn.io/button.svg)](https://god.gw.postman.com/run-collection/horecahperu-api)

Or download the OpenAPI specification:
- [OpenAPI 3.0 Spec](https://api.horecahperu.com/docs/api-docs.json)

---

## 📞 Support

For API support:
- 📧 **Email**: api-support@horecahperu.com
- 💬 **Discord**: [#api-help](https://discord.gg/horecahperu)
- 📖 **Documentation**: [docs.horecahperu.com](https://docs.horecahperu.com)

---

**Happy coding! 🚀** 