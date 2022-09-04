FROM ubuntu:latest
RUN useradd -m -p Nopassword defuser
USER defuser

FROM openjdk:8-jre-alpine3.9
WORKDIR /app
RUN ls
COPY ./target/my-app-1.0.0.jar /app.jar
CMD ["java", "-jar", "/app.jar"]