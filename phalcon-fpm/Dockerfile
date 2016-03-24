#Comment
FROM centos:7
MAINTAINER <unit.1985@gmail.com> 
RUN echo "start container"
RUN rpm --import http://mirror.centos.org/centos/RPM-GPG-KEY-CentOS-7 && \ 
rpm --import https://mirror.webtatic.com/yum/RPM-GPG-KEY-webtatic-el7 && \
rpm --import https://dl.fedoraproject.org/pub/epel/RPM-GPG-KEY-EPEL-7 && \
rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm && \
rpm -Uvh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm && \
yum update -y && \
yum install -y git php55w-pdo php55w-pecl-redis php55w-pdo php55w-mbstring php55w-pear php55w-fpm php55w-cli git php55w-bcmath php55w-devel pcre-devel gcc make cronie openssl-devel && \
cd /tmp/ && \
git clone --depth=1 git://github.com/phalcon/cphalcon.git && \
cd cphalcon/build && \
./install && \
echo "extension=phalcon.so" > /etc/php.d/phalcon2.ini && \
printf "\n"|pecl install mongo && \
echo "extension=mongo.so" > /etc/php.d/mongo.ini && \

# cron fix
sed -i '/session    required   pam_loginuid.so/c\#session    required   pam_loginuid.so' /etc/pam.d/crond && \

#cleanup
yum erase -y php55w-devel pcre-devel gcc make openssl-devel m4 cpp automake autoconf glibc-headers  \
    openssh-clients perl zlib-devel rsync openssh libselinux-devel libsepol-devel libverto-devel    \
    keyutils-libs-devel kernel-headers glibc-devel && \
yum clean all && \
rm -fr /tmp/*

# for production
CMD ["/bin/bash"]
