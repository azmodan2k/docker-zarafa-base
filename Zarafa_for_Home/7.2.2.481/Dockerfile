FROM ubuntu:14.04
MAINTAINER Tobias Mandjik "webmaster@leckerbeef.de"
# ORIGINAL MAINTAINER Felix Bartels "felix@host-consultants.de"

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update -qq -y \
 && apt-get install -qq -y wget \
 && mkdir -p /root/packages \
 && cd /root/packages \
 && wget -q http://download.zarafa.com/zarafa/drupal/download_platform.php?platform=beta/7.2/7.2.2.481/zcp-7.2.2.481-ubuntu-14.04-x86_64-forhome.tar.gz -O- | tar xz --strip-components=1 \
 && apt-ftparchive packages . | gzip -9c > Packages.gz \
 && echo "deb file:/root/packages /" > /etc/apt/sources.list.d/zarafa.list \
 && apt-get update -qq -y \
 && apt-get install -qq -y apache2  \
 && service apache2 start \
 && apt-get install -qq -y --force-yes php5-mapi  \
 && apt-get install -qq -y --force-yes mysql-server zarafa \
 && rm -rf /root/*.deb \
 && apt-get clean
 

