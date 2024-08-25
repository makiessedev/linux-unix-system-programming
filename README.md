# linux-unix-system-programming

## Inotify

### Rather than writings lots of code before first compilation, use a frequent **edit-save-build** cycle to catch compiler errors early:

```shell
    while inotifywait -q . ; do clear; make; done
```

*`inotifywait is provided in the inotify-tools package`*

## System data types

> Examples of system data types


| Data type | POSIX type requirement | Description |
|-----------|------------------------|-------------|
| `uid_t` | Integer | User ID |
| `gid_t` | Integer | Groups ID |
| `pid_t` | Signed Integer | Process ID |
| `id_t` | Integer | Generic ID type; can hold pid_t, gid_t, uid_t|
| `off_t` | Signed Integer | File offset or size|
| `sigset_t` | Integer or Structu     re | Signal set |
| `size_t` | Unsigned Integer | Size of object (in bytes) |
| `ssize_t` | Signed Integer | Size of object or error indication |
| `time_t` | Integer/Real-floating | Time in seconds since Epoch |
| `timer_t` | Arithmetic type | POSIX timer ID |

> `(Arithmetic type == integer or floating type)`

## File descriptors (FD)

| FD | PORPOSE | POSIX name | stdio stream |
|----|---------|------------|--------------|
| `0` | Standard input | STDIN_FILENO | `stdin` |
| `1` | Standard output | STDOUT_FILENO | `stdout` |
| `2` | Standard error | STDERR_FILENO | `stderr` |

> are defined in <unistd.h>

 ## Key file I/O system calls

| fc | Description |
|----|---------|
| `open(const char \*pathname , int flags , mode_t mode)` | open a file, optionally creating it if needed. Returns file descriptor used by remaining calls |
| `read()` | input |
| `write()` | output |
| `close()` | close file descriptor |

### Open Flags

| Flag         | Description                                                                                           |
|--------------|-------------------------------------------------------------------------------------------------------|
| `O_RDONLY`   | Open the file for read-only access.                                                                   |
| `O_WRONLY`   | Open the file for write-only access.                                                                  |
| `O_RDWR`     | Open the file for both reading and writing.                                                           |
| `O_CLOEXEC`  | Set the close-on-exec flag for the file descriptor. This flag ensures that the file descriptor is automatically closed when executing a new program. |
| `O_CREAT`    | Create the file if it does not exist. Requires a third argument to specify the file mode (permissions). |
| `O_DIRECTORY`| Fail if the file is not a directory. This flag ensures that the `pathname` refers to a directory.       |
| `O_EXCL`     | Ensure that the call creates the file. If the file already exists, the call will fail. This flag requires `O_CREAT` to be set. |
| `O_NOCTTY`   | Do not make the file the controlling terminal for the process.                                        |
| `O_NOFOLLOW` | Do not follow symbolic links; if the `pathname` is a symbolic link, the open call will fail.            |
| `O_TMPFILE`  | Create a temporary file. The file will be created in the directory specified by `pathname` but will not be visible in the filesystem. Requires `O_DIRECTORY` to be set. |
| `O_TRUNC`    | Truncate the file to zero length if it already exists.                                                  |
| `O_APPEND`   | Append data to the end of the file.                                                                    |
| `O_ASYNC`    | Enable signal-driven I/O for the file descriptor. This flag allows asynchronous notifications for I/O operations. |

> `man open to more flgas or details`