FROM python:3.6.11-slim-buster

LABEL maintainer="Mr.D"

COPY sources.list /etc/apt
RUN apt-get update \
    && apt-get install -y --no-install-recommends locales debconf \
    && echo "Asia/Shanghai" > /etc/timezone \
    && dpkg-reconfigure -f noninteractive tzdata  \
    && cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && sed -i -e 's/# en_US.UTF-8 UTF-8/en_US.UTF-8 UTF-8/' /etc/locale.gen \
    && echo 'LANG="en_US.UTF-8"'>/etc/default/locale \
    && dpkg-reconfigure --frontend=noninteractive locales \
    && update-locale LANG=en_US.UTF-8 \
    && apt-get install -yqq --no-install-recommends \
    apt-utils \
    cron \
    make \
    vim \
    && apt-get clean && \
    rm -rf /var/lib/apt/lists/* \
    && pip install --upgrade pip -i https://pypi.douban.com/simple \
    && pip config set global.index-url https://pypi.douban.com/simple \
    && pip install pipenv --no-cache-dir

ENV LC_ALL=en_US.UTF-8 \
    LANG=en_US.UTF-8 \
    LANGUAGE=en_US.UTF-8 \
    PIPENV_VENV_IN_PROJECT=1
