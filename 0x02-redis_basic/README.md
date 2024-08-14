# 0x02. Redis Basic

This project involves working with Redis to store, retrieve, and manipulate data using Python. The tasks focus on understanding basic Redis operations, decorators, and managing call histories.

## Tasks :page_with_curl:

* **0. Writing strings to Redis**
  * [exercise.py](./exercise.py): Implement a `Cache` class with methods to store data in Redis.
    * **store**: Generates a random key and stores data in Redis.
    * Usage:
      ```python
      from exercise import Cache
      cache = Cache()
      key = cache.store(b"hello")
      ```
    * Annotations:
      * Stores data of types `str`, `bytes`, `int`, `float` in Redis and returns the key.
      * Example: `local_redis.get(key) -> b'hello'`

* **1. Reading from Redis and recovering original type**
  * [exercise.py](./exercise.py): Implement methods to retrieve data from Redis and convert it to its original format.
    * **get**: Retrieves data using a key and optionally applies a function to convert it to the original type.
    * **get_str**: Retrieves and decodes a string from Redis.
    * **get_int**: Retrieves an integer from Redis.
    * Usage:
      ```python
      cache = Cache()
      cache.get(key, fn=lambda d: d.decode("utf-8"))
      ```
    * Annotations:
      * Utilizes Redis to store and retrieve various data types, ensuring type consistency.

* **2. Incrementing values**
  * [exercise.py](./exercise.py): Implement a decorator to count how many times methods are called.
    * **count_calls**: A decorator to count method calls.
    * Usage:
      ```python
      cache.store(b"first")
      cache.get(cache.store.__qualname__)  # -> b'1'
      ```
    * Annotations:
      * Uses the Redis `INCR` command to keep track of method calls.

* **3. Storing lists**
  * [exercise.py](./exercise.py): Implement a decorator to store the history of inputs and outputs for a function.
    * **call_history**: A decorator to store input and output history.
    * Usage:
      ```python
      cache.store("first")
      inputs = cache._redis.lrange("Cache.store:inputs", 0, -1)
      outputs = cache._redis.lrange("Cache.store:outputs", 0, -1)
      ```
    * Annotations:
      * Stores inputs and outputs of method calls as lists in Redis.

* **4. Retrieving lists**
  * [exercise.py](./exercise.py): Implement a function to display the history of calls for a function.
    * **replay**: Displays the call history for a decorated function.
    * Usage:
      ```python
      cache.store("foo")
      replay(cache.store)
      ```
    * Annotations:
      * Uses Redis to retrieve and display the input and output history of method calls.
      * Example Output:
        ```
        Cache.store was called 3 times:
        Cache.store(*('foo',)) -> some-uuid
        Cache.store(*('bar',)) -> some-uuid
        Cache.store(*(42,)) -> some-uuid
        ```

* **5. Implementing an expiring web cache and tracker**
  * [web.py](./web.py): Python function `get_page` that fetches the HTML content of a given URL, tracks how many times the URL is accessed, and caches the result with an expiration time of 10 seconds.
  * Usage: `python3 web.py`
  * Annotations: `def get_page(url: str) -> str: Uses the requests module to get HTML content, tracks access count, and caches with a 10-second expiry.`
"""
