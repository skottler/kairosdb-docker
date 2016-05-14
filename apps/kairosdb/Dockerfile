FROM ubuntu:14.04

MAINTAINER Sam Kottler <shk@linux.com>

RUN apt-get update && \
      apt-get install software-properties-common -y

RUN add-apt-repository ppa:webupd8team/java
RUN echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | debconf-set-selections

RUN apt-get update && \
      apt install oracle-java8-installer oracle-java8-set-default -y

RUN wget -O /var/cache/kairosdb_1.1.1-1_all.deb \
      https://github.com/kairosdb/kairosdb/releases/download/v1.1.1/kairosdb_1.1.1-1_all.deb

RUN dpkg -i /var/cache/kairosdb_1.1.1-1_all.deb

ADD kairosdb.properties /opt/kairosdb/conf/kairosdb.properties

ADD run.sh /usr/local/sbin/run_kairosdb.sh

ENTRYPOINT ["/usr/local/sbin/run_kairosdb.sh"]
