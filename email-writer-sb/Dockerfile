# Build stage
FROM maven:3.9.12-eclipse-temurin-17 AS build
WORKDIR /app

# Copy project files
COPY pom.xml .
COPY .mvn/ .mvn
COPY mvnw .
COPY src ./src

# Build with Maven inside container
RUN ./mvnw clean package -DskipTests

# Runtime stage
FROM eclipse-temurin:17-jdk
WORKDIR /app

COPY --from=build /app/target/*.jar app.jar

EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]
