#+++++++++++++++++++++++++++++++++++++++
# Dockerfile for webdevops/typo3-solr:6.0
#    -- automatically generated  --
#+++++++++++++++++++++++++++++++++++++++

FROM solr:6.3.0

LABEL maintainer=info@webdevops.io \
      vendor=WebDevOps.io \
      io.webdevops.layout=8 \
      io.webdevops.version=1.5.0

ENV TERM="xterm" \
    LANG="C.UTF-8" \
    LC_ALL="C.UTF-8"

USER root

ADD baselayout.tar /

RUN apt-update \
    && apt-install net-tools \
    && generate-dockerimage-info \
    && mkdir /tmp/solr \
    && wget -O/tmp/solr/extension.tar.gz "https://github.com/TYPO3-Solr/ext-solr/archive/6.0.1.tar.gz" \
    && cd /tmp/solr \
    && tar --strip 1 -zxf /tmp/solr/extension.tar.gz \
    && rm -rf /opt/solr/server/solr \
    && mv /tmp/solr/Resources/Private/Solr/ /opt/solr/server/solr \
    && mkdir -p /opt/solr/server/solr/data \
    && chown -R solr:solr /opt/solr/server/solr \
    && chmod 755 /opt/solr/server/solr \
    && cd / \
    && rm -rf /tmp/solr \
    && docker-image-cleanup

USER solr

VOLUME ["/opt/solr/server/solr/data"]
