FROM ubuntu:latest
RUN useradd -m -p Nopassword defuser
USER defuser


FROM maven:3.8.6-jdk-8 AS build
WORKDIR /src
COPY ./src/pom.xml /app
RUN 'ls'
RUN "mvn -B clean  package --file ./my-app/pom.xml"
CMD 'ls'

FROM openjdk:8-jre-alpine3.9
WORKDIR /app
COPY ./target/my-app-1.0.0.jar /app.jar
CMD ["java", "-jar", "/app.jar"]