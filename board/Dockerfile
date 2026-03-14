# Use Maven to build the application
FROM maven:3.9.6-eclipse-temurin-17 AS build

WORKDIR /app

# Copy project files
COPY pom.xml .
COPY src ./src

# Build the jar
RUN mvn clean package -DskipTests

# Use lightweight Java runtime
FROM eclipse-temurin:17-jdk-jammy

WORKDIR /app

# Copy jar from build stage
COPY --from=build /app/target/*.jar app.jar

EXPOSE 8080

ENTRYPOINT ["java","-jar","app.jar"]
