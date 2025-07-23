# 🏨 HorecaH Peru - B2B Hospitality Marketplace

<div align="center">

**The Ultimate B2B Marketplace for Peru's Hospitality Industry**

[![React](https://img.shields.io/badge/React-18.2.0-61DAFB?style=for-the-badge&logo=react)](https://reactjs.org/)
[![Laravel](https://img.shields.io/badge/Laravel-10.x-FF2D20?style=for-the-badge&logo=laravel)](https://laravel.com/)
[![Flutter](https://img.shields.io/badge/Flutter-3.1+-02569B?style=for-the-badge&logo=flutter)](https://flutter.dev/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.0-3178C6?style=for-the-badge&logo=typescript)](https://www.typescriptlang.org/)
[![PHP](https://img.shields.io/badge/PHP-8.1+-777BB4?style=for-the-badge&logo=php)](https://php.net/)

[![MIT License](https://img.shields.io/badge/License-MIT-green.svg?style=for-the-badge)](https://choosealicense.com/licenses/mit/)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=for-the-badge)](http://makeapullrequest.com)
[![Stars](https://img.shields.io/github/stars/yourusername/horecah-peru?style=for-the-badge)](https://github.com/yourusername/horecah-peru/stargazers)

[🚀 Live Demo](#-live-demo) • [📱 Features](#-features) • [🛠️ Tech Stack](#️-tech-stack) • [⚡ Quick Start](#-quick-start) • [📖 Documentation](#-documentation)

</div>

---

## 🎯 **Problem & Solution**

### **The Challenge**
Peru's hospitality industry (HORECA - Hotels, Restaurants, Cafés) faces significant challenges:
- 🔍 **Fragmented marketplace** for equipment and services
- 📞 **Inefficient communication** between buyers and suppliers
- 💰 **Lack of transparent pricing** and payment systems
- 🏢 **Limited franchise and business opportunities** visibility

### **Our Solution**
HorecaH Peru is a comprehensive **full-stack B2B marketplace** that revolutionizes how hospitality businesses connect, trade, and grow in Peru.

---

## ✨ **Key Features**

<table>
<tr>
<td width="50%">

### 📱 **Mobile App (Flutter)**
- 🛒 **Multi-category marketplace** (Furniture, Equipment, Services)
- 💬 **Real-time chat** with Firebase integration
- 📸 **Advanced image upload** with gallery management
- 🗺️ **Location-based search** with Google Maps
- 💳 **Secure payments** via Stripe integration
- 👤 **User profiles** and business verification
- ⭐ **Favorites & saved searches**

</td>
<td width="50%">

### 🖥️ **Admin Panel (React)**
- 👥 **User management** with approval workflows
- 📋 **Content moderation** and listing approval
- 📊 **Analytics dashboard** with real-time metrics
- 💰 **Payment management** and transaction tracking
- 🏷️ **Category & subcategory** management
- 💬 **Message monitoring** and customer support
- 🛠️ **Service provider** verification system

</td>
</tr>
</table>

### 🔧 **Backend API (Laravel)**
- 🔐 **Secure authentication** with Laravel Sanctum
- ⚡ **Real-time messaging** with WebSockets
- 📱 **SMS notifications** via Twilio integration
- 🗄️ **Robust database** with migration system
- 📁 **File management** and multimedia handling
- 🔄 **RESTful API** with comprehensive endpoints

---

## 🏗️ **Architecture Overview**

```mermaid
graph TB
    subgraph "Frontend Applications"
        A[React Admin Panel<br/>TypeScript + Vite + Tailwind]
        B[Flutter Mobile App<br/>iOS + Android + Web]
    end
    
    subgraph "Backend Services"
        C[Laravel API Server<br/>PHP 8.1 + MySQL]
        D[WebSocket Server<br/>Real-time Messaging]
        E[File Storage<br/>Images + Documents]
    end
    
    subgraph "Third-party Services"
        F[Firebase<br/>Auth + Cloud Storage]
        G[Stripe<br/>Payment Processing]
        H[Twilio<br/>SMS Notifications]
        I[Google Maps<br/>Location Services]
    end
    
    A --> C
    B --> C
    B --> F
    B --> G
    C --> D
    C --> H
    B --> I
    C --> E
```

---

## 🛠️ **Tech Stack**

<table>
<tr>
<td width="33%">

### **Frontend**
- ⚛️ **React 18** with TypeScript
- 🎨 **Tailwind CSS** + Material-UI
- ⚡ **Vite** for lightning-fast development
- 🔄 **Redux Toolkit** for state management
- 📱 **Flutter 3.1+** for mobile apps
- 🎯 **GetX** for Flutter state management

</td>
<td width="33%">

### **Backend**
- 🐘 **Laravel 10** with PHP 8.1+
- 🔐 **Laravel Sanctum** authentication
- 🌐 **WebSockets** for real-time features
- 🗄️ **MySQL** database
- 📧 **Twilio SDK** for SMS
- 🔄 **Ratchet** for WebSocket handling

</td>
<td width="33%">

### **Integrations**
- 🔥 **Firebase** (Auth, Firestore, Storage)
- 💳 **Stripe** payment processing
- 🗺️ **Google Maps API**
- 📱 **Twilio** SMS service
- 📧 **EmailJS** for notifications
- ☁️ **Cloud storage** solutions

</td>
</tr>
</table>

---

## ⚡ **Quick Start**

### **Prerequisites**
- 📦 Node.js 18+ and npm/yarn
- 🐘 PHP 8.1+ and Composer
- 📱 Flutter SDK 3.1+
- 🗄️ MySQL 8.0+
- 🔥 Firebase project setup

### **1. Clone the Repository**
```bash
git clone https://github.com/yourusername/horecah-peru.git
cd horecah-peru
```

### **2. Setup Laravel Backend**
```bash
cd Laravel-backend
composer install
cp .env.example .env
php artisan key:generate
php artisan migrate --seed
php artisan serve
```

### **3. Setup React Admin Panel**
```bash
cd React-Admin
npm install
npm run dev
```

### **4. Setup Flutter Mobile App**
```bash
cd "Flutter -frontend"
flutter pub get
flutter run
```

---

## 🔧 **Environment Configuration**

### **Laravel (.env)**
```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=horecah_peru
DB_USERNAME=your_username
DB_PASSWORD=your_password

TWILIO_SID=your_twilio_sid
TWILIO_TOKEN=your_twilio_token
```

### **Flutter (.env)**
```env
API_URL=https://your-api-url.com
STRIPE_PUBLISHABLE_KEY=pk_test_your_stripe_key
GOOGLE_MAPS_API_KEY=your_google_maps_key
```

---

## 📖 **API Documentation**

### **Authentication Endpoints**
```http
POST /api/auth/login
POST /api/auth/register
POST /api/auth/logout
```

### **Product Management**
```http
GET    /api/products           # List all products
POST   /api/products           # Create new product
PUT    /api/products/{id}      # Update product
DELETE /api/products/{id}      # Delete product
```

### **Real-time Features**
```javascript
// WebSocket connection for real-time chat
const socket = new WebSocket('ws://localhost:6001');
socket.on('new-message', (data) => {
    // Handle incoming message
});
```

## 📞 **Support & Contact**

- 📧 **Email**: montecristodev2025@gmail.com
- 💬 **Telegram**: [Join our community](https://t.me/alpha_T0108)
- 🐦 **Twitter**: [@HorecahPeru](https://twitter.com/horecahperu)

---

<div align="center">

**⭐ Star this repository if you find it helpful!**


</div> 
