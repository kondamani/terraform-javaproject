# Stage 1: Build
FROM maven:3.9.4-eclipse-temurin-17-alpine AS builder

WORKDIR /app
COPY . .
RUN mvn clean package -DskipTests

# Stage 2: Runtime
FROM eclipse-temurin:17-jre-alpine

WORKDIR /opt/app
COPY --from=builder /app/target/spring-boot-web.jar app.jar

EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]
