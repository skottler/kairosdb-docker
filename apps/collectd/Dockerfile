FROM ubuntu:16.04

MAINTAINER Sam Kottler <shk@linux.com>

RUN apt-get update && \
      apt-get install collectd --no-install-recommends -y && \
      apt-get install wget libpython2.7-dev -y

RUN wget -O /usr/lib/collectd/kairosdb_writer.py \
      https://raw.githubusercontent.com/kairosdb/collectd-kairosdb/master/kairosdb_writer.py

ADD collectd.conf /etc/collectd/collectd.conf

RUN service collectd stop
RUN rm -f /etc/init/collectd.conf
RUN rm -f /etc/init.d/collectd

ADD run.sh /usr/local/sbin/run_collectd.sh
ENTRYPOINT ["/usr/local/sbin/run_collectd.sh"]
