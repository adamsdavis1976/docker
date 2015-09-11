# Dockerizing Mule MMC
# Version:  0.1
# Based on:  dockerfile/java (Trusted Java from http://java.com)

FROM                    tomcat:6-jre8
MAINTAINER              Adam Davis

# Mule MMC installation:

# This line can reference either a web url (ADD), network share or local file (COPY)
COPY                    ./mmc-console-3.7.0.war $JENKINS_HOME/webapps

WORKDIR                 /opt

# Configure external access:

# Mule remote debugger
EXPOSE  5000

# Mule JMX port (must match Mule config file)
EXPOSE  1098
