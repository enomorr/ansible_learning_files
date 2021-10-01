FROM centos:centos7

RUN yum install openssh-server -y
    
RUN yum install -y iputils 

RUN useradd remote_user && \
    echo "remote_user:1234" | chpasswd && \
    mkdir /home/remote_user/.ssh && \
    chmod 700 /home/remote_user/.ssh

COPY remte_key.pub /home/remote_user/.ssh/authorized_keys


RUN chown remote_user:remote_user -R /home/remote_user/.ssh && \
    chmod 600 /home/remote_user/.ssh/authorized_keys


RUN ssh-keygen -A

RUN  yum install -y python3-pip && \
     pip3 install awscli --upgrade --user


CMD  /usr/sbin/sshd -D
