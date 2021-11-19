FROM ibm-zcon-server:beta

# customise server.xml via dropins
COPY --chown=1001:0 src/main/liberty/config /config/configDropins/defaults

# install war
COPY --chown=1001:0 build/libs /config/dropins
