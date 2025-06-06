# C++ File Handling Concepts
File handling in C++ allows programs to read from and write to files, enabling data storage and retrieval. The `<fstream>` library provides the functionality for file operations.

---

#### **File Streams in C++**
C++ provides three main classes in the `<fstream>` library for file handling:

1. **`ifstream`**: Input file stream (for reading files).
2. **`ofstream`**: Output file stream (for writing files).
3. **`fstream`**: File stream (for both reading and writing).

---

#### **Steps in File Handling**
1. **Include the `<fstream>` header**: 
   ```cpp
   #include <fstream>
   ```
2. **Create a stream object**:
   ```cpp
   std::ifstream infile;  // For reading
   std::ofstream outfile; // For writing
   std::fstream file;     // For both reading and writing
   ```
3. **Open the file**: Use the `.open()` function or directly specify the file name when creating the stream object.
   - Example:
     ```cpp
     infile.open("example.txt");
     outfile.open("output.txt");
     ```
4. **Check if the file is open**:
   ```cpp
   if (infile.is_open()) {
       // File operations
   }
   ```
5. **Perform file operations** (read/write).
6. **Close the file** using `.close()` to free resources.

---

#### **Modes for Opening Files**
Files can be opened in different modes using the second argument of the `.open()` function. Modes include:
- **`ios::in`**: Open for reading.
- **`ios::out`**: Open for writing.
- **`ios::app`**: Append to the end of the file.
- **`ios::trunc`**: Discard the file's existing content.
- **`ios::binary`**: Open in binary mode.

Multiple modes can be combined using the `|` operator:
```cpp
file.open("example.txt", ios::in | ios::binary);
```

---

#### **File Writing Example**
```cpp
#include <iostream>
#include <fstream>
using namespace std;

int main() {
    ofstream obj("example.txt"); // file opening with obj
    // or
    //ofstream obj;
    //obj.open("example.txt"); // file opening with open()

    if (obj.is_open()) {
        obj << "Hello, File Handling in C++!" << endl;
        obj.close();  // file closing
    } else {
        cout << "Unable to open file for writing!" << endl;
    }
    return 0;
}
```
```txt
   Hello, File Handling in C++!
```

---

#### **File Reading Example**
```cpp
#include <iostream>
#include <fstream>
#include <string>
using namespace std;

int main() {
    ifstream obj("example.txt"); // Open for reading 
    if (obj.is_open()) {
        string line;
        while (getline(obj, line)) {
            cout << line << endl;
        }
        obj.close();
    } else {
        cout << "Unable to open file for reading!" << endl;
    }
    return 0;
}
```
```txt
   Hello, File Handling in C++!
```

---

#### **File Reading and Writing Together**
```cpp
#include <iostream>
#include <fstream>
using namespace std;

int main() {
    fstream file("example.txt", ios::in | ios::out | ios::app);

    if (file.is_open()) {
        // Writing to the file
        file << "Appending new content.\n";

        // Reading from the file
        file.seekg(0); // Move file pointer to the beginning
        string line;
        while (getline(file, line)) {
            cout << line << endl;
        }

        file.close();
    } else {
        cout << "Unable to open file!" << endl;
    }

    return 0;
}
```
```txt
   Hello, File Handling in C++!
   Appending new content.

```
---

#### **File Writing**
```cpp
#include <iostream>
#include <fstream>
using namespace std;

int main() {
    //fstream obj("example.txt"); // file opening with obj
    // or
    fstream obj;
    obj.open("example.txt", ios::app); // file opening with open()
    char sentence[40]="Hello, This is Brijesh.";
    int len = strlen(sentence);
    //obj.write(sentence,len);
    //or
    for(int i=0;i<len;i++){
      obj.put(sentence[i]);  
    }
    obj.close();
    return 0;
}
```
```txt
   Hello, This is Brijesh.

```
---

#### **Check if a File Exists**
```cpp
#include <iostream>
#include <fstream>
using namespace std;

int main() {
    string filename = "example.txt";
    
    // Try opening the file in input mode
    ifstream file(filename);
    
    // Check if the file is open (i.e., it exists)
    if (file.is_open()) {
        cout << "File exists!" << endl;
        file.close();  // Close the file
    } else {
        cout << "File does not exist!" << endl;
    }
    
    return 0;
}

```
```txt
   File exists!

```

#### **Important Points**
1. Always close files after use with `.close()`.
2. Use `file.is_open()` to check if the file was successfully opened.
3. File pointers (`seekg` for input, `seekp` for output) can move to specific file positions.
4. Error handling can be implemented using:
   - `fail()`: Checks if a file operation failed.
   - `eof()`: Checks for end-of-file.

---

#### **Common File Handling Functions**
| Function           | Description                                 |
|--------------------|---------------------------------------------|
| `.open()`          | Opens a file.                              |
| `.close()`         | Closes a file.                             |
| `.is_open()`       | Checks if a file is open.                  |
| `.fail()`          | Checks if the last file operation failed.  |
| `.eof()`           | Checks if the end of file is reached.      |
| `.getline()`       | Reads a line from a file.                  |
| `.write()`         | Writes binary data to a file.              |
| `.read()`          | Reads binary data from a file.             |
| `seekp()`  | Moves the file output (write) pointer to a specified position.                                               |
| `seekg()`  | Moves the file input (read) pointer to a specified position.                                                 |
| `tellp()`  | Returns the current position of the output (write) pointer.                                                  |
| `tellg()`  | Returns the current position of the input (read) pointer.                                                    |
| `put()`    | Writes a single character to the file at the current write position.                                         |

---

### **Advantages and Disadvantages of File Handling in C++**

| **Advantages**                                                                 | **Disadvantages**                                                              |
|-------------------------------------------------------------------------------|--------------------------------------------------------------------------------|
| **Storage**: Data remains saved permanently, even after the program ends. | **Complexity**: Requires more boilerplate code compared to higher-level languages. |
| **Data Sharing**: Files allow easy sharing of data between different systems and programs. | **Error-Prone**: Improper handling (e.g., forgetting to close files) may lead to issues like memory leaks or corrupted files. |
| **Scalability**: Handles large volumes of data, exceeding memory limitations.  | **Limited Built-In Parsing**: Parsing complex formats (e.g., JSON, XML) requires additional libraries. |
| **Flexibility**: Supports various file formats (text, binary) and operations (read, write, append). | **Platform Dependency**: File paths and behaviors can differ across operating systems. |
| **Error Handling**: Built-in methods like `.fail()` and `.eof()` make error detection easier. | **Manual Management**: Requires explicit handling of file pointers, modes, and error checks. |
| **Control Over Operations**: Allows fine-grained control over appending, overwriting, and reading specific file parts. | **Performance Overhead**: File I/O is slower than in-memory operations, especially with large files. |
| **Custom Binary Operations**: Efficient for binary read/write operations, particularly for complex data structures. | **Security Risks**: Improper handling can cause vulnerabilities like unauthorized access or overwriting important files. |

---

#### **2 Ways to store data**
| Text           | Binary                                |
|--------------------|---------------------------------------------|
| ASCII code data stored  | Data is stored in Machine code / Binary  |
| It is human readable  | It is not in human readable form (read(), write())   |
| Portable  | Not Portable  |
| .txt   | .dat |

---



## **License**
This project is licensed under the MIT License.

---

Happy Coding!


