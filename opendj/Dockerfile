FROM java:8
MAINTAINER des@drury-family.com

ENV OPENDJ_URL=http://maven.forgerock.org/repo/snapshots/org/forgerock/opendj/opendj3-server-dev/3.0.0-SNAPSHOT/opendj3-server-dev-3.0.0-20150211.174712-258.zip

WORKDIR /opt

RUN curl $OPENDJ_URL -o opendj.zip; \
    unzip opendj.zip; \
    rm opendj.zip

ADD k8sdc.ldif /tmp/k8sdc/k8sdc.ldif
ADD run.sh /opt/opendj/run.sh

EXPOSE 389 636 4444

CMD  ["/opt/opendj/run.sh"]

