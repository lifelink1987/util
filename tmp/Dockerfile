# Life-link
# version 0.1

from            ubuntu:12.04
maintainer      Andrei Neculau <andrei.neculau@gmail.com>

# basic
env             DEBIAN_FRONTEND noninteractive
run             echo "deb http://archive.ubuntu.com/ubuntu precise main universe multiverse" >> /etc/apt/sources.list
run             apt-get dist-upgrade -y
run             apt-get update --fix-missing
run             apt-get update -y
run             apt-get upgrade -y
run             apt-get install -y aptitude build-essential curl dialog emacs git lynx nano vim
# locale
run             apt-get install locales
run             locale-gen en_US en_US.UTF-8
run             update-locale LANG=en_US.UTF-8
#run             dpkg-reconfigure locales
# keep upstart from complaining
run             dpkg-divert --local --rename --add /sbin/initctl
run             ln -s /bin/true /sbin/initctl

# mysql
run             apt-get install mysql-server mysql-server-5.5 mysql-client
run             sed -i -e"s/^bind-address\s*=\s*127.0.0.1/bind-address = 0.0.0.0/" /etc/mysql/my.cnf

# php
run             apt-get install php-pear php5 php5-cli php5-common php5-curl php5-fpm php5-gd php5-imagick php5-imap php5-intl php5-mcrypt php5-memcache php5-ming php5-mysql php5-ps php5-pspell php5-recode php5-snmp php5-sqlite php5-tidy php5-xmlrpc php5-xsl
run             sed -i -e "s/;cgi.fix_pathinfo=1/cgi.fix_pathinfo=0/g" /etc/php5/fpm/php.ini
run             sed -i -e "s/upload_max_filesize\s*=\s*2M/upload_max_filesize = 100M/g" /etc/php5/fpm/php.ini
run             sed -i -e "s/post_max_size\s*=\s*8M/post_max_size = 100M/g" /etc/php5/fpm/php.ini
run             sed -i -e "s/;daemonize\s*=\s*yes/daemonize = no/g" /etc/php5/fpm/php-fpm.conf
run             find /etc/php5/cli/conf.d/ -name "*.ini" -exec sed -i -re 's/^(\s*)#(.*)/\1;\2/g' {} \;

# nginx
run             apt-get install nginx
#run             sed -i -e"s/keepalive_timeout\s*65/keepalive_timeout 2/" /etc/nginx/nginx.conf
#run             sed -i -e"s/keepalive_timeout 2/keepalive_timeout 2;\n\tclient_max_body_size 100m/" /etc/nginx/nginx.conf
#run             echo "daemon off;" >> /etc/nginx/nginx.conf
run             rm /etc/nginx/sites-available/default
add             ./nginx-site.conf /etc/nginx/sites-available/lifelink

# apache
# run             apt-get install apache2 apache2.2-common libapache2-mod-php5
# run             a2enmod rewrite
# run             a2dissite default
# add             ./apache.conf /etc/apache2/sites-available/lifelink
# run             a2ensite lifelink

expose 80
