 # 1. Build stage
FROM maven:3.8.6-openjdk-17 AS build
WORKDIR /app

# copy pom and src
COPY pom.xml .
COPY src ./src

RUN ./mvnw clean package -DskipTests

# 2. Runtime image
FROM eclipse-temurin:17-jdk
WORKDIR /app

COPY --from=build /app/target/*.jar app.jar

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "app.jar"]
