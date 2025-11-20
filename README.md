# 🛒 GreatKart E-commerce Platform with Advanced User Behavior Tracking

A comprehensive e-commerce platform built with Django, featuring advanced user behavior analytics and PostgreSQL integration. This project combines a fully functional online shopping platform with sophisticated user interaction tracking capabilities.

![Django](https://img.shields.io/badge/Django-3.1-green.svg)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-16.10-blue.svg)
![Python](https://img.shields.io/badge/Python-3.8+-yellow.svg)
![License](https://img.shields.io/badge/License-MIT-red.svg)

## 🌟 Features

### E-commerce Platform
- **Complete Shopping Cart System** - Add, remove, and manage items
- **User Account Management** - Registration, login, profile management
- **Product Catalog** - Browse products by categories
- **Order Management** - Complete order processing system
- **Admin Interface** - Enhanced admin panel with thumbnails
- **Security Features** - Admin honeypot protection and session management

### Advanced User Behavior Tracking
- **Real-time Interaction Tracking** - Comprehensive user activity monitoring
- **PostgreSQL Analytics Backend** - Robust data storage and analysis
- **Mouse & Click Tracking** - Detailed interaction patterns
- **Keyboard Activity Monitoring** - Form interaction analysis
- **Page Navigation Analytics** - User journey mapping
- **E-commerce Event Tracking** - Purchase behavior analysis
- **Engagement Metrics** - User engagement scoring system
- **Session Management** - Complete user session analytics

## 🎯 User Behavior Analytics Features

### Tracked Interactions
- ✅ **Mouse Clicks** - Coordinates, timestamps, target elements
- ✅ **Mouse Movements** - Movement patterns and coordinates
- ✅ **Scroll Events** - Scroll position and behavior
- ✅ **Keyboard Activities** - Key presses and form interactions
- ✅ **Form Interactions** - Field changes and submissions
- ✅ **Page Navigation** - Page visits and time spent
- ✅ **Touch Events** - Mobile device interactions
- ✅ **Window Resizing** - Viewport changes
- ✅ **Time Tracking** - Accurate time-on-page measurements

### Database Models
- **UserBehaviorSession** - Session-level tracking
- **UserBehaviorLog** - Detailed interaction logs (23+ fields)
- **EcommerceEvent** - Commerce-specific events
- **UserEngagementMetrics** - Engagement scoring and analytics

## 🚀 Quick Start

### Prerequisites
- Python 3.8+
- PostgreSQL 12+
- pip (Python package manager)

### Installation

1. **Clone the Repository**
   ```bash
   git clone https://github.com/dev-rathankumar/greatkart-pre-deploy.git
   cd greatkart-pre-deploy
   ```

2. **Create Virtual Environment**
   ```bash
   python -m venv cenv
   
   # Windows
   cenv\Scripts\activate
   
   # macOS/Linux
   source cenv/bin/activate
   ```

3. **Install Dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **PostgreSQL Setup**
   ```sql
   -- Create database
   CREATE DATABASE Tracker;
   CREATE USER postgres WITH PASSWORD 'your_password';
   GRANT ALL PRIVILEGES ON DATABASE Tracker TO postgres;
   ```

5. **Environment Configuration**
   Create a `.env` file in the root directory:
   ```env
   SECRET_KEY=your-secret-key-here
   DEBUG=True
   DB_NAME=Tracker
   DB_USER=postgres
   DB_PASSWORD=your_password
   DB_HOST=localhost
   DB_PORT=5432
   ```

6. **Database Migration**
   ```bash
   cd greatkart
   python manage.py makemigrations
   python manage.py migrate
   python manage.py migrate tracking
   ```

7. **Create Superuser**
   ```bash
   python manage.py createsuperuser
   python manage.py create_missing_profiles
   ```

8. **Run Development Server**
   ```bash
   python manage.py runserver
   ```

   Visit `http://127.0.0.1:8000` to access the application.

## 📊 Analytics Dashboard

### Access Analytics
1. Login as admin/staff user
2. Navigate to `/admin/` for Django admin interface
3. View tracking data in the tracking models section

### Available Analytics
- **User Sessions** - Complete session analytics
- **Behavior Logs** - Detailed interaction data
- **E-commerce Events** - Shopping behavior analysis
- **Engagement Metrics** - User engagement scoring

### Management Commands
```bash
# Verify PostgreSQL connection
python manage.py verify_postgresql

# Test user interactions
python manage.py test_user_interactions

# Test tracking endpoint
python manage.py test_endpoint
```

## 🏗️ Project Structure

```
greatkart/
├── greatkart/                 # Main project directory
│   ├── settings.py           # Django settings with PostgreSQL config
│   ├── urls.py              # Main URL configuration
│   ├── tracking_views.py    # User behavior tracking views
│   └── wsgi.py              # WSGI configuration
├── tracking/                 # User behavior tracking app
│   ├── models.py            # Analytics database models
│   ├── views.py             # Analytics dashboard views
│   ├── admin.py             # Admin interface for analytics
│   └── management/          # Management commands
├── accounts/                 # User account management
├── store/                   # Product catalog
├── carts/                   # Shopping cart functionality
├── orders/                  # Order processing
├── category/                # Product categories
├── templates/               # HTML templates
│   ├── base.html           # Base template with tracking integration
│   └── tracking/           # Analytics templates
├── static/                  # Static files
│   └── js/                 # JavaScript files
│       └── userBehaviour.min.js  # Tracking library
├── media/                   # Media files
└── requirements.txt         # Python dependencies
```

## 🔧 Configuration

### Database Settings
The project uses PostgreSQL as the primary database. Configuration is in `settings.py`:

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'Tracker',
        'USER': 'postgres',
        'PASSWORD': 'your_password',
        'HOST': 'localhost',
        'PORT': '5432',
    }
}
```

### Tracking Configuration
User behavior tracking is configured in `templates/base.html`:

```javascript
userBehaviour.config({
    clicks: true,                    // Track mouse clicks
    mouseMovement: true,             // Track mouse movements
    mouseScroll: true,               // Track scroll events
    keyboardActivity: true,          // Track keyboard input
    formInteractions: true,          // Track form interactions
    pageNavigation: true,            // Track page navigation
    touchEvents: true,               // Track touch events
    processTime: 15,                 // Process data every 15 seconds
});
```

## 🔌 API Endpoints

### Tracking API
- **POST** `/api/track-behavior/` - Submit user behavior data

Example request:
```json
{
  "trackingData": {
    "clicks": [...],
    "mouseMovement": [...],
    "keyboardActivity": [...]
  },
  "page": "/current-page/",
  "timestamp": "2025-11-20T12:00:00Z",
  "userAgent": "Mozilla/5.0...",
  "screenResolution": {"width": 1920, "height": 1080}
}
```

## 📝 Database Schema

### Key Tables
- `tracking_userbehaviorsession` - User session tracking
- `tracking_userbehaviorlog` - Detailed interaction logs
- `tracking_ecommerceevent` - E-commerce specific events
- `tracking_userengagementmetrics` - User engagement analytics

### Sample Queries
```sql
-- Get user click data
SELECT clicks_data FROM tracking_userbehaviorlog 
WHERE user_id = 1 AND clicks_data IS NOT NULL;

-- Analyze page views
SELECT page_url, COUNT(*) as views 
FROM tracking_userbehaviorlog 
GROUP BY page_url ORDER BY views DESC;

-- User engagement scores
SELECT user_id, engagement_score, total_sessions 
FROM tracking_userengagementmetrics 
ORDER BY engagement_score DESC;
```

## 🧪 Testing

### Run Tests
```bash
# Test database connection
python manage.py verify_postgresql

# Test tracking functionality
python manage.py test_endpoint

# Run Django tests
python manage.py test
```

### Verify Tracking
1. Start the development server
2. Navigate through the application
3. Check the PostgreSQL database for tracking data
4. Review analytics in the admin interface

## 🛡️ Security Features

- **CSRF Protection** - All forms protected against CSRF attacks
- **Admin Honeypot** - Fake admin login to catch malicious attempts
- **Session Management** - Automatic session timeout
- **SQL Injection Protection** - Django ORM provides protection
- **XSS Protection** - Template auto-escaping enabled

## 📦 Dependencies

### Core Dependencies
- **Django 3.1** - Web framework
- **psycopg2** - PostgreSQL adapter
- **Pillow** - Image processing
- **python-decouple** - Environment variable management

### Additional Features
- **django-admin-thumbnails** - Enhanced admin interface
- **django-session-timeout** - Session management
- **django-admin-honeypot** - Security enhancement

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/new-feature`)
3. Commit your changes (`git commit -am 'Add new feature'`)
4. Push to the branch (`git push origin feature/new-feature`)
5. Create a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🔍 Troubleshooting

### Common Issues

**Database Connection Error**
```bash
# Check PostgreSQL service
# Windows: services.msc -> PostgreSQL
# Verify database credentials in .env file
```

**Static Files Not Loading**
```bash
python manage.py collectstatic
```

**Tracking Data Not Saving**
```bash
# Verify tracking migrations
python manage.py migrate tracking

# Test tracking endpoint
python manage.py test_endpoint
```

## 📞 Support

For support and questions:
- Create an issue in the GitHub repository
- Check the troubleshooting section
- Review Django and PostgreSQL documentation

## 🏆 Acknowledgments

- Django community for the excellent framework
- PostgreSQL team for the robust database system
- Contributors to the open-source libraries used in this project

---

**Built with ❤️ using Django and PostgreSQL**