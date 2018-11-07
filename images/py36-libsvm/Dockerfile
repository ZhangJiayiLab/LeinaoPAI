FROM ubuntu:16.04

RUN sed -i 's/archive.ubuntu.com/mirrors.tuna.tsinghua.edu.cn/g' /etc/apt/sources.list && \
    APT_INSTALL="apt-get install -y --no-install-recommends" && \
    apt-get update && \
    $APT_INSTALL \
        build-essential \
        ca-certificates \
        cmake \
        wget \
        git \
        vim \
        openssh-client \
        openssh-server \
        unzip \
        && \
    ldconfig && \
    apt-get clean && \
    apt-get autoremove && \
    rm -rf /var/lib/apt/lists/* /tmp/* ~/*

RUN wget --quiet https://mirrors.tuna.tsinghua.edu.cn/anaconda/miniconda/Miniconda3-4.5.4-Linux-x86_64.sh -O ~/conda.sh && \
    /bin/bash ~/conda.sh -b -p /opt/conda && \
    rm ~/conda.sh

RUN conda config --set show_channel_urls yes && \
    conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/ && \
    conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/

RUN conda install -y scipy numpy matplotlib h5py pandas && \
    conda clean -y --all

RUN wget -O libsvm.tar.gz http://www.csie.ntu.edu.tw/~cjlin/cgi-bin/libsvm.cgi?+http://www.csie.ntu.edu.tw/~cjlin/libsvm+tar.gz && \
    tar xzf libsvm.tar.gz && \
    cd libsvm && \
    make && cd python && make && cd .. && \
    ln -s $(pwd)/python /opt/conda/lib/python3.6/site-packages/libsvm && \
    cd ..

EXPOSE 6006
WORKDIR /userhome
