# linux-unix-system-programming

### Rather than writings lots of code before first compilation, use a frequent **edit-save-build** cycle to catch compiler errors early:

```shell
    while inotifywait -q . ; do clear; make; done
```

*inotifywait is provided in the inotify-tools package*
