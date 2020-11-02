# Building

## Requirements

1. C toolchain (compiler, linker, standard C library)
1. Make
1. [CMake](https://cmake.org/)
1. [libev](http://software.schmorp.de/pkg/libev.html)

## Steps to build

Assuming current directory is directory where this file is located

```bash
cmake -D CMAKE_SKIP_BUILD_RPATH=ON -D CMAKE_BUILD_TYPE=Release .
cmake --build .
```

# Docker image

## Building

### Requirements

1. Docker 17.06+ for building
1. Current directory is directory where this repository is cloned

### Steps to build

```bash
docker build -t c-bachan c-bachan
```

## Running with Docker

```bash
docker run --rm c-bachan $app $params
```

where

* `$app` is application to run, i.e. one of:
  - `client`
  - `server`
  - `server-honest`
  - `thread`
  - `thread-honest`
* `$params` are parameters passed to application
