FROM debian:stable
RUN apt-get update
RUN apt-get install -y gawk wget git-core diffstat unzip texinfo gcc-multilib build-essential chrpath socat libsdl1.2-dev xterm
WORKDIR /yocto
RUN git clone git://git.yoctoproject.org/poky -b fido
RUN git clone git://git.yoctoproject.org/meta-rockchip -b fido
RUN apt-get install cpio
RUN /bin/bash -c "source poky/oe-init-build-env && \
sed -i 's/MACHINE ??= "qemux86"/MACHINE ?="marsboard-rk3066"/g' conf/local.conf && \
sed -i '10i\  /yocto/meta-rockchip \\\ ' conf/bblayers.conf && \
touch conf/sanity.conf && \
bitbake core-image-minimal && \
bitbake linux-petitboot"
