# SQLwk8Final-project
week 8 plp final project assignment
📦 E-commerce Store Database (MySQL)
📌 Overview

This project implements a full-featured relational database for an online e-commerce store (similar to an online jersey shop).
The database is designed to manage users, products, categories, orders, payments, and shipping addresses with proper constraints and relationships.

🛠 Features

✅ Users can register and place orders.

✅ Products are organized into categories.

✅ Orders can contain multiple products (many-to-many).

✅ Payments are linked one-to-one with orders.

✅ Addresses store customer shipping and billing details.

✅ Proper constraints:

PRIMARY KEY, FOREIGN KEY, NOT NULL, UNIQUE

Cascade updates/deletes where appropriate.

📂 Schema Overview

Entities & Relationships:

Users → (1-to-Many) → Orders

Categories → (1-to-Many) → Products

Orders ↔ (Many-to-Many) ↔ Products (via Order_Items)

Orders → (1-to-1) → Payments

Users → (1-to-Many) → Addresses

📜 Files

ecommerce_store.sql → contains:

CREATE DATABASE

CREATE TABLE statements

Constraints and relationships

🚀 How to Run

Open MySQL CLI or a tool like phpMyAdmin / MySQL Workbench.

Run the SQL script:

mysql -u your_username -p < ecommerce_store.sql


Verify database:

SHOW DATABASES;
USE ecommerce_store;
SHOW TABLES;

📊 Example Queries
-- Get all products in stock
SELECT name, price, stock FROM Products WHERE stock > 0;

-- Find orders by a specific user
SELECT order_id, status, order_date
FROM Orders
WHERE user_id = 1;

-- Get order details with products
SELECT o.order_id, p.name, oi.quantity, oi.price
FROM Order_Items oi
JOIN Orders o ON oi.order_id = o.order_id
JOIN Products p ON oi.product_id = p.product_id
WHERE o.order_id = 1;

✅ Next Steps

Add sample data (INSERT statements) for testing.

Create views for reports (e.g., monthly sales).

Add stored procedures for business logic (e.g., auto-update stock).
