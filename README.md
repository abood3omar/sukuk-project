# Sukuk Platform | Enterprise Real Estate Asset Management

<div align="center">
  <img src="images/logo.png" alt="Sukuk Logo" width="150"/>
  <br>
  
  ![Laravel](https://img.shields.io/badge/Backend-Laravel_10-FF2D20?style=for-the-badge&logo=laravel)
  ![PHP](https://img.shields.io/badge/Language-PHP_8.2-777BB4?style=for-the-badge&logo=php)
  ![SQL Server](https://img.shields.io/badge/Database-SQL_Server-CC2927?style=for-the-badge&logo=microsoft-sql-server)
  ![Google Maps](https://img.shields.io/badge/API-Google_Maps-4285F4?style=for-the-badge&logo=google-maps)
  ![Security](https://img.shields.io/badge/Security-Dynamic_RBAC-forestgreen?style=for-the-badge&logo=security-scorecard)
</div>

> **⚠️ Proprietary Software Notice:**
> This project was developed for **Rikaz Advanced**. The repository serves as a **Technical Showcase** of the architecture and development patterns used.
> **Source code is confidential** and available for technical review upon request by authorized recruiters.

---

## 🏗️ System Architecture & Engineering
Sukuk is not just a CRUD application; it is a complex **SaaS-ready platform** designed to manage high-value real estate assets. The system is built on a **Modular Monolith** architecture to ensure scalability and maintainability.

### 1. Dynamic Role-Based Access Control (RBAC) 🛡️
Unlike standard permission packages, I engineered a **Custom Dynamic Permission Engine**.
* **Concept:** Permissions are not just hardcoded; they are stored as `System Modules` (Entities) and `Actions` (Create, Edit, Approve, Export).
* **Implementation:** * Created `SystemModuleController` to dynamically manage system capabilities.
    * Implemented strict Middleware: `middleware('permission:module_name,action')`.
    * **Example:** A route like `Route::post('/approve')` is guarded by `permission:users,approve`, ensuring only specific roles can trigger critical business logic.

### 2. User Subscription Lifecycle (State Machine) 🔄
The system handles complex user statuses beyond simple Login/Logout. I implemented a strict **Subscription Workflow**:
* **Flow:** `Guest` → `Registration` → `Pending (Review)` → `Approved` → `Active` (or `Rejected`/`Suspended`).
* **Security:** Using `CheckUserStatus` Middleware to intercept requests from users with expired or suspended subscriptions instantly.
* **Logic:** Dedicated controllers (`approve`, `renew`, `reject`) to handle the business rules for each state transition.

### 3. Advanced Integrations & Localization 🌍
* **Google Maps API:** Deep integration for visualizing asset locations with custom markers based on `Sukuk Type`.
* **Multi-Tenancy Preparation:** The database is designed with "Databank" modules (Countries, Provinces, Cities) to support international data scalability.
* **Localization:** Full Arabic/English support using Middleware-based Locale switching (`session()->put('locale', $lang)`), ensuring all responses and UI elements are translated dynamically.

### 4. Enterprise Database Design (SQL Server) 🗄️
* Leveraged **Microsoft SQL Server** for robust data handling suitable for financial records.
* **Complex Relationships:** Designed a normalized schema handling `Evaluations`, `Authorities`, and `Portfolios` with strict foreign key constraints.
* **Data Integrity:** Used Transactions for critical operations like Subscription Renewal and Asset Transfer.

---

## 💻 Technical Stack Overview

| Category | Technology | Usage |
| :--- | :--- | :--- |
| **Backend Framework** | **Laravel 10** | Core Logic, Service Container, Eloquent ORM. |
| **Database** | **MS SQL Server** | Enterprise-grade data storage. |
| **Frontend** | **Tailwind CSS & AJAX** | Responsive UI and Asynchronous data loading. |
| **APIs** | **Google Maps API** | Asset Geolocation & Markers. |
| **Security** | **Custom Middleware** | Route Protection, XSS Filtering, Input Sanitization. |

---

## 📸 System Previews (Gallery)

| **Interactive Map & Markers** | **Dynamic Dashboard** |
|:---:|:---:|
| <img src="images/maps.png" width="400" alt="Google Maps Integration"> | <img src="images/dashboard.png" width="400" alt="Admin Dashboard"> |
| *Filtering Assets via Google Maps API* | *Real-time statistics based on User Role* |

| **Subscription Workflow** | **Evaluation System** |
|:---:|:---:|
| <img src="images/users.png" width="400" alt="User Management"> | <img src="images/eval.png" width="400" alt="Evaluations"> |
| *Admin panel for approving/rejecting users* | *Asset evaluation reports* |

---

## 🚀 Key Achievements
* **Secure API Design:** Built internal APIs for `SearchResultController` to handle property searching with complex filters securely.
* **Code Reusability:** Used **Traits** and **Service Classes** to handle the `Import/Export` logic across different modules (Sukuk, Evaluations).
* **Performance:** Optimized SQL queries using Eager Loading to handle large datasets of "Provinces" and "Cities" without latency.

---

## 📬 Request Access
To view the underlying code structure or discuss the implementation details:

* **Abdalrhman Hamed**
* **Role:** Backend Software Engineer
* **LinkedIn:** [Your Profile Link]
* **Email:** [Your Email]
