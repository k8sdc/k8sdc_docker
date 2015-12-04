FROM java:8

MAINTAINER des@drury-family.com

WORKDIR /opt

RUN curl https://forgerock.org/djs/opendjrel.js?948497823 | grep -o "http://.*\.zip" | tail -1 | xargs curl -o opendj.zip

ADD k8sdc.ldif /opt/opendj/k8sdc.ldif

RUN unzip opendj.zip && ./opendj/setup --cli -p 389 --ldapsPort 636 --enableStartTLS --generateSelfSignedCertificate \
    --ldifFile /opt/opendj/k8sdc.ldif --baseDN "dc=k8sdc,dc=io" -h localhost --rootUserPassword password --acceptLicense --no-prompt \
    && rm opendj.zip && /opt/opendj/bin/stop-ds

ADD run.sh /opt/opendj/run.sh

EXPOSE 389 636 4444

CMD  ["/opt/opendj/run.sh"]
