FROM ubuntu:trusty
MAINTAINER Gitlab.com

RUN apt-get update ;\
    apt-get -y install openssh-server supervisor software-properties-common rsync ;\
    rm -rf /var/lib/apt/lists/* ;\
    mkdir /var/run/sshd

#password is vagrant
RUN useradd -m -p '$6$UFLdXsV4$hnP4J2l8w02eCoj7ogsQZ0wdEImAKtzIoQqmrNLEXkyI1UsuPPofdpf4DMViq4QPdFVOz0yekQ35lgaFUB6SF/' -s /bin/bash vagrant

COPY assets /

RUN chown -R vagrant:vagrant /home/vagrant; \
    chmod 600 /home/vagrant/.ssh/authorized_keys

CMD supervisord -c /etc/supervisord.conf
EXPOSE 22
