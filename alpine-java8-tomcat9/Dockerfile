FROM anapsix/alpine-java:8_server-jre_unlimited

LABEL maintainer="Marcel Jänicke <inpercima@gmail.com>"

WORKDIR /tmp

ARG VERSION="9.0.12"

RUN apk upgrade --update && \
    apk add --update curl && \
    curl -jkSL -o apache-tomcat.tar.gz http://archive.apache.org/dist/tomcat/tomcat-9/v${VERSION}/bin/apache-tomcat-${VERSION}.tar.gz && \
    tar -xzf apache-tomcat.tar.gz -C /opt && \
    ln -s /opt/apache-tomcat-${VERSION} /opt/apache-tomcat && \
    apk del curl && \
    rm -rf * /var/cache/apk/*

ENV CATALINA_HOME="/opt/apache-tomcat"
ENV PATH="$PATH:$CATALINA_HOME/bin"

EXPOSE 8080

ENTRYPOINT [ "catalina.sh" ]

CMD [ "run" ]
