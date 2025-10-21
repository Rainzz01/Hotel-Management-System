# Hotel Management System

## Overview

This Hotel Management System (HMS) is a web-based application developed as a group mini-project for Universiti Tunku Abdul Rahman (UTAR) course UCCA2513. It aims to streamline hotel operations by integrating four key modules: Guest Module, Staff Module, Rooms & Maintenance Module, and Inventory Module. The system addresses inefficiencies in existing hotel management solutions through automation, real-time updates, advanced analytics, and role-based access control.

The project focuses on improving operational efficiency, guest satisfaction, and resource management. It supports features like personalized guest experiences, dynamic staff scheduling, preventive maintenance, and proactive inventory alerts. Built on a centralized framework, it enables seamless inter-departmental coordination and data-driven decision-making.

## Features

The system includes:

- **Guest Module**:
  - Guest registration, profile management (view/edit), and uploads (e.g., profile images).
  - Room booking, viewing bookings, check-in/check-out.
  - Loyalty program tracking, rewards management (create, edit, delete).
  - API endpoints for fetching guest info, loyalty details, rewards, and rooms by type.
  - Guest reports (e.g., occupancy trends, preferences).

- **Staff Module**:
  - Staff authentication, login/logout.
  - Role-based dashboards (Admin, HR, Normal Staff, etc.).
  - Staff management: CRUD operations for staff records, shifts, and performance ratings.
  - Viewing staff by types (e.g., HA staff, M staff, N staff).
  - Shift management: Create, update, delete, view, and status updates.
  - Staff reports.

- **Rooms & Maintenance (R&M) Module**:
  - Dashboards for maintenance overview and reports.
  - Maintenance requests: Create (regular/emergency), view, update, delete.
  - Maintenance tasks: Create (regular/emergency), view, update status.
  - Room management: View rooms, update status (e.g., available, occupied, maintenance).
  - Integration with inventory for automatic deductions based on room activity.

- **Inventory Module**:
  - Dashboards for inventory, assignments, and orders.
  - Inventory management: Add, update, delete, view items; select/add/update decisions.
  - Assign inventory to rooms: View, update, delete assignments.
  - Order management: Add, update, cancel, view orders; order-inventory associations.
  - Real-time alerts for low stock levels.
  - Inventory reports (e.g., usage over time periods).

- **General**:
  - Role-based access control (e.g., HR for staff, Managers for modules).
  - Real-time notifications and analytics.
  - Integration across modules (e.g., inventory auto-deduct on room status change, emergency requests from guest module).
  - User-friendly interface with CSS styling and JavaScript for frontend logic (e.g., dynamic forms, error handling).

## Innovations

- **Staff Module**: Dynamic scheduling automating tasks based on occupancy and workload.
- **Guest Module**: Enhanced reporting tools for customizable insights on preferences and loyalty.
- **Maintenance Module**: Automated preventive maintenance scheduling based on room usage.
- **Inventory Module**: Real-time customizable notifications for stock thresholds.

## Project Objectives

1. Investigate limitations of current hotel management systems.
2. Design a centralized, role-based framework for integration.
3. Develop an automated, user-friendly system with analytics and notifications.

## Tech Stack

From the project report and code review:

- **Backend**: PHP (for server-side logic, CRUD operations, API endpoints, and form handlers).
- **Database**: MySQL (for storing entities like guests, rooms, inventory, staff; connected via `database.php`).
- **Frontend**: HTML (embedded in PHP files), CSS (via `style.css` for styling), JavaScript (for dynamic elements like data display, read-only fields, error handling in modules like Guest).
- **Development Tools**: Visual Studio Code (IDE), XAMPP v3.3.0 (local server with Apache and MySQL).
- **Deployment OS**: Windows (tested environment).
- **Other**: No external frameworks (vanilla PHP); mysqli or similar for DB interactions; sessions for authentication.

The system is built on the LAMP stack (Apache, MySQL, PHP) via XAMPP, ensuring scalability, security, and ease of maintenance.

## Database Schema

The Entity-Relationship Diagram (ERD) defines the database structure with the following key entities and relationships:

- **Guest Management**:
  - `Guest`: guest_id (PK), guest_name, guest_email, guest_phone, guest_address, record_date, gender.
  - `Loyalty_Program`: loyalty_id (PK), guest_id (FK), tier_level, points, total_book_days.

