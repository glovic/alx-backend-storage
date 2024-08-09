# Project Documentation

## 0x00. MySQL Advanced

This project focuses on advanced MySQL queries, including unique constraints, filtering, complex joins, and more. The tasks involve writing SQL scripts to perform various advanced operations on the database.

## Tasks :page_with_curl:

* **0. We are all unique!**
  * [0-uniq_users.sql](./0-uniq_users.sql): SQL script (`.sql`) to find unique users in the database, ensuring no duplicates based on a specified criterion.
  * Usage: `mysql -uroot -p < 0-uniq_users.sql`
  * Annotations: `SELECT DISTINCT column_name FROM table_name;`

* **1. In and not out**
  * [1-country_users.sql](./1-country_users.sql): SQL script (`.sql`) to filter users based on their country, showing those within a specific list and excluding others.
  * Usage: `mysql -uroot -p < 1-country_users.sql`
  * Annotations: `SELECT * FROM users WHERE country IN ('Country1', 'Country2') AND country NOT IN ('Country3');`

* **2. Best band ever!**
  * [2-fans.sql](./2-fans.sql): SQL script (`.sql`) to find all users who are fans of a specific band, using JOIN operations to connect relevant tables.
  * Usage: `mysql -uroot -p < 2-fans.sql`
  * Annotations: `SELECT users.name FROM users JOIN bands ON users.band_id = bands.id WHERE bands.name = 'BandName';`

* **3. Old school band**
  * [3-glam_rock.sql](./3-glam_rock.sql): SQL script (`.sql`) to retrieve users who are fans of old-school bands, focusing on a particular genre and era.
  * Usage: `mysql -uroot -p < 3-glam_rock.sql`
  * Annotations: `SELECT users.name FROM users JOIN bands ON users.band_id = bands.id WHERE bands.genre = 'Glam Rock' AND bands.year < 1980;`

* **4. Buy buy buy**
  * [4-store.sql](./4-store.sql): SQL script (`.sql`) to track purchases in a store, summarizing total sales per user and identifying top spenders.
  * Usage: `mysql -uroot -p < 4-store.sql`
  * Annotations: `SELECT users.name, SUM(orders.amount) AS total_spent FROM users JOIN orders ON users.id = orders.user_id GROUP BY users.name ORDER BY total_spent DESC;`

* **5. Email validation to sent**
  * [5-valid_email.sql](./5-valid_email.sql): SQL script (`.sql`) to validate email addresses of users and ensure that they meet a specific format or criterion.
  * Usage: `mysql -uroot -p < 5-valid_email.sql`
  * Annotations: `SELECT email FROM users WHERE email REGEXP '^[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Z|a-z]{2,}$';`

* **6. Add bonus**
  * [6-bonus.sql](./6-bonus.sql): SQL script (`.sql`) to calculate bonuses for employees based on their performance, adjusting their salaries accordingly.
  * Usage: `mysql -uroot -p < 6-bonus.sql`
  * Annotations: `UPDATE employees SET salary = salary + bonus WHERE performance_rating >= 4;`

* **7. Average score**
  * [7-compute_avg.sql](./7-compute_avg.sql): SQL script (`.sql`) to compute the average score or rating for a given dataset, such as user feedback or product reviews.
  * Usage: `mysql -uroot -p < 7-compute_avg.sql`
  * Annotations: `SELECT AVG(score) FROM reviews;`

* **8. Optimize database**
  * [8-indexing.sql](./8-indexing.sql): SQL script (`.sql`) to optimize the database by adding indexes to frequently queried columns.
  * Usage: `mysql -uroot -p < 8-indexing.sql`
  * Annotations: `CREATE INDEX idx_column_name ON table_name(column_name);`

* **9. Unique IDs**
  * [9-unique_ids.sql](./9-unique_ids.sql): SQL script (`.sql`) to ensure that all IDs in a table are unique and non-null.
  * Usage: `mysql -uroot -p < 9-unique_ids.sql`
  * Annotations: `ALTER TABLE table_name ADD UNIQUE(column_name);`

* **10. Relationships**
  * [10-relationships.sql](./10-relationships.sql): SQL script (`.sql`) to define relationships between different tables using foreign keys.
  * Usage: `mysql -uroot -p < 10-relationships.sql`
  * Annotations: `ALTER TABLE child_table ADD CONSTRAINT fk_name FOREIGN KEY (column_name) REFERENCES parent_table(column_name);`

