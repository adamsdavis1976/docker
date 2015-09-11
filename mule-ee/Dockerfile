# Dockerizing Mule EE
# Version:  0.1
# Based on: java (Trusted Java from http://java.com)

FROM                    java:8-jre
MAINTAINER              Adam Davis

# MuleEE installation:

# This line can reference either a web url (ADD), network share or local file (COPY)
COPY                    ./mule-ee-distribution-standalone-3.7.1.tar.gz /opt/

WORKDIR                 /opt
RUN                     tar -xzvf /opt/mule-ee-distribution-standalone-3.7.1.tar.gz
RUN                     ln -s mule-enterprise-standalone-3.7.1 mule
RUN                     rm -f mule-ee-distribution-standalone-3.7.1.tar.gz

# Copy the license key, keep the license conditions in mind!
WORKDIR                 /opt/mule-enterprise-standalone-3.7.1
RUN                     rm -Rf .mule
ADD                     ./mule-ee-license.lic /opt/mule-enterprise-standalone-3.7.1/
RUN                     bin/mule -installLicense conf/mule-ee-license.lic
RUN                     rm -f conf/mule-ee-license.lic
RUN                     rm -Rf apps/default*


# Configure external access:

# Mule remote debugger
EXPOSE  5000

# Mule JMX port (must match Mule config file)
EXPOSE  1098

# Mule MMC agent port
EXPOSE  7777

# Expose Test Service port 
EXPOSE  8081

# Environment and execution:

ENV             MULE_BASE /opt/mule
WORKDIR         /opt/mule-enterprise-standalone-3.7.1/

CMD             /opt/mule/bin/mule