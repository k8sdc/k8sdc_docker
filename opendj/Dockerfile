FROM java:8

MAINTAINER des@drury-family.com

WORKDIR /opt

RUN curl http://maven.forgerock.org/repo/snapshots/org/forgerock/opendj/opendj3-server-dev/3.0.0-SNAPSHOT/opendj3-server-dev-3.0.0-20150211.174712-258.zip -o opendj.zip

ADD k8sdc.ldif /opt/opendj/k8sdc.ldif

RUN unzip opendj.zip && ./opendj/setup --cli -p 389 --ldapsPort 636 --enableStartTLS --generateSelfSignedCertificate \
    --ldifFile /opt/opendj/k8sdc.ldif --baseDN "dc=k8sdc,dc=io" -h localhost --rootUserPassword password --acceptLicense --no-prompt \
    && rm opendj.zip && /opt/opendj/bin/stop-ds

ADD run.sh /opt/opendj/run.sh

EXPOSE 389 636 4444

CMD  ["/opt/opendj/run.sh"]
