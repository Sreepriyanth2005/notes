e#### Evaluation

| Generation | Time Period | Key Feature                     | Example                       |
| ---------- | ----------- | ------------------------------- | ----------------------------- |
| 1st        | 1940s–50s   | No OS, manual control           | ENIAC                         |
| 2nd        | 1950s–60s   | Batch processing                | IBM 7090                      |
| 3rd        | 1960s–70s   | Multiprogramming / multitasking | OS/360                        |
| 4th        | 1970s–80s   | GUI, PC OS                      | MS-DOS, early Windows         |
| 5th        | 1990s–Now   | Modern OS, networking, mobile   | Windows 10/11, Linux, Android |


#### Types of OS

|**Type of OS**|**Definition**|**Example**|**Key Feature / Use Case**|
|---|---|---|---|
|**Single-User, Single-Tasking**|Only one user can use the system and run one task at a time|MS-DOS (1981)|Simple, sequential execution; basic personal computers|
|**Batch Processing OS**|Jobs are collected into batches and executed sequentially without user interaction|ATLAS (Manchester Univ., 1950s–60s)|Efficient for processing large jobs; CPU idle time reduced|
|**Multiprogramming OS**|Multiple programs are loaded in memory; CPU switches between them to maximize utilization|THE System (Dijkstra, 1960s)|Efficient CPU usage; multiple jobs run concurrently|
|**Multitasking / Time-Sharing OS**|CPU time is divided among multiple tasks; gives the impression of simultaneous execution|CTSS (MIT, 1960s), Modern Windows/Linux|Interactive use; multiple programs appear to run simultaneously|

#### Types of System calls

| **Type**                       | **Definition / Purpose**                                          | **Examples**                                         |
| ------------------------------ | ----------------------------------------------------------------- | ---------------------------------------------------- |
| **1. Process Control**         | Manage processes: create, terminate, suspend, or resume processes | `fork()`, `exit()`, `wait()`, `exec()`               |
| **2. File Management**         | Perform operations on files and directories                       | `open()`, `read()`, `write()`, `close()`, `delete()` |
| **3. Device Management**       | Interact with hardware devices (I/O operations)                   | `read()`, `write()`, `ioctl()`, `close()`            |
| **4. Information Maintenance** | Get or set system or process information                          | `getpid()`, `alarm()`, `time()`, `sleep()`           |
| **5. Communication**           | Facilitate inter-process communication                            | `pipe()`, `shmget()`, `msgsnd()`, `recv()`           |
| **6. Protection**              | Control access and permissions for processes and resources        | `chmod()`, `chown()`, `umask()`, `access()`          |


| **Type**                    | **System Call**         | **Function / What it Does**                                             |
| --------------------------- | ----------------------- | ----------------------------------------------------------------------- |
| **Process Control**         | `fork()`                | Creates a new process (child process) from the calling process          |
|                             | `exit(status)`          | Terminates the calling process and returns a status code                |
|                             | `wait()`                | Makes a process wait until its child process finishes execution         |
|                             | `exec()`                | Replaces the current process image with a new program                   |
|                             | `getpid()`              | Returns the Process ID (PID) of the calling process                     |
|                             | `getppid()`             | Returns the Parent Process ID of the calling process                    |
| **File Management**         | `open()`                | Opens a file for reading/writing and returns a file descriptor          |
|                             | `read()`                | Reads data from a file into a buffer                                    |
|                             | `write()`               | Writes data from a buffer to a file                                     |
|                             | `close()`               | Closes an opened file descriptor                                        |
|                             | `unlink()` / `delete()` | Deletes a file from the filesystem                                      |
|                             | `lseek()`               | Moves the file pointer to a specified location in the file              |
| **Device Management**       | `ioctl()`               | Performs device-specific input/output operations                        |
|                             | `read()`                | Reads data from a device (like keyboard, disk)                          |
|                             | `write()`               | Writes data to a device                                                 |
|                             | `close()`               | Closes a device (similar to file)                                       |
| **Information Maintenance** | `time()`                | Returns the current system time                                         |
|                             | `gettimeofday()`        | Returns current time with higher precision                              |
|                             | `alarm()`               | Schedules a signal to be sent after a specified time                    |
|                             | `sleep()`               | Suspends the process for a specified number of seconds                  |
| **Communication**           | `pipe()`                | Creates a pipe for communication between processes                      |
|                             | `shmget()`              | Allocates a shared memory segment                                       |
|                             | `shmat()`               | Attaches a shared memory segment to a process                           |
|                             | `msgsnd()`              | Sends a message to a message queue                                      |
|                             | `msgrcv()`              | Receives a message from a message queue                                 |
| **Protection**              | `chmod()`               | Changes permissions of a file                                           |
|                             | `chown()`               | Changes ownership of a file                                             |
|                             | `umask()`               | Sets default file creation permissions                                  |
|                             | `access()`              | Checks whether the process can access a file with specified permissions |
