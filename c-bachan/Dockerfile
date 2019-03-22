FROM alpine:3.9

LABEL name="c-bachan"

ENV PATH=/opt/c-bachan:$PATH

ADD ["client", "/tmp/c-bachan/client"]
ADD ["header", "/tmp/c-bachan/header"]
ADD ["server", "/tmp/c-bachan/server"]
ADD ["server-honest", "/tmp/c-bachan/server-honest"]
ADD ["thread", "/tmp/c-bachan/thread"]
ADD ["thread-honest", "/tmp/c-bachan/thread-honest"]
ADD ["CMakeLists.txt", "/tmp/c-bachan/"]

RUN apk add --no-cache libev &&\
    apk add --no-cache --virtual build-dependencies gcc make cmake musl-dev libev-dev &&\
    cd /tmp/c-bachan &&\
    mkdir build && cd build &&\
    cmake -D CMAKE_SKIP_BUILD_RPATH=ON -D CMAKE_BUILD_TYPE=Release .. &&\
    cmake --build . &&\
    mkdir -p /opt/c-bachan &&\
    mv -f client/client /opt/c-bachan/ &&\
    mv -f server/server /opt/c-bachan/ &&\
    mv -f server-honest/server-honest /opt/c-bachan/ &&\
    mv -f thread/thread /opt/c-bachan/ &&\
    mv -f thread-honest/thread-honest /opt/c-bachan/ &&\
    cd /tmp &&\
    rm -rf c-bachan &&\
    apk del build-dependencies