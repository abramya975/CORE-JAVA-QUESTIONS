# Java I/O Interview Questions
 
A curated list of essential Java I/O questions and concepts.
 
### 1. What is Java I/O and what are its core packages?
Java I/O (Input/Output) allows programs to read data from a source and write data to a destination. Common data sources and destinations include files, network connections, memory, and console input/output. The core packages used are `java.io`, `java.nio`, and `java.nio.file`.
 
### 2. What is a Stream, and what is the difference between an `InputStream` and an `OutputStream`?
A stream is a flow or sequence of data between a source and a destination. An `InputStream` is used to read data (meaning data flows into the program), while an `OutputStream` is used to write data (meaning data flows out of the program).
 
### 3. What is the difference between Byte Streams and Character Streams?
* **Byte Streams:** These handle raw binary data, work with 8-bit data, and use `InputStream` and `OutputStream` as base classes. They are used for images, audio, and video files.
* **Character Streams:** These handle text data, work with 16-bit Unicode characters, and use `Reader` and `Writer` as base classes. They are specifically used for text files.
 
### 4. Are `InputStream` and `OutputStream` interfaces?
No, `InputStream` and `OutputStream` are abstract classes, not interfaces. They define the basic API for reading and writing byte streams, while concrete subclasses (like `FileInputStream` and `BufferedInputStream`) extend them to provide the actual implementation.
 
### 5. Why are Buffered Streams used instead of standard streams?
Buffered streams improve performance by reading or writing large chunks of data at once instead of processing one byte or character at a time. This approach significantly reduces the number of expensive, slow disk access operations.

**Without buffering:**
- a program reads or writes one byte or character at a time, *causing frequent and expensive `system calls`*.

**With buffering:**
- A large block of data is read from the source into memory.
- The program then processes the data from the buffer.
This makes file operations much faster and more efficient.
 
### 6. What is Serialization and what role does the `Serializable` interface play?
Serialization is the process of converting a Java object into a byte stream so its state can be saved to a file, stored in memory, or transmitted over a network. The `Serializable` interface is a marker interface that indicates to the JVM that a class's objects are eligible to be converted into a byte stream. It does not contain any methods.
 
### 7. What is the `transient` keyword used for in Java serialization?
The `transient` keyword indicates that a specific field should not be serialized when the object is converted into a byte stream. It is typically used for sensitive data, like passwords, or temporary data that shouldn't be stored. When the object is deserialized, the transient field will revert to its default value (e.g., `null` for Objects, `0` for `int`).
 
### 8. Does JPA/Hibernate use Java Serialization to store objects in a database?
No, JPA and Hibernate do not use Java Serialization to store objects in a database. Instead, they use `Object Relational Mapping (ORM)` to convert Java objects into SQL statements that map to relational database tables. Serialization is primarily used for object persistence in files, caching, or network transfers.
 
### 9. What is `try-with-resources` and why is it preferred for I/O operations?
Introduced in Java 7, `try-with-resources` automatically closes resources (like files or database connections) after they are used. This eliminates the need to manually close resources in a `finally` block. It requires the resource to implement the `AutoCloseable` interface.
 
### 10. How does Java NIO differ from traditional Java I/O?
Java NIO (New Input/Output) is a modern, high-performance API that is buffer-based, whereas traditional Java I/O is stream-based. NIO supports non-blocking operations and allows a single thread to manage multiple channels via Selectors. Traditional I/O relies on blocking operations where each connection may require a separate thread.