FROM base/devel
LABEL maintainer "Darlan"

RUN pacman --noconfirm -Sy archlinux-keyring && pacman --noconfirm -Syu \
&& pacman --noconfirm -S wget python gcc-fortran git cmake ninja \
&& wget --no-check-certificate --quiet https://bootstrap.pypa.io/get-pip.py \
&& python get-pip.py \
&& rm get-pip.py \
&& pip install -q -U pip \
&& pip install -q --no-cache-dir conan \
&& useradd -m conan \
&& groupadd sudo \
&& gpasswd -a conan sudo \
&& echo "conan ALL= NOPASSWD: ALL" >> /etc/sudoers

USER conan
WORKDIR /home/conan
RUN mkdir -p /home/conan/.conan

CMD ["/bin/bash"]
