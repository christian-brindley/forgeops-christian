FROM gcr.io/forgerock-io/ds/pit1:7.1.0-ce85e1cbb56dc562fba297a5842904bbb512b4e6

# If you want to update any o/s software, or require root access, uncomment the lines below
# Ensure that the /opt/opendj is owned by forgeorock:root
# USER root
# RUN chown -R forgerock:root /opt/opendj
# USER forgerock
WORKDIR  /opt/opendj

COPY --chown=forgerock:root common  /opt/opendj/
COPY --chown=forgerock:root idrepo  /opt/opendj/
COPY --chown=forgerock:root scripts /opt/opendj/scripts

ARG profile_version
RUN bin/setup.sh "$profile_version" && \
    bin/relax-security-settings.sh  && \
    rm bin/setup.sh bin/relax-security-settings.sh
