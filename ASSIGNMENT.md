#### Question: Describe and discuss the use case of the following:

1. **fork()**
   The `fork()` system call is a fundamental operation in operating systems used to create a new process by duplicating the calling process. The new process, known as the child process, runs concurrently with the parent process. After a new child process is created, both the parent and child processes will execute the next instruction following the `fork()` system call.

2. **exec()**
   The `exec()` function replaces the current process image with a new process image. It runs an executable file in the context of an already existing process, terminating the current process and starting a new one. This is commonly used to run different programs within the same process context.

3. **getpid()**
   The `getpid()` function returns the process ID (PID) of the calling process. It is simple to use and does not take any arguments. When a parent process creates a child process using `fork()`, it can use `getpid()` to manage and coordinate between the parent and child processes.

4. **wait()**
   The `wait()` function is used by a parent process to wait for its child processes to terminate. When a parent process calls `wait()`, it pauses execution until one of its child processes exits or a signal is received. This function helps manage the lifecycle of multiple child processes spawned by a parent process.

5. **stat()**
   The `stat()` function retrieves information about a file or directory, such as size, permissions, owner, and timestamps. This function is commonly used in file management and system programming to get detailed attributes of files and directories.

6. **opendir()**
   The `opendir()` function opens a directory stream, which can be used to read the contents of the directory using functions like `readdir()`, and to close the directory stream with `closedir()`. It is commonly used in utilities that need to manage or analyze directory contents.

7. **readdir()**
   The `readdir()` function reads directory entries from a directory stream opened with `opendir()`. It allows iteration through the contents of a directory and retrieval of information about each file or subdirectory within it.

8. **close()**
   The `close()` function closes a file descriptor, which is an integer handle used by the operating system to identify an open file, socket, or other I/O resource. Closing a file descriptor releases the associated resources and marks it as no longer in use.

---

### Program for Producer-Consumer Problem

```c
#include <stdio.h>
#include <stdlib.h>

int buffer = 0;  // Current number of items in the buffer
const int bufferSize = 10;

void producer() {
    if (buffer < bufferSize) {
        buffer++;
        printf("\nProducer produces item %d", buffer);
    } else {
        printf("\nBuffer is full!");
    }
}

void consumer() {
    if (buffer > 0) {
        printf("\nConsumer consumes item %d", buffer);
        buffer--;
    } else {
        printf("\nBuffer is empty!");
    }
}

int main() {
    int choice;
    while (1) {
        printf("\n1. Press 1 for Producer");
        printf("\n2. Press 2 for Consumer");
        printf("\n3. Press 3 for Exit");
        printf("\nEnter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                producer();
                break;
            case 2:
                consumer();
                break;
            case 3:
                exit(0);
            default:
                printf("\nInvalid choice! Please try again.");
        }
    }
    return 0;
}

```
