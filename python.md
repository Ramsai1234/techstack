## python git hub resourses

https://github.com/krishnaik06/Complete-Python-Bootcamp.git

Top 50 Python Interview Questions & Answers 
Section A: Python Basics (Q1–Q12)

1. What are the key features of Python? Python is interpreted, dynamically typed, object-oriented, and has automatic memory management. It has a large standard library, supports multiple paradigms (procedural, OOP, functional), and emphasizes readability through simple, clean syntax.

2. What is the difference between a list, tuple, set, and dictionary? A list is mutable and ordered, allowing duplicates. A tuple is immutable and ordered, also allowing duplicates. A set is mutable, unordered, and stores only unique elements. A dictionary stores key-value pairs, is mutable, and (since Python 3.7) maintains insertion order.

3. What is the difference between is and ==? == checks value equality (whether two objects have the same content), while is checks identity (whether two references point to the exact same object in memory). For example, two separate lists with the same elements are == but not is.

4. What are mutable and immutable data types in Python? Mutable objects (list, dict, set) can be changed after creation without changing their identity. Immutable objects (int, float, str, tuple, frozenset) cannot be altered once created — any "modification" creates a new object.

5. What is the difference between deepcopy and copy? copy.copy() creates a shallow copy — it duplicates the outer object but nested objects are still shared by reference. copy.deepcopy() recursively copies all nested objects, producing a completely independent structure.

6. Explain Python's dynamic typing. Variables in Python don't have a fixed type; the type is determined at runtime based on the assigned value, and a variable can be reassigned to a different type later. This differs from statically typed languages like Java or C++.

7. What is the difference between range() and xrange()? This distinction applies to Python 2 — range() returned a list, while xrange() returned a lazy iterator. In Python 3, range() behaves like the old xrange(), returning a memory-efficient range object rather than a full list.

8. What are Python namespaces and scope (LEGB rule)? A namespace maps names to objects. Python resolves variable names using the LEGB rule: Local → Enclosing → Global → Built-in, searching in that order to determine which variable a name refers to.

9. What is the difference between .py and .pyc files? A .py file contains human-readable Python source code. A .pyc file contains compiled bytecode generated automatically by the interpreter to speed up subsequent imports of the same module.

10. What is PEP 8, and why does it matter? PEP 8 is Python's official style guide, covering naming conventions, indentation, line length, and code layout. Following it improves code readability and consistency, especially important in team environments and code reviews.

