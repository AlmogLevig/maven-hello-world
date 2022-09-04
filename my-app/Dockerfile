FROM openjdk:8-jre-alpine3.9
WORKDIR /app
COPY target/original-my-app-1.0.0.jar /app/
RUN useradd -m -p Nopassword defuser
USER defuser
CMD ["java", "-jar", "/app.jar"]