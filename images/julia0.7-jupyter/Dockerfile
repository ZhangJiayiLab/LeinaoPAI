FROM ufoym/deepo:all-jupyter-py36-cu90


# ===== ssh service =====
RUN sed -i 's/archive.ubuntu.com/mirrors.ustc.edu.cn/g' /etc/apt/sources.list && \
    apt update && \
    apt install -y openssh-server openssh-client && \
    apt-get clean && \
    apt-get autoremove && \
    rm -rf /var/lib/apt/lists/* /tmp/* ~/*

RUN apt-get install -y python-software-properties software-properties-common

RUN apt-get-repository ppa:staticfloat/juliareleases && apt-get update
RUN apt-get install -y julia
RUN julia -e "using Pkg; Pkg.resolve()"
