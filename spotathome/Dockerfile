FROM ubuntu
RUN apt-get update
RUN apt-get install -y g++ git make zlib1g-dev libboost-all-dev libssl-dev cmake
RUN apt-get install -y vim
RUN useradd -ms /bin/bash dev
USER dev
WORKDIR /home/dev
RUN git clone https://github.com/Microsoft/cpprestsdk.git casablanca
WORKDIR /home/dev/casablanca/Release
RUN mkdir build.debug
WORKDIR /home/dev/casablanca/Release/build.debug
RUN pwd
RUN cmake .. -DCMAKE_BUILD_TYPE=Debug
RUN make
USER root
RUN make install
USER dev
WORKDIR /home/dev
RUN ls
RUN git clone https://github.com/chusAlvarez/spotathome.git spotathome
WORKDIR /home/dev/spotathome
RUN make clean
RUN export LD_LIBRARY_PATH=/usr/local/lib && make test
ENTRYPOINT /bin/bash
