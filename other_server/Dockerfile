FROM ubuntu
ENV TZ=Europe/Moscow
RUN apt-get clean && apt-get update -y 
RUN DEBIAN_FRONTEND=noninteractive TZ=Etc/UTC apt-get -y install tzdata git sudo build-essential autoconf libtool libssl-dev zlib1g-dev librdkafka-dev pkg-config cmake gcc git g++ mysql-client libmysqlclient-dev libboost-all-dev libssl-dev && apt-get clean
RUN git clone -b master https://github.com/pocoproject/poco.git && cd poco && mkdir cmake-build && cd cmake-build && cmake .. && make && sudo make install && cd .. && cd ..
ADD http://date.jsontest.com /etc/builddate
RUN git clone https://github.com/Siegmeyer1/mai_architecture.git
RUN sudo ldconfig
RUN cd mai_architecture && mkdir build && cd build && cmake .. && make
ENTRYPOINT [ "mai_architecture/build/other_service" ]