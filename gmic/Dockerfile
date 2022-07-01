FROM i386/debian:buster

# Set environment variables
ENV DIST_NAME=debian-10
ENV USER=gmic
ENV HOME=/home/$USER

# Update and install basic OS packages
RUN \
        apt-get update; \
# Set up a user, and etc.
        mkdir -p /dist; \
        adduser --disabled-password --gecos "" ${USER}; \
        echo "${USER} ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers; \
# Install development packages needed for building
        apt-get install -y \
                 git \
                 build-essential \
                 libgimp2.0-dev \
                 libcurl4-openssl-dev \
                 libfftw3-dev \
                 libtiff-dev \
                 libjpeg-dev \
                 libopenexr-dev \
                 qtbase5-dev \
                 qttools5-dev-tools



# Set the user and group to use for the rest of the commands
USER ${USER}:${USER}

# Set the working directory
WORKDIR ${HOME}

# Create virtual environments for each Python
RUN \
        git clone --depth=1 https://github.com/dtschump/CImg.git \
        git clone --depth=1 https://github.com/dtschump/gmic.git \
        git clone --depth=1 https://github.com/c-koi/gmic-qt.git
        
# Define default command
CMD ["/bin/bash", "-l"]
