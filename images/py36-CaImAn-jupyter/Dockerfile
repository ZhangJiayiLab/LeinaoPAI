FROM conda/miniconda3

CMD /bin/bash

# ===== ssh service =====
RUN apt update && \
    apt install -y openssh-server openssh-client curl && \
    apt-get clean && \
    apt-get autoremove && \
    rm -rf /var/lib/apt/lists/* /tmp/* ~/*

RUN git clone --depth 1 https://github.com/flatironinstitute/CaImAn && \
    cd CaImAn/ && conda env create -f environment.yml -n caiman && \
    source activate caiman && pip install .
