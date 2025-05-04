# airbnb-clone-project

## Team Roles

This section outlines the various team roles involved in the project, along with their core responsibilities. These roles are essential for successful planning, development, and deployment of the software product.

### 1. Project Manager
Responsible for overseeing the project from start to finish, ensuring it meets deadlines, stays within budget, and fulfills scope requirements. Acts as the main point of communication between stakeholders and the team.

### 2. Business Analyst
Bridges the gap between stakeholders and the technical team by gathering, analyzing, and translating business requirements into technical specifications.

### 3. UX/UI Designer
Focuses on user experience and interface design. Ensures the product is intuitive, user-friendly, and visually consistent.

### 4. Frontend Developer
Implements the visual components of the application. Converts UI designs into interactive web pages using HTML, CSS, JavaScript, and frameworks like React or Angular.

### 5. Backend Developer
Handles the server-side logic, API development, authentication, and integration with databases or third-party services. Ensures performance, scalability, and security of the backend system.

### 6. Database Administrator (DBA)
Designs, maintains, and optimizes the database systems. Responsible for ensuring data integrity, security, and availability.


## ⚙️ Technology Stack

Below is a list of technologies used in this project along with their purposes:

### 🐍 Django
A high-level Python web framework used to build the backend logic and APIs. It provides tools for rapid development, secure authentication, and an admin interface for managing data.

### 🧰 Django REST Framework (DRF)
A powerful toolkit for building RESTful APIs in Django. It simplifies the creation of serializers, views, and URL routing for endpoints like users, properties, bookings, etc.

### 🐘 PostgreSQL
A robust, open-source relational database used to store structured data such as users, properties, bookings, payments, and reviews.

### 🔍 GraphQL
A query language for APIs that enables clients to request exactly the data they need. Used alongside REST to offer flexible and efficient querying of backend data.

### 🧵 Celery
An asynchronous task queue used for background job processing, such as sending notifications or handling delayed tasks like booking confirmations.

### ⚡ Redis
An in-memory data store used for caching and managing Celery task queues. Improves performance by reducing database load and speeding up task execution.

### 🐳 Docker
A containerization tool that ensures consistent development, testing, and deployment environments. All services are containerized for portability and isolation.

### 🔁 CI/CD Pipelines
Automated pipelines for building, testing, and deploying code. Helps maintain code quality and reduces manual intervention in deployments.

### 7. DevOps Engineer
Manages infrastructure, deployment pipelines, and automation. Ensures the application can be reliably deployed and scaled in various environments.

### 8. Quality Assurance (QA) Engineer
Tests the application for bugs and usability issues. Develops test plans, automates tests when possible, and ensures the product meets quality standards before release.


## 🗄️ Database Design

The database for this project is designed to support core features such as user management, property listings, bookings, payments, and reviews. Below are the key entities, important fields, and their relationships.

### 1. Users
Represents the people using the platform (both guests and hosts).

**Key Fields:**
- `id`: Primary key identifier
- `name`: Full name of the user
- `email`: Unique email address
- `password`: Hashed password for authentication
- `is_host`: Boolean flag to indicate host status

**Relationships:**
- A user can create multiple properties.
- A user can make multiple bookings.
- A user can leave multiple reviews.

---

### 2. Properties
Represents the properties listed by hosts for rent.

**Key Fields:**
- `id`: Primary key identifier
- `title`: Title of the property
- `description`: Detailed information about the property
- `price_per_night`: Cost of booking per night
- `host_id`: Foreign key to the User (host)

**Relationships:**
- A property is owned by one user (host).
- A property can have many bookings.
- A property can receive many reviews.

---

### 3. Bookings
Represents the reservations made by users for properties.

**Key Fields:**
- `id`: Primary key identifier
- `user_id`: Foreign key to the User (guest)
- `property_id`: Foreign key to the Property
- `start_date`: Check-in date
- `end_date`: Check-out date

**Relationships:**
- A booking belongs to one user and one property.
- A booking is associated with a payment.

---

### 4. Payments
Tracks the payment transactions for bookings.

**Key Fields:**
- `id`: Primary key identifier
- `booking_id`: Foreign key to the Booking
- `amount`: Total amount paid
- `status`: Payment status (e.g., completed, pending, failed)
- `timestamp`: Date and time of the transaction

**Relationships:**
- A payment is linked to one booking.

---

### 5. Reviews
Allows users to leave feedback on properties.

**Key Fields:**
- `id`: Primary key identifier
- `user_id`: Foreign key to the User (reviewer)
- `property_id`: Foreign key to the Property
- `rating`: Numerical rating (e.g., 1–5)
- `comment`: Textual review content

**Relationships:**
- A review belongs to one user and one property.

