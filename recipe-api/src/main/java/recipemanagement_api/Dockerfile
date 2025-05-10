FROM maven:3.8.6-openjdk-17-slim AS build
WORKDIR /app
COPY . .
# Make the Maven wrapper executable (sometimes necessary)
RUN chmod +x ./mvnw
RUN ./mvnw clean package -DskipTests

FROM eclipse-temurin:17-jre-alpine
WORKDIR /app
COPY --from=build /app/target/*.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","/app/app.jar"]
