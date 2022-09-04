FROM ubuntu:latest
RUN useradd -m -p Nopassword defuser
USER defuser


FROM maven:3.8.6-jdk-8 AS build
WORKDIR /build
COPY /pom.xml .
COPY src/ /build/src/
RUN mvn -Dmaven.test.skip=true package -Dcheckstyle.skip


FROM openjdk:8-jre-alpine3.9
COPY --from=build /build/target/my-app-1.0.0.jar /app/app.jar
WORKDIR /app
CMD ["java", "-jar", "app/app.jar"]