FROM --platform=linux/amd64 maven:3.8.7-eclipse-temurin-17 as builder

COPY src /usr/app/src
COPY pom.xml /usr/app

RUN mvn -f /usr/app/pom.xml clean package

FROM --platform=linux/amd64 eclipse-temurin:17-jdk-alpine

COPY --from=builder /usr/app/target/*.jar /usr/app/app.jar

ENTRYPOINT ["java", "-jar", "/usr/app/app.jar"]