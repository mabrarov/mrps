FROM ubuntu:20.04 AS build

RUN apt-get update && \
    apt-get install -y --no-install-suggests --no-install-recommends \
      ca-certificates \
      curl \
      git \
      gcc \
      make \
      libc-dev \
      libev-dev && \
    rm -rf /var/lib/apt/lists/*

ENV CMAKE_HOME="/opt/cmake"

ARG CMAKE_VERSION="3.18.4"

RUN mkdir -p "${CMAKE_HOME}" && \
    cmake_url="https://github.com/Kitware/CMake/releases/download/v${CMAKE_VERSION}/cmake-${CMAKE_VERSION}-Linux-x86_64.tar.gz" && \
    echo "Downloading CMake ${CMAKE_VERSION} from ${cmake_url} to ${CMAKE_HOME}" && \
    curl -jksSL "${cmake_url}" | tar -xzf - -C "${CMAKE_HOME}" --strip-components 1

ENV PATH="${CMAKE_HOME}/bin:${PATH}"

ADD ["CMakeLists.txt", "/usr/src/c-bachan/"]
ADD ["cmake",          "/usr/src/c-bachan/cmake"]
ADD ["client",         "/usr/src/c-bachan/client"]
ADD ["header",         "/usr/src/c-bachan/header"]
ADD ["server",         "/usr/src/c-bachan/server"]
ADD ["server-honest",  "/usr/src/c-bachan/server-honest"]
ADD ["thread",         "/usr/src/c-bachan/thread"]
ADD ["thread-honest",  "/usr/src/c-bachan/thread-honest"]

RUN source_dir="/usr/src/c-bachan" && \
    build_dir="${source_dir}/build" && \
    mkdir -p "${build_dir}" && \
    cmake \
      -D CMAKE_SKIP_BUILD_RPATH=ON \
      -D CMAKE_BUILD_TYPE=Release \
      -D Libev_USE_STATIC_LIBS=ON \
      -S "${source_dir}" \
      -B "${build_dir}" && \
    cmake --build "${build_dir}"

FROM gcr.io/distroless/cc-debian10

ENV PATH="/opt/c-bachan:${PATH}"

COPY --from=build \
    ["/usr/src/c-bachan/build/client/client", \
     "/usr/src/c-bachan/build/server/server", \
     "/usr/src/c-bachan/build/server-honest/server-honest", \
     "/usr/src/c-bachan/build/thread/thread", \
     "/usr/src/c-bachan/build/thread-honest/thread-honest", \
     "/opt/c-bachan/"]

LABEL name="c-bachan"
