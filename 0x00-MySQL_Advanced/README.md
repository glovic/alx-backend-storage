## 0x03. SQL Basics

This project covers basic SQL operations including table creation, indexing, and query optimization. The tasks involve creating tables and applying different SQL techniques.

## Tasks :page_with_curl:

* **0. SQL Basics**
  * [0-sql_basics.sql](./0-sql_basics.sql): SQL script to create a `users` table with columns for `id`, `email`, and `name`.
  * Usage: `mysql -uroot -p < 0-sql_basics.sql`
  * Annotations: `CREATE TABLE users (id INT AUTO_INCREMENT PRIMARY KEY, email VARCHAR(255) NOT NULL UNIQUE, name VARCHAR(255));`

* **1. SQL Advanced**
  * [1-sql_advanced.sql](./1-sql_advanced.sql): SQL script to create an `orders` table with columns for `order_id`, `user_id`, `amount`, and `date`.
  * Usage: `mysql -uroot -p < 1-sql_advanced.sql`
  * Annotations: `CREATE TABLE orders (order_id INT AUTO_INCREMENT PRIMARY KEY, user_id INT, amount DECIMAL(10,2), date DATE);`

* **2. SQL Indexing**
  * [2-sql_indexing.sql](./2-sql_indexing.sql): SQL script to create an index on the `email` column of the `users` table.
  * Usage: `mysql -uroot -p < 2-sql_indexing.sql`
  * Annotations: `CREATE INDEX idx_email ON users(email);`

* **3. SQL Triggers**
  * [3-sql_triggers.sql](./3-sql_triggers.sql): SQL script to create a trigger that updates the `updated_at` column before updating rows in the `orders` table.
  * Usage: `mysql -uroot -p < 3-sql_triggers.sql`
  * Annotations: `CREATE TRIGGER update_timestamp BEFORE UPDATE ON orders FOR EACH ROW SET NEW.updated_at = NOW();`

* **4. SQL Stored Procedures**
  * [4-sql_stored_procedures.sql](./4-sql_stored_procedures.sql): SQL script to create a stored procedure that retrieves all orders for a given user.
  * Usage: `mysql -uroot -p < 4-sql_stored_procedures.sql`
  * Annotations: `CREATE PROCEDURE get_user_orders(IN user_id INT) BEGIN SELECT * FROM orders WHERE user_id = user_id; END;`

* **5. SQL Views**
  * [5-sql_views.sql](./5-sql_views.sql): SQL script to create a view showing the total amount of orders for each user.
  * Usage: `mysql -uroot -p < 5-sql_views.sql`
  * Annotations: `CREATE VIEW user_order_totals AS SELECT user_id, SUM(amount) AS total_amount FROM orders GROUP BY user_id;`

* **6. SQL Aggregation**
  * [6-sql_aggregation.sql](./6-sql_aggregation.sql): SQL script to find the average order amount for each user.
  * Usage: `mysql -uroot -p < 6-sql_aggregation.sql`
  * Annotations: `SELECT user_id, AVG(amount) AS average_amount FROM orders GROUP BY user_id;`
