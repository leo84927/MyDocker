# golang

# 基本 Image (指定容器的作業系統)
FROM golang:latest

# 安裝所需的工具
RUN set -eux; \
    apt-get update; \
    apt-get -y upgrade; \
    apt-get -y --no-install-recommends install \
            git \
            curl \
            lsof \
            vim; \
    rm -rf /var/lib/apt/lists/*

# 設定 GO111MODULE
RUN go env -w GO111MODULE="on"

#
#--------------------------------------------------------------------------
# Final Touch
#--------------------------------------------------------------------------
#

# Clean up
RUN apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* && \
    rm /var/log/lastlog /var/log/faillog

CMD ["tail", "-f", "/dev/null"]
