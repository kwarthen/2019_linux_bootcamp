FROM sickp/alpine-sshd:latest
MAINTAINER chapmanbe <brian.chapman@utah.edu>

# Create jovyan user with UID=1000 and in the 'users' group
RUN apk add --no-cache bash bash-completion
RUN adduser -D -h /home/jovyan -s /bin/bash -u 1000 jovyan && \
    echo "jovyan:jovyan" | chpasswd && \
    passwd -d root && \
    sed -i "s/PermitRootLogin yes/PermitRootLogin no/" /etc/ssh/sshd_config
