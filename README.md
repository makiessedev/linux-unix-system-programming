# linux-unix-system-programming

### Rather than writings lots of code before first compilation, use a frequent **edit-save-build** cycle to catch compiler errors early:

```shell
    while inotifywait -q . ; do clear; make; done
```

*inotifywait is provided in the inotify-tools package*

## System data types

> Examples of system data types


| Data type | POSIX type requirement | Description |
|-----------|------------------------|-------------|
| uid_t | Integer | User ID |
| gid_t | Integer | Groups ID |
| pid_t | Signed Integer | Process ID |
| id_t | Integer | Generic ID type; can hold pid_t, gid_t, uid_t|
| off_t | Signed Integer | File offset or size|
| sigset_t | Integer or Structu     re | Signal set |
| size_t | Unsigned Integer | Size of object (in bytes) |
| ssize_t | Signed Integer | Size of object or error indication |
| time_t | Integer/Real-floating | Time in seconds since Epoch |
| timer_t | Arithmetic type | POSIX timer ID |

> (Arithmetic type == integer or floating type)

## File descriptors (FD)

| FD | PORPOSE | POSIX name | stdio stream |
|----|---------|------------|--------------|
| 0 | Standard input | STDIN_FILENO | stdin |
| 1 | Standard output | STDOUT_FILENO | stdout |
| 2 | Standard error | STDERR_FILENO | stderr |

> are defined in <unistd.h>