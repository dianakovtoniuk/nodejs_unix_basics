
# Nodejs Unix Basics

Exploring how Node.js works with core Unix concepts: standard streams, pipes, processes, environment variables and child processes, with a bit of C and bash on the side.

## Structure

```
.
├── playground.js              # stdin, stdout and stderr, plus commented examples (argv, pid, env, spawn, exec)
├── playground.c               # C program that Node talks to over standard streams
├── cat.js                     # minimal clone of the Unix cat command
├── scripts.sh                 # bash alias, variable, function and pipe
├── learning-c/
│   └── app.c                  # basic C program
└── massive-communication/
    └── app.js                 # pipes a large file into a C program running as a child process
```

## Getting started

Requires Node.js 18+, a C compiler (gcc or clang) and bash.

Standard streams:

```bash
echo "hello" | node playground.js
```

Node talking to a C program (uncomment the `spawn` block in `playground.js` first):

```bash
gcc playground.c -o playground
node playground.js
```

The cat clone:

```bash
node cat.js some-file.txt   # prints a file
echo "hi" | node cat.js     # copies stdin to stdout
```

Shell script:

```bash
source scripts.sh
```

## Notes

- Most of `playground.js` and `playground.c` is commented out on purpose. Uncomment one section at a time to try it.
- `massive-communication/app.js` expects a `number_formatter` executable in your `PATH` and a large text file at a hardcoded path. Edit both before running it.
````
