# debian:latest points to latest stable release: trixie
FROM debian:latest
# ARG DEBIAN_FRONTEND=noninteractive
# Get newest updates
USER root

RUN DEBIAN_FRONTEND=noninteractive apt-get -qq update && apt-get full-upgrade -y
RUN DEBIAN_FRONTEND=noninteractive apt-get -qq install neovim eza curl locales gnupg2
ENV LC_ALL=en_US.UTF-8
ENV LANG=en_US.UTF-8
ENV LANGUAGE en_US:en
RUN sed -i '/en_US.UTF-8/s/^# //g' /etc/locale.gen && \
    locale-gen
RUN DEBIAN_FRONTEND=noninteractive apt-get -qq install git openssh* ssh* openssl*

# locales setup
RUN locale
RUN locale-gen en_US en_US.UTF-8
RUN update-locale LANG=en_US.UTF-8
RUN DEBIAN_FRONTEND=noninteractive apt-get -qq install unzip zip

RUN useradd -rm -d /home/nyx -U -s /bin/bash -G sudo,tty,dialout,video,root -u 1001 -p "$(openssl passwd -6 qwerty)" nyx

# ARG WS_PWD=$PWD
WORKDIR /home/nyx
RUN mkdir -p bin

RUN DEBIAN_FRONTEND=noninteractive apt-get update && apt-get full-upgrade -y

RUN <<-EOF
cat <<-EO2F >> /home/nyx/.bashrc
# ------------------------------------------- #
export PATH="$PATH:/home/nyx/bin"
alias viba="vim /home/nyx/.bashrc"
export LANG=en_US.UTF-8
alias ll="eza -la --bytes -all --icons --color=always"
alias ls="eza -la --bytes -all --icons --color=always"
alias reba=". /home/nyx/.bashrc"
alias syup="sudo apt update && sudo apt full-upgrade -y"
alias rp="realpath"
alias suaptinst="sudo apt install -y"
# ------------------------------------------- #
EO2F
EOF
RUN chown -R nyx:nyx /home/nyx/*
RUN sed -i -e 's/#force_color_prompt=yes/force_color_prompt=yes/g' .bashrc

USER nyx