FROM nvcr.io/nvidia/pytorch:22.07-py3

LABEL maintainer="Bernd Doser <bernd.doser@h-its.org>"

COPY requirements.txt .
RUN pip3 install -r requirements.txt

ARG USERNAME=vscode
ARG USER_UID=15005
ARG USER_GID=15000

RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
    && apt-get update \
    && apt-get install -y sudo \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME
