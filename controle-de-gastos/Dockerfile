FROM maven:3.9.6-eclipse-temurin-21 AS build
WORKDIR /app
COPY . .
RUN chmod +x mvnw || true
RUN ./mvnw -B -ntp clean package -DskipTests || mvn -B -ntp clean package -DskipTests
FROM eclipse-temurin:21-jdk
WORKDIR /app
COPY --from=build /app/target/app.jar app.jar
ENTRYPOINT ["java", "-jar", "app.jar"]
