# 0x01. NoSQL

This project focuses on interacting with MongoDB using both command-line scripts and Python functions. The tasks involve creating, reading, updating, and deleting documents, as well as managing databases and collections.

## Tasks :page_with_curl:

* **0. List all databases**
  * [0-list_databases](./0-list_databases): Script to list all databases in MongoDB.
  * Usage: `mongo < 0-list_databases`
  * Annotations: `show dbs;`

* **1. Create a database**
  * [1-use_or_create_database](./1-use_or_create_database): Script to create or switch to the database `my_db`.
  * Usage: `mongo < 1-use_or_create_database`
  * Annotations: `use my_db;`

* **2. Insert document**
  * [2-insert](./2-insert): Script to insert a document into the `school` collection with the attribute `name` set to "Holberton school".
  * Usage: `mongo my_db < 2-insert`
  * Annotations: `db.school.insert({ name: "Holberton school" });`

* **3. All documents**
  * [3-all](./3-all): Script to list all documents in the `school` collection.
  * Usage: `mongo my_db < 3-all`
  * Annotations: `db.school.find();`

* **4. All matches**
  * [4-match](./4-match): Script to list all documents in the `school` collection where `name="Holberton school"`.
  * Usage: `mongo my_db < 4-match`
  * Annotations: `db.school.find({ name: "Holberton school" });`

* **5. Count**
  * [5-count](./5-count): Script to count the number of documents in the `school` collection.
  * Usage: `mongo my_db < 5-count`
  * Annotations: `db.school.countDocuments();`

* **6. Update**
  * [6-update](./6-update): Script to add a new attribute `address` with the value “972 Mission street” to all documents with `name="Holberton school"` in the `school` collection.
  * Usage: `mongo my_db < 6-update`
  * Annotations: `db.school.updateMany({ name: "Holberton school" }, { $set: { address: "972 Mission street" } });`

* **7. Delete by match**
  * [7-delete](./7-delete): Script to delete all documents with `name="Holberton school"` in the `school` collection.
  * Usage: `mongo my_db < 7-delete`
  * Annotations: `db.school.deleteMany({ name: "Holberton school" });`

* **8. List all documents in Python**
  * [8-all.py](./8-all.py): Python function to list all documents in a collection.
  * Usage: `python3 8-main.py`
  * Annotations: `def list_all(mongo_collection): return list(mongo_collection.find());`

* **9. Insert a document in Python**
  * [9-insert_school.py](./9-insert_school.py): Python function to insert a new document into a collection based on kwargs.
  * Usage: `python3 9-main.py`
  * Annotations: `def insert_school(mongo_collection, **kwargs): return mongo_collection.insert_one(kwargs).inserted_id;`

* **10. Change school topics**
  * [10-update_topics.py](./10-update_topics.py): Python function to change all topics of a school document based on the `name`.
  * Usage: `python3 10-main.py`
  * Annotations: `def update_topics(mongo_collection, name, topics): return mongo_collection.update_many({"name": name}, {"$set": {"topics": topics}});`

* **11. Where can I learn Python?**
  * [11-schools_by_topic.py](./11-schools_by_topic.py): Python function that returns the list of school documents with a specific topic.
  * Usage: `python3 11-main.py`
  * Annotations: `def schools_by_topic(mongo_collection, topic): return mongo_collection.find({"topics": topic});`

* **12. Log stats**
  * [12-log_stats.py](./12-log_stats.py): Python script that provides some statistics about Nginx logs stored in MongoDB.
  * Usage: `python3 12-log_stats.py`
  * Annotations: `print the total number of logs and counts for each HTTP method.`

* **13. Regex filter**
  * [100-find](./100-find): Script to list all documents with names starting with "Holberton" in the `school` collection.
  * Usage: `mongo my_db < 100-find`
  * Annotations: `db.school.find({ name: /^Holberton/ });`

* **14. Top students**
  * [101-students.py](./101-students.py): Python function to return all students sorted by average score.
  * Usage: `python3 101-main.py`
  * Annotations: `def top_students(mongo_collection): return mongo_collection.aggregate([...]);`

* **15. Log stats - new version**
  * [102-log_stats.py](./102-log_stats.py): Improved version of the `12-log_stats.py` script, including the top 10 most present IPs in the `nginx` collection.
  * Usage: `python3 102-log_stats.py`
  * Annotations: `Prints top 10 most present IPs in logs.`
