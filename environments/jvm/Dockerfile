FROM maven:3.5-jdk-8 as BUILD
COPY src /usr/src/myapp/src
COPY pom.xml /usr/src/myapp
RUN mvn -f /usr/src/myapp/pom.xml clean package

FROM openjdk:8-jdk-alpine
VOLUME /tmp
COPY --from=BUILD /usr/src/myapp/target/env-java-0.0.1-SNAPSHOT.jar /app.jar
ENTRYPOINT java ${JVM_OPTS} -Djava.security.egd=file:/dev/./urandom -jar /app.jar --server.port=8888
EXPOSE 8888