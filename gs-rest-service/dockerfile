FROM openjdk:8-jre-alpine

# application placed into /opt/app
RUN mkdir -p /opt/app
WORKDIR /opt/app

#Copy files
COPY '/build/libs/*.jar' /opt/app/app.jar

ENV JAVA_OPTS=""
ENV SERVER_PORT 80

EXPOSE ${SERVER_PORT}

HEALTHCHECK --interval=10s --timeout=3s \
	CMD curl -v --fail http://localhost:${SERVER_PORT}/greeting || exit 1

ENTRYPOINT [ "sh", "-c", "java $JAVA_OPTS -Djava.security.egd=file:/dev/./urandom -jar /opt/app/app.jar" ]
