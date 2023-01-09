FROM ubuntu:22.04

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y -q \
			sudo \
			curl \
			vim \
			git \
			tmux \
	        build-essential \
			bash-completion \ 
			libssl-dev
			

RUN useradd -m dev_user && \
    echo "dev_user:dev_user" | chpasswd && \
    adduser dev_user sudo

WORKDIR /home/dev_user

RUN su - dev_user  -c \
    "curl -fL https://github.com/coursier/launchers/raw/master/cs-x86_64-pc-linux.gz | gzip -d > /home/dev_user/cs" && \
    su - dev_user  -c "chmod +x /home/dev_user/cs" && \
    su - dev_user  -c "/home/dev_user/cs setup --jvm 11 -y" && \
    su - dev_user  -c "rm /home/dev_user/cs" && \
	su - dev_user  -c "curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash" && \
	su - dev_user  -c "nvm install 16 --lts" 

USER dev_user
CMD /bin/bash
