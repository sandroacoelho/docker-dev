FROM java:8

RUN apt-get update && \
    apt-get -y install maven git sudo && \
    mkdir -p /home/developer && \
    mkdir -p /etc/sudoers.d && \
    adduser --quiet --disabled-password --shell /bin/bash --home /home/developer --gecos "User" developer && \
    export uid=1000 gid=1000 && \
    echo "developer:developer" | chpasswd && \
    echo "developer:x:${uid}:${gid}:Developer,,,:/home/developer:/bin/bash" >> /etc/passwd && \
    echo "developer:x:${uid}:" >> /etc/group && \
    echo "developer ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/developer && \
    chmod 0440 /etc/sudoers.d/developer && \
    chown ${uid}:${gid} -R /home/developer && \
    cd /opt && \
    wget http://downloads.typesafe.com/scalaide-pack/4.7.0-vfinal-oxygen-212-20170929/scala-SDK-4.7.0-vfinal-2.12-linux.gtk.x86_64.tar.gz && \
    wget https://downloads.lightbend.com/scala/2.12.7/scala-2.12.7.tgz && \
    wget https://www-eu.apache.org/dist/spark/spark-2.4.0/spark-2.4.0-bin-hadoop2.7.tgz && \
    tar -xvzf scala-SDK-4.7.0-vfinal-2.12-linux.gtk.x86_64.tar.gz && \
    rm  scala-SDK-4.7.0-vfinal-2.12-linux.gtk.x86_64.tar.gz && \
    tar -xvzf scala-2.12.7.tgz && \
    rm scala-2.12.7.tgz && \
    tar -xvzf spark-2.4.0-bin-hadoop2.7.tgz && \
    rm spark-2.4.0-bin-hadoop2.7.tgz
