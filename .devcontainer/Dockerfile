FROM mcr.microsoft.com/devcontainers/base:ubuntu-22.04

ENV DEBIAN_FRONTEND=noninteractive

# Install XFCE and VNC
RUN apt-get update && apt-get install -y \
    xfce4 \
    xfce4-goodies \
    xfce4-terminal \
    tigervnc-standalone-server \
    tigervnc-common \
    novnc \
    websockify \
    dbus-x11 \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

# Setup VNC password
RUN mkdir -p /root/.vnc && \
    echo "codespace" | vncpasswd -f > /root/.vnc/passwd && \
    chmod 600 /root/.vnc/passwd

# Create xstartup
RUN echo '#!/bin/bash\nstartxfce4' > /root/.vnc/xstartup && \
    chmod +x /root/.vnc/xstartup

EXPOSE 6080 5901

CMD ["/bin/bash"]
