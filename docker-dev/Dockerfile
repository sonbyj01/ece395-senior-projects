FROM nvcr.io/nvidia/pytorch:20.11-py3

ARG DEBIAN_FRONTEND=noninteractive

SHELL ["/bin/bash", "-c"]

RUN apt update && \
    apt install -y zip htop screen libgl1-mesa-glx vim

RUN pip install seaborn thop

RUN cd / && \
    git clone https://github.com/JunnYu/mish-cuda && \
    cd mish-cuda && \
    python setup.py build install

RUN cd / && \
    git clone https://github.com/fbcotter/pytorch_wavelets && \
    cd pytorch_wavelets && \
    pip install .

CMD ["bash"]
