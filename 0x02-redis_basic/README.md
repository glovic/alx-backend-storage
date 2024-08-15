# 0x02. Redis Basic

This project explores the basics of working with Redis, focusing on how to use Redis for storing, retrieving, and manipulating data with Python.

## Tasks :page_with_curl:

* **0. Writing strings to Redis**
  * **[exercise.py](./exercise.py):** In this task, we create a `Cache` class that interacts with Redis to store arbitrary data types. The `store` method generates a random key and stores the input data under that key.
  * **Usage:**
    ```python
    cache = Cache()
    data = b"hello"
    key = cache.store(data)
    print(key)
    print(cache._redis.get(key))
    ```
    **Output:**
    ```python
    b'hello'
    ```

* **1. Reading from Redis and recovering original type**
  * **[exercise.py](./exercise.py):** We implement the `get` method in the `Cache` class that retrieves data from Redis and converts it back to its original type using a Callable. Additionally, we create `get_str` and `get_int` methods for automatic conversion.
  * **Usage:**
    ```python
    cache = Cache()
    key = cache.store("foo")
    print(cache.get(key, fn=lambda d: d.decode('utf-8')))
    ```
    **Output:**
    ```python
    'foo'
    ```

* **2. Incrementing values**
  * **[exercise.py](./exercise.py):** This task introduces a `count_calls` decorator that tracks the number of times a method in the `Cache` class is called. The count is stored in Redis under the method's qualified name.
  * **Usage:**
    ```python
    cache = Cache()
    cache.store(b"first")
    print(cache.get(cache.store.__qualname__))
    ```
    **Output:**
    ```python
    b'1'
    ```

* **3. Storing lists**
  * **[exercise.py](./exercise.py):** We implement the `call_history` decorator that records the history of input parameters and outputs for a method in the `Cache` class. These histories are stored as lists in Redis.
  * **Usage:**
    ```python
    cache = Cache()
    key = cache.store("foo")
    inputs = cache._redis.lrange(f"{cache.store.__qualname__}:inputs", 0, -1)
    outputs = cache._redis.lrange(f"{cache.store.__qualname__}:outputs", 0, -1)
    print(inputs, outputs)
    ```
    **Output:**
    ```python
    [b"('foo',)"] [b'key']
    ```

* **4. Retrieving lists**
  * **[exercise.py](./exercise.py):** We create a `replay` function that retrieves and displays the history of calls to a particular function using the keys generated in the previous task.
  * **Usage:**
    ```python
    cache = Cache()
    cache.store("foo")
    cache.store("bar")
    cache.store(42)
    replay(cache.store)
    ```
    **Output:**
    ```python
    Cache.store was called 3 times:
    Cache.store(*('foo',)) -> key1
    Cache.store(*('bar',)) -> key2
    Cache.store(*(42,)) -> key3
    ```

* **5. Implementing an expiring web cache and tracker**
  * **[web.py](./web.py):** In this advanced task, we implement a `get_page` function that fetches HTML content from a URL, tracks the number of accesses to the URL, and caches the result for 10 seconds.
  * **Usage:**
    ```python
    html_content = get_page("http://example.com")
    print(html_content)
    ```
    **Output:**
    ```
    HTML content of the page with caching applied
    ```
  * **Bonus:**
    The `get_page` function can be enhanced with decorators for tracking and caching.
