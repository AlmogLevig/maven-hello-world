FROM ubuntu:latest
RUN useradd -m -p Nopassword defuser

FROM openjdk:8-jre-alpine3.9
# WORKDIR /app
COPY ./my-app/target/my-app-1.0.0.jar /app.jar
USER defuser
CMD ["java", "-jar", "/app.jar"]