- **Rewards System**:
  - `Reward`: reward_id (PK), reward_name, description, points_required, discount_rate.
  - `Redemption_Record`: redemption_id (PK), guest_id (FK), reward_id (FK), redemption_date.

- **Inventory Management**:
  - `Inventory_Management`: inv_id (PK), inv_name, inv_price, inv_category, alert_level.
  - `Inventory_Assign`: assign_id (PK), inv_id (FK), room_type_id (FK), quantity.

- **Room Management**:
  - `Room_Type`: room_type_id (PK), type, features.
  - `Room`: room_id (PK), room_type_id (FK), room_status, room_space, room_num.

- **Stay Details**:
  - `Stay`: stay_id (PK), guest_id (FK), room_id (FK), staff_id (FK), check_in_date, check_out_date.

- **Order Management**:
  - `Order_Inventory`: order_id (PK), inv_id (FK), supplier_name, supplier_contact, order_date, quantity.

- **Maintenance Management**:
  - `Maintenance_Request`: req_id (PK), room_id (FK), req_date, priority_level, req_status.
  - `Maintenance_Task`: task_id (PK), req_id (FK), task_desc, completion_date.

- **Staff Management**:
  - `Staff`: staff_id (PK), staff_name, staff_email, staff_role_id (FK).
  - `Staff_Shift`: shift_id (PK), staff_id (FK), start_time, end_time.
  - `Staff_Performance`: perf_id (PK), staff_id (FK), perf_rating, perf_comment.
  - `Staff_Role`: role_id (PK), role_name, responsibilities.

**Relationships**:
- One-to-Many: Guest to Loyalty_Program/Stay/Redemption_Record.
- Many-to-Many: Via associative tables like Inventory_Assign, Redemption_Record.
- Foreign keys ensure data integrity across modules.

## Prerequisites

- XAMPP v3.3.0 or compatible (includes Apache 2.4.x, MySQL 8.x, PHP 8.x).
- Web browser for access.
- Windows OS (recommended for deployment, as tested).

## Installation

1. **Clone the Repository**:
- git clone https://github.com/Rainzz01/Hotel-Management-System.git
- cd Hotel-Management-System/hotel

2. **Set Up XAMPP**:
- Install XAMPP and start Apache and MySQL services.
- Create a MySQL database (e.g., `hotel_management`) via phpMyAdmin.
- Import or create tables based on the ERD above (no schema.sql provided; use SQL queries from ERD).

3. **Configure Database**:
- Update `database.php` with your MySQL credentials (host: localhost, user: root, password: '', db: hotel_management).

4. **Run the Application**:
- Place the project in XAMPP's `htdocs` folder (e.g., `htdocs/hotel`).
- Access via `http://localhost/hotel`.
- Login with staff credentials (role-based; defaults may be in DB or hardcoded—check `staff_login.php`).

## Usage

- **Login**: Authenticate via staff module; roles direct to specific dashboards.
- **Module Navigation**: Use dashboards to access CRUD, reports, and features.
- **Testing**: Black-box tested for CRUD, alerts, reports (all passed per report).
- For details, refer to flowcharts and block diagrams in the project report.

## Evaluation

Black-box testing was conducted on all modules, covering CRUD operations, alerts, reports, and role-based access. All tests passed, confirming functionality, data integrity, and expected behaviors. See project report for detailed results.

## Known Limitations & Future Improvements

- **Guest Module**: Cluttered reports; add filters (weekly/daily/monthly) and seamless booking post-registration.
- **Staff Module**: Inflexible scheduling; add dynamic update tools.
- **Maintenance Module**: No image uploads for issues; add photo attachment.
- **Inventory Module**: Limited filtering; add category/room-based filters and search.

## Contributing

Fork the repo, create a feature branch, commit changes, and submit a pull request. Follow PHP standards.

## License

Not specified; open-source for educational purposes.

## Contact

For issues, contact [Rainzz01](https://github.com/Rainzz01) or group members from the report.

---

*Developed by UTAR Group 3: Lee Yong Wei, Low Yee Tian, Jeremy Lim Yeu Shuo, Tan Wen Pang*
