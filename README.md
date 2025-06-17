# 👥 HRMS FastAPI - Human Resource Management System

A modern, scalable Human Resource Management System designed to streamline team coordination, resource allocation, and project management for growing organizations. 🚀

## 🎯 What It Does

This HRMS provides a complete solution for managing human resources in technology-driven organizations. It handles everything from employee onboarding to project delivery tracking, with real-time resource availability and comprehensive reporting capabilities.

### 🔑 Key Capabilities

- **Smart Resource Management** 🧠 - Automatically tracks employee availability and prevents double-booking
- **Project-Centric Workflow** 📋 - Links employees, time tracking, and deliverables to specific projects
- **Role-Based Access Control** 🔐 - Granular permissions for users, admins, and super admins
- **Real-Time Analytics** 📊 - Live dashboards showing utilization rates, bench time, and project status
- **Automated Background Tasks** 🤖 - Self-maintaining system that cleans up expired bookings

## 💼 Business Value

### For HR Teams 👨‍💼👩‍💼
- Eliminate scheduling conflicts with automated availability tracking ✅
- Generate compliance reports with accurate time and leave records 📄
- Monitor team utilization to optimize workforce planning 📈

### For Project Managers 🎯  
- Real-time visibility into resource allocation across projects 👀
- Historical data for better project estimation and planning 📊
- Skills-based team member selection for optimal project outcomes 🎪

### For Leadership 🏆
- Data-driven insights into team productivity and utilization 📈
- Cost analysis through detailed time tracking and resource allocation 💰
- Scalable system that grows with your organization 📏

## 🔌 API Overview

The system exposes RESTful APIs organized into logical modules:

### 🔑 Authentication & Authorization
```http
POST http://<your-ip>:7007/auth/login
Content-Type: application/json

{
  "email": "john.doe@company.com",
  "password": "secure123",
  "role": "user"
}
```

Returns JWT tokens for accessing protected endpoints with role-based permissions. 🎫

### 👥 Team Management
```http
GET http://<your-ip>:7007/team/employee_stats
Authorization: Bearer <token>
```

Provides real-time team insights: 📊
```json
{
  "employee_number": 25,
  "allocated_employee": 18,
  "bench_employee": 7,
  "allocated_employee_details": {
    "alice@company.com": 8,
    "bob@company.com": 6
  },
  "utilization_rate": 72.5
}
```

### 📅 Resource Booking
```http
POST http://<your-ip>:7007/resource/book_resource
Authorization: Bearer <token>
Content-Type: application/json

{
  "email": "developer@company.com",
  "project_id": "60d21b4e8b0f0c1c2c8b4567",
  "start_date": "2025-04-15T00:00:00",
  "end_date": "2025-04-25T00:00:00",
  "hours_booked": 6,
  "priority": "High",
  "ShortTaskName": "API Development"
}
```

Automatically manages availability calendars and prevents conflicts. ⚡

### 🚀 Project Lifecycle
```http
POST http://<your-ip>:7007/projects/create_project
Authorization: Bearer <token>
Content-Type: application/json

{
  "project_name": "E-commerce Platform",
  "allocated_hours": 400,
  "client_name": "TechCorp Inc",
  "manager_email": "pm@company.com",
  "project_type": "Fixed",
  "priority": "High",
  "status": "Development",
  "skills": ["React", "Node.js", "MongoDB"]
}
```

### 📈 Advanced Reporting
```http
POST http://<your-ip>:7007/reports/project_report
Authorization: Bearer <token>
Content-Type: application/json

{
  "date_range": {
    "start_date": "2025-04-01",
    "end_date": "2025-04-30"
  },
  "export_format": "csv"
}
```

Generate comprehensive reports for compliance, billing, and analysis. 📋

## 🏗️ Data Architecture

### 🗄️ Core Collections

**Teams Collection** 👥 - Employee profiles with skills, departments, and roles
```json
{
  "email": "developer@company.com",
  "full_name": "Jane Developer",
  "department": "Backend Developer", 
  "skills": ["Python", "FastAPI", "MongoDB"],
  "role": "user"
}
```

**Resources Collection** 📊 - Dynamic availability tracking
```json
{
  "email": "developer@company.com",
  "available_hours_per_day": {
    "2025-04-15": 2,
    "2025-04-16": 0,
    "2025-04-17": 8
  },
  "Projects": [{
    "booking_id": "BR123456",
    "project_id": "60d21b4e8b0f0c1c2c8b4567",
    "hours_booked": 6,
    "start_date": "2025-04-15",
    "end_date": "2025-04-20"
  }]
}
```

**Projects Collection** 📁 - Complete project metadata
```json
{
  "project_name": "E-commerce Platform",
  "client_name": "TechCorp Inc",
  "allocated_hours": 400,
  "status": "Development",
  "skills": ["React", "Node.js", "MongoDB"]
}
```

## 💡 Use Cases

### 🎬 Scenario 1: New Project Kickoff
1. Project manager creates project with required skills 📝
2. Resources are booked for project duration 📅
3. Real-time reports show project progress and resource utilization 📊

### 🏖️ Scenario 2: Leave Management
1. Manager sets leave through the system 📝
2. System automatically blocks availability for those dates 🚫
3. Resource booking system prevents conflicts during leave period ⚠️
4. Payroll integration receives accurate leave records 💰

### ⚖️ Scenario 3: Resource Optimization
1. Admin views real-time utilization dashboard 👀
2. Identifies underutilized team members (bench time) 🔍
3. Reassigns resources to high-priority projects 🔄
4. Tracks impact on overall team productivity 📈

## ⚡ Performance Capabilities

### 📈 Scalability Features
- **Async MongoDB Operations** 🚀 - Handles concurrent requests efficiently
- **Background Task Processing** 🤖 - Automated cleanup prevents data bloat
- **Prometheus Metrics** 📊 - Built-in monitoring for production environments
- **Docker Containerization** 🐳 - Easy horizontal scaling

### ⚡ Real-Time Processing
- Live availability updates across all resource bookings 🔄
- Instant conflict detection for scheduling ⚠️
- Real-time dashboard updates for management insights 📊

## 🔗 Integration Capabilities

The system is designed for enterprise integration:

- **RESTful APIs** 🌐 - Standard HTTP protocols for easy integration
- **JWT Authentication** 🎫 - Compatible with existing identity providers
- **Webhook Support** 📡 - Real-time notifications to external systems
- **CSV/Excel Export** 📄 - Seamless data exchange with existing tools
- **Prometheus Metrics** 📊 - Integration with monitoring infrastructure

---

Explore the interactive API documentation at `http://<your-ip>:7007/docs` to see the full capabilities in action. 🎯✨
