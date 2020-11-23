bootstrap: docker
from: nvidia/cuda:10.2-cudnn7-devel-ubuntu18.04

%environment
    # setup necessary bash variables
    export LC_ALL=en_US.utf8
    export POETRY_VIRTUALENVS_IN_PROJECT=1
    # setup PATH to point to julia, poetry, and blender
    export PATH=$PATH:/poetry/bin

%runscript
    exec bash "$@"

%post
    # install deps available in os repos
    export DEBIAN_FRONTEND=noninteractive
    apt-get update
    apt-get install -y locales
    locale-gen en_US.utf8
    export LC_ALL=en_US.utf8
    apt-get install -y  build-essential \
                        curl \
                        graphviz \
                        git \
                        wget \
                        cmake \
                        python3.8 \
                        python3.8-distutils \
                        python3.8-venv
    apt-get clean

    # set up poetry (package manager for python)
    export POETRY_HOME=/poetry
    curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py | python3.8
    chmod +x /poetry/bin/*
