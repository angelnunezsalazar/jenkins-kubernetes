FROM jenkinsci/jenkins:2.46.2-alpine

ARG JENKINS_SHARE=/usr/share/jenkins/ref

# Install plugins
COPY plugins.txt "${JENKINS_SHARE}/plugins.txt"
RUN /usr/local/bin/install-plugins.sh $(cat "${JENKINS_SHARE}/plugins.txt" | tr '\n' ' ')

# Copy default configuration files
COPY config/* "${JENKINS_SHARE}"

# Remove executors in master
COPY init.groovy.d/* "${JENKINS_SHARE}/init.groovy.d/"

# Configure slaves and their corresponding keys
COPY nodes "${JENKINS_SHARE}/nodes/"
COPY ssh/ "${JENKINS_SHARE}/.ssh/"

# Skip installation Wizard
RUN echo 2.0 > "${JENKINS_SHARE}/jenkins.install.UpgradeWizard.state"