ARG PHP_EXTENSIONS="mysqli pgsql pdo_mysql pdo_pgsql"

FROM thecodingmachine/php:8.1-v4-apache-node12
WORKDIR /workspace


## AWS CLI
# 使用するベースイメージを指定
FROM mcr.microsoft.com/vscode/devcontainers/base:0-buster

# 必要なツールのインストール
#RUN apt-get update && apt-get install -y \
#    curl \
#    unzip \
#    && rm -rf /var/lib/apt/lists/*

# AWS CLIのインストール
#RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" \
#    && unzip awscliv2.zip \
#    && ./aws/install

ARG VARIANT="18"
FROM mcr.microsoft.com/vscode/devcontainers/typescript-node:0-${VARIANT}
RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" \
  && unzip awscliv2.zip \
  && ./aws/install \
  && rm -rf ./aws awscliv2.zip \
  && npm install -g typescript \
  && npm install -g aws-cdk \
  && npm install -g npm-check-updates
RUN curl -sL -O https://github.com/kayac/ecspresso/releases/download/v2.0.0/ecspresso_2.0.0_linux_amd64.tar.gz \
  && tar -zxvf ecspresso_2.0.0_linux_amd64.tar.gz \
  && sudo install ecspresso /usr/local/bin/ecspresso \
  && rm -f LICENSE README.md ecspresso ecspresso_2.0.0_linux_amd64.tar.gz