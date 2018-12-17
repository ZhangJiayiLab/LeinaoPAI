FROM ufoym/deepo:all-jupyter-py36-cu90

CMD /bin/bash

# ===== ssh service =====
RUN sed -i 's/archive.ubuntu.com/mirrors.ustc.edu.cn/g' /etc/apt/sources.list && \
    apt update && \
    apt install -y openssh-server openssh-client curl && \
    apt-get clean && \
    apt-get autoremove && \
    rm -rf /var/lib/apt/lists/* /tmp/* ~/*

RUN curl -L https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -o miniconda_install.sh && \
    bash ~/miniconda.sh -b -p $HOME/miniconda

ENV PATH="$HOME/miniconda/bin:$PATH"

RUN git clone --depth 1 https://github.com/flatironinstitute/CaImAn && \
    cd CaImAn/ && conda env create -f environment.yml -n caiman && \
    source activate caiman && pip install .
