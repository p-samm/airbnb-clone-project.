# AIRBNB-CLONE-PROJECT
## Team Roles 
### Backend Developer  
Responsible for implementing **API endpoints**, designing **database schemas**, and developing the **business logic** that powers the application. Works closely with the frontend team to ensure smooth data exchange and functionality.

### Database Administrator (DBA)  
Manages **database design**, **indexing**, and **query optimization**. Ensures data integrity, performance, and security while maintaining efficient storage structures.

### DevOps Engineer  
Handles **deployment**, **monitoring**, and **scaling** of backend services. Implements CI/CD pipelines, automates workflows, and ensures system reliability in production environments.

### QA Engineer  
Ensures backend functionalities are thoroughly **tested** and meet **quality standards**. Develops and runs test cases, detects bugs, and collaborates with developers to deliver stable, high-quality releases.



##  Technology Stack

###  Django  
A **high-level Python web framework** used for building the RESTful API and managing server-side logic. It provides a secure and scalable foundation for backend development.

### Django REST Framework (DRF)  
Provides a powerful and flexible toolkit for **creating and managing RESTful APIs**. It simplifies serialization, authentication, and permission handling, making API development faster and more consistent.

###  PostgreSQL  
A **robust relational database system** used for reliable data storage and complex querying. It supports scalability, data integrity, and advanced features like indexing and stored procedures.

###  GraphQL  
Enables **flexible and efficient data querying**, allowing clients to request exactly the data they need. This improves performance and reduces unnecessary API calls.

###  Celery  
Handles **asynchronous tasks** such as sending notifications, processing background jobs, or managing scheduled tasks. Improves system performance by offloading long-running operations.

###  Redis  
Used for **caching** and **session management** to enhance performance. It stores frequently accessed data in memory for faster response times and smooth user experiences.

###  Docker  
A **containerization tool** that ensures consistent development and deployment environments. It packages the application and its dependencies, eliminating compatibility issues across systems.

### CI/CD Pipelines  
Implements **automated testing and deployment pipelines**, enabling continuous integration and delivery. Ensures code changes are tested, validated, and deployed efficiently with minimal downtime.



---

## Database Design

### Objective
Understand how the database will be structured and how different entities (tables) connect to each other.

---

### Users  
**Purpose:** Stores information about people who use the platform — both property owners and guests.  

**Key Fields:**  
- `id`: Unique identifier for each user  
- `name`: Full name of the user  
- `email`: Contact email address  
- `password`: Encrypted user password  
- `role`: Defines whether the user is an owner or a guest  

**Relationships:**  
- A **user** can own multiple **properties**.  
- A **user** can make multiple **bookings** and **reviews**.

---

### Properties  
**Purpose:** Represents the listings or accommodations available for booking.  

**Key Fields:**  
- `id`: Unique identifier for each property  
- `owner_id`: The user who owns the property  
- `title`: Property name or title  
- `description`: Short summary of the property  
- `price_per_night`: Cost per night  

**Relationships:**  
- Each **property** belongs to one **user** (the owner).  
- A **property** can have many **bookings** and **reviews**.

---

### Bookings  
**Purpose:** Tracks reservations made by users for specific properties.  

**Key Fields:**  
- `id`: Unique booking identifier  
- `user_id`: The guest who made the booking  
- `property_id`: The property being booked  
- `check_in`: Start date of the booking  
- `check_out`: End date of the booking  

**Relationships:**  
- A **booking** belongs to a **user** (the guest).  
- A **booking** also belongs to a **property**.  
- Each **booking** can have one related **payment** record.

---

### Reviews  
**Purpose:** Stores feedback and ratings from guests who stayed at a property.  

**Key Fields:**  
- `id`: Unique review identifier  
- `user_id`: The guest who wrote the review  
- `property_id`: The property being reviewed  
- `rating`: Numerical score (e.g., 1–5)  
- `comment`: Written feedback  

**Relationships:**  
- A **review** belongs to one **user** and one **property**.  
- A **property** can have multiple **reviews**.

---

### Payments  
**Purpose:** Records all payment transactions made for bookings.  

**Key Fields:**  
- `id`: Unique payment identifier  
- `booking_id`: The booking being paid for  
- `amount`: Total amount paid  
- `payment_method`: Type of payment (e.g., card, PayPal)  
- `status`: Whether the payment is completed, pending, or failed  

**Relationships:**  
- Each **payment** belongs to one **booking**.  
- A **booking** can have one **payment** record.

---

### Entity Relationships Summary  
- A **User** can own many **Properties**.  
- A **User** can make many **Bookings**.  
- A **Property** can have many **Bookings** and **Reviews**.  
- Each **Booking** belongs to one **Property** and one **User**.  
- Each **Payment** is linked to one **Booking**.  
- Each **Review** is written by a **User** about a **Property**.

