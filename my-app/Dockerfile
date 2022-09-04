FROM ubuntu:latest
RUN useradd -m -p Nopassword defuser
USER defuser


FROM maven:3.8.6-jdk-8 AS build
WORKDIR /build
COPY /pom.xml .
COPY src/ /build/src/
RUN mvn -Dmaven.test.skip=true package -Dcheckstyle.skip


# COPY /my-app/pom.xml /my-app/pom.xml
# COPY /src/ /my-app/src/
# WORKDIR /my-app/
# RUN "mvn -B clean  package --file /my-app/pom.xml"
# CMD 'ls'
# COPY --from=MAVEN_TOOL_CHAIN /tmp/target/wizard*.jar $CATALINA_HOME/webapps/wizard.war


FROM openjdk:8-jre-alpine3.9
COPY --from=build /build/target/my-app-1.0.0.jar /app/app.jar
WORKDIR /app

# WORKDIR /app-art
# COPY ./target/my-app-1.0.0.jar /app-art.jar
CMD ["java", "-jar", "/app-art.jar"]