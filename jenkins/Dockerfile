FROM jenkinsci/jenkins:2.9

COPY custom.groovy /usr/share/jenkins/ref/init.groovy.d/custom.groovy
COPY plugins.txt /usr/share/jenkins/plugins.txt

RUN /usr/local/bin/plugins.sh /usr/share/jenkins/plugins.txt
RUN echo 2.9 > /usr/share/jenkins/ref/jenkins.install.UpgradeWizard.state
RUN echo 2.9 > /usr/share/jenkins/ref/jenkins.install.InstallUtil.lastExecVersion