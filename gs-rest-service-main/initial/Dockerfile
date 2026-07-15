# Multi-stage Dockerfile for building and running the Spring Boot service

FROM maven:3.9.4-eclipse-temurin-17 AS builder
WORKDIR /workspace

# Copy project files and build the fat jar
COPY . /workspace
RUN mvn -B -DskipTests package

FROM eclipse-temurin:17-jre AS runtime
WORKDIR /app

# Copy the built jar from the builder stage (artifact name created by the build)
COPY --from=builder /workspace/target/rest-service-0.0.1-SNAPSHOT.jar /app/app.jar

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "/app/app.jar"]
