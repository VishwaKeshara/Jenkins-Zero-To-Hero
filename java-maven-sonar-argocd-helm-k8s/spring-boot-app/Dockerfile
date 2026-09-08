# Build stage
FROM maven:3.8-openjdk-11 AS builder
WORKDIR /build
COPY pom.xml .
COPY src ./src
RUN mvn clean package -DskipTests

# Runtime stage
FROM adoptopenjdk/openjdk11:alpine-jre
WORKDIR /opt/app
COPY --from=builder /build/target/spring-boot-web.jar app.jar
ENTRYPOINT ["java","-jar","app.jar"]