11. What is the difference between append() and extend() in lists? append() adds a single element (even if it's a list) as one item at the end. extend() iterates over an iterable and adds each of its elements individually to the list.

12. Explain Python's pass, break, and continue statements. pass is a null operation used as a placeholder where syntax requires a statement. break exits a loop entirely. continue skips the current iteration and moves to the next one in the loop.

Section B: Functions, OOP & Advanced Concepts (Q13–Q26)

13. What is the difference between a function and a method? A function is a standalone block of reusable code defined independently. A method is a function that's associated with an object/class and is called on an instance (e.g., my_list.append()), implicitly receiving the object as its first argument.

14. What are *args and **kwargs? *args allows a function to accept any number of positional arguments as a tuple. **kwargs allows it to accept any number of keyword arguments as a dictionary — both are useful for writing flexible, generic functions.

15. What are lambda functions, and when would you use one? A lambda is a small, anonymous, single-expression function defined using the lambda keyword, typically used for short throwaway operations like a custom sort key: sorted(data, key=lambda x: x[1]).

16. Explain the four pillars of OOP in Python. Encapsulation (bundling data and methods, restricting direct access via naming conventions), Abstraction (hiding internal implementation details), Inheritance (a class deriving properties from a parent class), and Polymorphism (the same interface behaving differently based on the object, e.g., method overriding).

17. What is the difference between __init__ and __new__? __new__ is a static method responsible for creating and returning a new instance of a class (allocating memory), while __init__ initializes that already-created instance with values. __new__ runs before __init__.

18. What is method overriding vs method overloading in Python? Method overriding occurs when a subclass redefines a method from its parent class with the same name and signature. Python doesn't natively support method overloading (multiple methods with the same name but different parameters) — it can be mimicked using default arguments or *args.

19. What are class variables vs instance variables? Class variables are shared across all instances of a class and defined directly inside the class body. Instance variables are unique to each object and typically defined inside __init__ using self.

20. What is multiple inheritance, and how does Python resolve conflicts (MRO)? Multiple inheritance allows a class to inherit from more than one parent class. Python resolves method resolution order (MRO) conflicts using the C3 linearization algorithm, which can be inspected via ClassName.__mro__.

21. What are decorators in Python? A decorator is a function that wraps another function or method to extend or modify its behavior without changing its actual code, commonly used for logging, access control, timing, or caching (@functools.lru_cache).

22. What are generators, and how do they differ from normal functions? A generator uses yield instead of return to produce a sequence of values lazily, one at a time, pausing its state between calls. This makes generators memory-efficient for processing large or infinite sequences, unlike normal functions that compute and return everything at once.

23. What is a Python iterator, and how is it different from an iterable? An iterable is any object capable of returning an iterator (implements __iter__), such as a list. An iterator is the object that actually produces values one at a time using __next__() and maintains state about where it is in the sequence.

24. What are context managers, and what does the with statement do? A context manager handles setup and teardown logic automatically (like opening/closing a file or a database connection) by implementing __enter__ and __exit__. The with statement ensures resources are properly released even if an exception occurs.

25. What is the difference between @staticmethod and @classmethod? A @staticmethod doesn't receive an implicit first argument and behaves like a regular function grouped inside a class. A @classmethod receives the class itself (cls) as its first argument and can access or modify class-level state.

26. What are Python magic/dunder methods? Give an example. Magic methods (like __init__, __str__, __len__, __eq__) let you define how objects behave with built-in operations. For example, overriding __str__ controls what's printed when you call print(obj).

Section C: Data Structures & Algorithms Basics (Q27–Q34)

27. How do you reverse a string in Python? The simplest way is slicing: my_string[::-1], which creates a new string traversing from the end to the start.

28. How would you check if a string is a palindrome? Compare the string to its reverse: s == s[::-1]. If they match, it's a palindrome.

29. What is the time complexity of common list operations (append, insert, search)? append() is O(1) amortized. insert() at an arbitrary position is O(n) since elements need to shift. Searching for an element with in is O(n) since it may scan the whole list. Indexing (list[i]) is O(1).

30. What is the difference between a stack and a queue, and how would you implement them in Python? A stack is LIFO (Last In, First Out) — implementable using a list with append()/pop(). A queue is FIFO (First In, First Out) — best implemented using collections.deque with append()/popleft() for O(1) operations on both ends.

31. How do you remove duplicates from a list while preserving order? Using dict.fromkeys(my_list) (Python 3.7+ preserves insertion order) and converting back to a list: list(dict.fromkeys(my_list)). A simple set() would remove duplicates but not preserve order.

32. How would you find the most frequent element in a list? Use collections.Counter(my_list).most_common(1), which counts occurrences of each element and returns the most frequent one efficiently.

33. What is a hash table, and how does Python's dictionary use it internally? A hash table stores key-value pairs using a hash function to compute an index for fast lookup, insertion, and deletion — typically O(1) average time. Python's dict is implemented as a hash table, which is why dictionary lookups are so fast.

34. How would you find duplicate elements in a list efficiently? Iterate through the list while tracking seen elements in a set; if an element is already in the set, it's a duplicate. This gives O(n) time complexity compared to a nested-loop O(n²) approach.

Section D: Error Handling, File I/O & Modules (Q35–Q41)

35. How does exception handling work in Python? Using try to wrap risky code, except to catch and handle specific exceptions, else to run code if no exception occurred, and finally to run cleanup code regardless of whether an exception was raised.

36. What is the difference between Exception and BaseException? BaseException is the root of Python's exception hierarchy, including system-exiting exceptions like SystemExit and KeyboardInterrupt. Exception is a subclass of BaseException and is the base for almost all user-defined and standard exceptions that should typically be caught.

37. How do you create a custom exception in Python? By defining a new class that inherits from Exception (or a more specific built-in exception), optionally overriding __init__ to add custom attributes or messages, then raising it with raise MyCustomError("message").

38. How do you read and write files in Python safely? Using the with open(filename, mode) as f: syntax, which automatically closes the file even if an error occurs during reading/writing, avoiding resource leaks compared to manually calling open() and close().

39. What is the difference between import module and from module import function? import module imports the whole module, requiring you to prefix calls with module.function(). from module import function imports a specific function directly into the current namespace, letting you call it as function() without the prefix.

40. What is __name__ == "__main__" used for? It checks whether a script is being run directly or imported as a module. Code inside this block only executes when the file is run directly, not when it's imported elsewhere — useful for including test code or entry points in reusable modules.

41. What are Python virtual environments, and why are they used? A virtual environment (venv or conda env) creates an isolated Python installation with its own dependencies, preventing version conflicts between different projects that may require different package versions.

Section E: Concurrency, Testing & Practical Topics (Q42–Q50)

42. What is the GIL (Global Interpreter Lock)? The GIL ensures only one thread executes Python bytecode at a time in CPython, which limits true parallel execution of CPU-bound threads. For CPU-bound tasks, multiprocessing is preferred; for I/O-bound tasks (like network calls), threading or asyncio still provide benefits since the GIL is released during I/O waits.

43. What is the difference between multithreading and multiprocessing? Multithreading runs multiple threads within a single process sharing memory space, best suited for I/O-bound tasks. Multiprocessing runs separate processes each with their own memory space, bypassing the GIL, making it better suited for CPU-bound tasks that need true parallelism.

44. What is asyncio, and when would you use it? asyncio enables asynchronous, non-blocking programming using async/await syntax, allowing a single thread to handle many I/O-bound operations concurrently (like multiple API calls) without waiting for each one to finish sequentially.

45. How do you write and run unit tests in Python? Using the built-in unittest module (or the more popular third-party pytest), you write test functions/classes that assert expected outcomes, e.g., assert result == expected_value, and run them via a test runner to automatically verify code correctness.

46. What is mocking, and why is it used in tests? Mocking replaces real objects or external dependencies (like a database or API call) with fake, controllable substitutes during testing, using libraries like unittest.mock, so tests run reliably and quickly without needing the real dependency.

47. What is the difference between == and .equals()-style comparison for custom objects? Python doesn't have .equals() — by default, == compares object identity for custom classes unless you override the __eq__ method to define what equality means for your object (e.g., comparing specific attributes).

48. How would you connect Python to a database and execute a query? Using a database driver/library appropriate to the database (e.g., sqlite3, psycopg2 for PostgreSQL, or an ORM like SQLAlchemy), you open a connection, create a cursor, execute SQL queries via parameterized statements (to prevent SQL injection), and commit/close the connection properly.

49. What is a REST API, and how would you build one in Python? A REST API exposes application functionality over HTTP using standard methods (GET, POST, PUT, DELETE) and typically JSON payloads. In Python, frameworks like Flask or FastAPI let you define routes/endpoints that map to functions handling requests and returning responses.

50. How do you optimize slow Python code? Common strategies: profile first (cProfile, timeit) to find actual bottlenecks, use built-in functions and vectorized operations (NumPy) instead of manual loops, use appropriate data structures (e.g., sets for membership checks), cache repeated computations (functools.lru_cache), and consider multiprocessing or C extensions for CPU-heavy work.
