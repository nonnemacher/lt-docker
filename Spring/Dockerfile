FROM openjdk:13-alpine
RUN apk add curl
COPY target/docker-0.0.1-SNAPSHOT.jar /opt/app.jar
CMD java -jar /opt/app.jar