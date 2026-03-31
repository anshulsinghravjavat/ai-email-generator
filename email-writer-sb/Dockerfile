 Copy Maven config and source
COPY pom.xml .
COPY .mvn/ .mvn
COPY mvnw .
COPY src ./src

# Build the jar
RUN ./mvnw clean package -DskipTests

# Run stage
FROM eclipse-temurin:17-jdk
WORKDIR /app

# Copy the built jar into container
COPY --from=build /app/target/*.jar app.jar

# Expose Spring Boot default port
EXPOSE 8080

# Start Spring Boot app
ENTRYPOINT ["java", "-jar", "app.jar"]
