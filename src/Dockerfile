FROM archlinux:latest

RUN pacman -Syu --noconfirm && \
    pacman -S --noconfirm \
    base-devel \
    git \
    sudo \
    go \
    vim 

RUN useradd -m -G wheel aurbuilder && \
    echo 'aurbuilder ALL=(ALL) NOPASSWD: ALL' >> /etc/sudoers

RUN mkdir -p /__w/_temp && chmod -R 777 /__w/_temp

USER aurbuilder
WORKDIR /home/aurbuilder

RUN git clone https://aur.archlinux.org/yay.git && \
    cd yay && \
    makepkg -si --noconfirm

RUN sudo pacman -Scc --noconfirm && \
    sudo rm -rf /var/cache/pacman/pkg/* yay

USER root

ENTRYPOINT ["/bin/bash"]
