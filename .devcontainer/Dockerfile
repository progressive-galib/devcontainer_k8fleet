FROM debian:12

RUN apt-get update && apt-get install -y \
    build-essential \
    openssl \
    sudo \
    tigervnc-standalone-server \
    python3 \
    python3-pip \
    python-is-python3 \
    wget \
    #&& rm -rf /var/lib/apt/lists/*

# Install noVNC
WORKDIR /opt
RUN wget https://github.com/novnc/noVNC/archive/refs/tags/v1.5.0.tar.gz
RUN tar -xzf v1.5.0.tar.gz
WORKDIR /opt/noVNC-1.5.0

# Create VNC password (replace with your actual password)
RUN tigervnc-passwd -c "your_vnc_password" > /home/user/.vnc/passwd

# Environment variables
ENV DISPLAY_WIDTH=1920 \
    DISPLAY_HEIGHT=1080 \
    WEB_LISTENING_PORT=5800 \
    VNC_LISTENING_PORT=5900 \
    DISPLAY=:1

# Expose ports
#EXPOSE 6081  # noVNC web port
#EXPOSE 5900  # VNC port (optional, for direct VNC connection)

# Start noVNC and VNC server
#CMD ["/usr/local/bin/novnc_startup.sh"]
