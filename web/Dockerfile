FROM python:3.9

ARG version

RUN mkdir -p /usr/src/app
WORKDIR /usr/src/app

RUN apt-get update && \
    apt-get -y upgrade && \
    DEBIAN_FRONTEND=noninteractive apt-get -y install \
        default-mysql-client \
        libsasl2-dev \
        libssl-dev \
        libldap2-dev && \
    apt-get clean
    
RUN echo "$version"

RUN svn export --force https://github.com/LCBRU/acadex/trunk/ /usr/src/app/
ADD gunicorn.conf /usr/src/app/gunicorn.conf

RUN pip install --no-cache-dir gunicorn
RUN pip install --no-cache-dir -r requirements.txt
