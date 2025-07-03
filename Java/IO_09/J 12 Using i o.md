
## Chapter 10 : Using I/O


Key Skills & Concepts
●Understand the stream
●Know the difference between byte and character streams
●Know Java’s byte stream classes
●Know Java’s character stream classes
●Know the predefined streams
●Use byte streams
●Use byte streams for file I/O
●Automatically close a file by using try-with-resources
●Read and write binary data
●Use random-access files
●Use character streams
●Use character streams for file I/O
●Apply Java’s type wrappers to convert numeric strings


Java’s I/O system is quite large, containing many classes, interfaces, and methods. Part of the reason for its size is that Java defines two complete I/O systems: one for
byte I/O and the other for character I/O. It won’t be possible to discuss every aspect of Java’s
I/O here.

Java’s
I/O system is cohesive and consistent; once you understand its fundamentals, the rest of the
I/O system is easy to master.

___


Java programs perform I/O through streams. An I/O stream is an abstraction that either produces
or consumes information. A stream is linked to a physical device by the Java I/O system.
All streams behave in the same manner, even if the actual physical devices they are linked to
differ. Thus, the same I/O classes and methods can be applied to different types of devices.

Java implements I/O streams within class hierarchies defined in the java.io package.


#### Byte Streams and Character Streams

Modern versions of Java define two types of I/O streams: byte and character.

Byte streams provide a convenient means for handling input and output of bytes. They are
used, for example, when reading or writing binary data. They are especially helpful when
working with files. Character streams are designed for handling the input and output of
characters. They use Unicode and, therefore, can be internationalized. Also, in some cases,
character streams are more efficient than byte streams.


for the most part, the functionality of byte streams is paralleled by that of the character streams.

At the lowest level, all I/O is still byte-oriented. The character-based streams simply provide a convenient and efficient means for handling characters.


#### The Byte Stream Classes

Byte streams are defined by using two class hierarchies. At the top of these are two abstract
classes: InputStream and OutputStream.

InputStream defines the characteristics common to byte input streams and OutputStream describes the behavior of byte output streams.

These two create several subclasses for various functionalities for reading and writig data.

|**Class**|**Meaning**|
|---|---|
|`BufferedInputStream`|Buffered input stream|
|`BufferedOutputStream`|Buffered output stream|
|`ByteArrayInputStream`|Input stream that reads from a byte array|
|`ByteArrayOutputStream`|Output stream that writes to a byte array|
|`DataInputStream`|An input stream that contains methods for reading the Java standard data types|
|`DataOutputStream`|An output stream that contains methods for writing the Java standard data types|
|`FileInputStream`|Input stream that reads from a file|
|`FileOutputStream`|Output stream that writes to a file|
|`FilterInputStream`|Implements `InputStream`|
|`FilterOutputStream`|Implements `OutputStream`|
|`InputStream`|Abstract class that describes stream input|
|`ObjectInputStream`|Input stream for objects|
|`ObjectOutputStream`|Output stream for objects|
|`OutputStream`|Abstract class that describes stream output|
|`PipedInputStream`|Input pipe|
|`PipedOutputStream`|Output pipe|
|`PrintStream`|Output stream that contains `print()` and `println()`|
|`PushbackInputStream`|Input stream that allows bytes to be returned to the stream|
|`SequenceInputStream`|Input stream that is a combination of two or more input streams read sequentially|

---

#### The Character Stream Classes

Character streams are defined by using two abstract classes:
Reader is used for input, and Writer is used for output. 

Concrete classes derived from Reader and Writer operate on Unicode character streams.

The character-based classes parallel the byte-based classes.

| **Class**            | **Meaning**                                                            |
| -------------------- | ---------------------------------------------------------------------- |
| `BufferedReader`     | Buffered input character stream                                        |
| `BufferedWriter`     | Buffered output character stream                                       |
| `CharArrayReader`    | Input stream that reads from a character array                         |
| `CharArrayWriter`    | Output stream that writes to a character array                         |
| `FileReader`         | Input stream that reads from a file                                    |
| `FileWriter`         | Output stream that writes to a file                                    |
| `FilterReader`       | Filtered reader                                                        |
| `FilterWriter`       | Filtered writer                                                        |
| `InputStreamReader`  | Input stream that translates bytes to characters                       |
| `LineNumberReader`   | Input stream that counts lines                                         |
| `OutputStreamWriter` | Output stream that translates characters to bytes                      |
| `PipedReader`        | Input pipe                                                             |
| `PipedWriter`        | Output pipe                                                            |
| `PrintWriter`        | Output stream that contains `print()` and `println()`                  |
| `PushbackReader`     | Input stream that allows characters to be returned to the input stream |
| `Reader`             | Abstract class that describes character stream input                   |
| `StringReader`       | Input stream that reads from a string                                  |
| `StringWriter`       | Output stream that writes to a string                                  |
| `Writer`             | Abstract class that describes character stream output                  |

#### The Predefined Streams

Java programs automatically import the java.lang package. This package
defines a class called System, which encapsulates several aspects of the run-time environment.
Among other things, it contains three predefined stream variables, called in, out, and err. These
fields are declared as public, final, and static within System. This means that they can be used
by any other part of your program and without reference to a specific System object.
System.out refers to the standard output stream. By default, this is the console. System.in
refers to standard input, which is by default the keyboard. System.err refers to the standard
error stream, which is also the console by default. However, these streams can be redirected to
any compatible I/O device.
System.in is an object of type InputStream; System.out and System.err are objects of
type PrintStream. These are byte streams, even though they are typically used to read and
write characters from and to the console. The reason they are byte and not character streams
is that the predefined streams were part of the original specification for Java, which did not
include the character streams. As you will see, it is possible to wrap these within character-
based streams if desired.




#### Using the Byte Streams



#### Reading Console Input



#### Writing Console Output



#### Reading and Writing Files Using Byte Streams



#### Automatically Closing a File



#### Reading and Writing Binary Data


#### Random-Access Files

#### Using Java’s Character-Based Streams

#### Console Input Using Character Streams


#### Console Output Using Character Streams

#### File I/O Using Character Streams


#### Using Java’s Type Wrappers t Convert Numeric Strings

