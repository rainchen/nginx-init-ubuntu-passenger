# nginx-init-ubuntu-rails #

Nginx init script for passenger default build on ubuntu.

Original Author: [Jason Giedymin](http://jasongiedymin.com) <jasong -_at_- apache -=dot=- org>


## Install ##

    cd /etc/init.d
    sudo wget https://raw.githubusercontent.com/rainchen/nginx-init-ubuntu-passenger/master/nginx
    sudo update-rc.d nginx defaults
    sudo chmod +x nginx
    sudo service nginx start

## Nginx Vhost Tools ##

### install ###

    cd /opt/nginx/sbin/
    sudo wget https://raw.githubusercontent.com/rainchen/nginx-init-ubuntu-passenger/master/nginx-enable-site

    sudo wget https://raw.githubusercontent.com/rainchen/nginx-init-ubuntu-passenger/master/nginx-disable-site

    sudo chmod +x nginx-*

    sudo mkdir /opt/nginx/conf/sites-available

    sudo mkdir /opt/nginx/conf/sites-enabled

    # add to /opt/nginx/conf/nginx.conf
    http {
        ...
        include /opt/nginx/conf/sites-enabled/*;
    }


### usage ###

created 

    $ sudo vim /opt/nginx/conf/sites-available/example.com

enable site
    $ /opt/nginx/sbin/nginx-enable-site example.com
    /opt/nginx/conf/sites-enabled/example.com
    Enabled 'example.com'


disable site

    $ /opt/nginx/sbin/nginx-disable-site example.com
    /opt/nginx/conf/sites-enabled/example.com
    Disabled 'example.com'


check nginx config

    $ sudo service nginx configtest
    nginx: the configuration file /opt/nginx/conf/nginx.conf syntax is ok
    nginx: configuration file /opt/nginx/conf/nginx.conf test is successful

restart nginx

    $ sudo service nginx restart


## Notes ##
It is recommended to install [Nginx](http://nginx.net/) by doing a full compile & build. Not all package repositories keep their branches updated. For security it is your duty to maintain a good working environment and thus includes all interfacing applications.

A great resource is the [Nginx Wiki](http://wiki.nginx.org/).

## Contributions ##
_Contributions are welcome!_
