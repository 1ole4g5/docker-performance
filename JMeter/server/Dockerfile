FROM alpine:3.11.5

LABEL maintainer="my@emai.l"

ADD Dockerfile /server/

ARG JMETER_VERSION="5.2.1"

ENV JMETER_HOME /jmeter/apache-jmeter-${JMETER_VERSION}
ENV JMETER_BIN  ${JMETER_HOME}/bin
ENV MIRROR_HOST https://apache-mirror.rbc.ru/pub/apache/jmeter
ENV JMETER_DOWNLOAD_URL ${MIRROR_HOST}/binaries/apache-jmeter-${JMETER_VERSION}.tgz
# Set default values for allocation of system resources (memory) which will be used by JMeter
ENV Xms 257m
ENV Xmx 513m
ENV MaxMetaspaceSize 1025m

# Install JMeter
RUN mkdir /jmeter \
      && cd /jmeter/ \
      && wget ${JMETER_DOWNLOAD_URL} \
      && tar -xzf apache-jmeter-${JMETER_VERSION}.tgz

ENV PATH $PATH:$JMETER_BIN

# Install OpenJDK-8
RUN apk add --update openjdk8-jre tzdata curl unzip bash \
        && cp /usr/share/zoneinfo/Europe/Moscow /etc/localtime \
        && echo "Europe/Moscow" >  /etc/timezone \
	&& rm -rf /var/cache/apk/*

# Setup JAVA_HOME = not working
ENV JAVA_HOME /usr/lib/jvm/java-1.8-openjdk/
RUN export PATH=$PATH:/usr/lib/jvm/java-1.8-openjdk/bin
RUN export JAVA_HOME=/usr/lib/jvm/java-1.8-openjdk/

WORKDIR ${JMETER_HOME}

# Ports required for JMeter Slaves/Server
EXPOSE 1099 50000

RUN chmod +x ${JMETER_HOME}/bin/*

COPY entrypoint.sh /

RUN chmod +x /entrypoint.sh

ENTRYPOINT ["/entrypoint.sh"]

