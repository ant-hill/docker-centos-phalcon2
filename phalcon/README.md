# docker-centos-phalcon2

Base docker with phalcon2, CentOS 7, php-55 and php-mongo

# How to build

1. Clone repository 
2. Run ` docker build -t ant-hill/phalcon2:0.0.2 . ` 
3. Run ` docker tag ant-hill/phalcon2:0.0.2 ant-hill/phalcon2:latest ` for tagging 
4. Check image by ` docker run --rm ant-hill/phalcon2 php --info ` 
