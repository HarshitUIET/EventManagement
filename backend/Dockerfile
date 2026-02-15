# Use Maven + Java 17 image to build
FROM maven:3.9.6-eclipse-temurin-17-alpine AS build

WORKDIR /app

# Copy everything
COPY . .

# Build the jar
RUN mvn clean package -DskipTests

# -----------------------------

# Use lightweight Java image to run
FROM eclipse-temurin:17-jdk-alpine

WORKDIR /app

# Copy jar from build stage
COPY --from=build /app/target/*.jar app.jar

# Expose port (Spring default)
EXPOSE 8080

# Run application
CMD ["java", "-jar", "app.jar"]
