FROM nvidia/cuda:11.8.0-devel-ubuntu22.04

# Set UTF-8 locale
RUN apt-get update && \
    apt-get install --no-install-recommends -y locales && \
    locale-gen en_US.UTF-8 && \
    rm -rf /var/lib/apt/lists/*
ENV LANG=en_US.UTF-8 \
    LANGUAGE=en_US:en \
    LC_ALL=en_US.UTF-8

# Install Python 3.10 and essential tools
RUN apt-get update && \
    apt-get install --no-install-recommends -y \
        python3.10 \
        python3.10-venv \
        python3.10-distutils \
        curl \
        git \
        sudo \
        openssh-client \
        ca-certificates \
        wget && \
    ln -sf python3.10 /usr/bin/python3 && \
    rm -rf /var/lib/apt/lists/*


# Install pip (latest) and PyTorch + dependencies
RUN curl -sS https://bootstrap.pypa.io/get-pip.py | python3 && \
    pip install --upgrade pip && \
    pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118


# Create working directory
WORKDIR /workspace

# Use bash by default
CMD ["/bin/bash"]
