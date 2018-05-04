FROM node:9

RUN apt-get update && \
    apt-get -y -f install git libgtk2.0-0 libxss1 libx11* apt-transport-https sudo  && \ 
    curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg && \
    mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg && \
    sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main" > /etc/apt/sources.list.d/vscode.list'  && \
    apt-get update && \
    apt-get -y -f install code &&\
    mkdir -p /home/developer && \
    mkdir -p /etc/sudoers.d && \
    adduser --quiet --disabled-password --shell /bin/bash --home /home/developer --gecos "User" developer && \
    export uid=1000 gid=1000 && \
    echo "developer:developer" | chpasswd && \
    echo "developer:x:${uid}:${gid}:Developer,,,:/home/developer:/bin/bash" >> /etc/passwd && \
    echo "developer:x:${uid}:" >> /etc/group && \
    echo "developer ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/developer && \
    chmod 0440 /etc/sudoers.d/developer && \
    chown ${uid}:${gid} -R /home/developer    
 

USER developer
ENV HOME /home/developer

ENTRYPOINT ["bash"]
