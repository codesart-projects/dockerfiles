FROM debian:stable-slim

USER root

WORKDIR /root

RUN /bin/bash -c                                                                 '  \
        apt-get update && apt -y upgrade                                         && \
        apt-get -y install iputils-ping telnet net-tools                         && \
        apt-get -y install curl wget vim zip unzip tar locales                   && \
        sed -i -e "s/# zh_CN.UTF-8 UTF-8/zh_CN.UTF-8 UTF-8/" /etc/locale.gen     && \
        dpkg-reconfigure -f noninteractive locales                               && \
        ln -snf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime                 && \
        dpkg-reconfigure -f noninteractive tzdata                                && \
        rm -rf /var/lib/apt/lists/* && apt-get -y autoremove && apt-get clean    && \
        curl -s "https://get.sdkman.io" | bash                                   && \
        source "/root/.sdkman/bin/sdkman-init.sh"                                && \
        sdk install java 21.0.2-graal                                            && \
        sdk install visualvm 2.1.7                                               '

ENV LANG "zh_CN.UTF-8"
ENV LC_ALL "zh_CN.UTF-8"
ENV PATH /root/.sdkman/candidates/java/current/bin:$PATH
