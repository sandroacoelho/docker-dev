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
    wget https://download.jetbrains.com/idea/ideaIU-2018.1.4.tar.gz && \
    tar -xvzf ideaIU-2018.1.4.tar.gz && \
    rm  ideaIU-2018.1.4.tar.gz 

USER developer
ENV HOME /home/developer

ENTRYPOINT ["bash"]
