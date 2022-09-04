FROM ubuntu:latest
RUN useradd -m -p Nopassword defuser
USER defuser


FROM maven:3.8.6-jdk-8 AS build
COPY my-app/pom.xml /my-app/pom.xml
COPY src my-app/src/
WORKDIR /my-app/
RUN "mvn -B clean  package --file /my-app/pom.xml"
CMD 'ls'
# COPY --from=MAVEN_TOOL_CHAIN /tmp/target/wizard*.jar $CATALINA_HOME/webapps/wizard.war


FROM openjdk:8-jre-alpine3.9
WORKDIR /app-art
COPY ./target/my-app-1.0.0.jar /app-art.jar
CMD ["java", "-jar", "/app-art.jar"]