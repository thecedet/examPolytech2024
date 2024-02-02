FROM maven:3.9.5-eclipse-temurin-8-alpine as builder

WORKDIR /usr/src/app

COPY . .
RUN mvn clean package -DskipTests=true

FROM eclipse-temurin:8-jre-alpine

COPY --from=builder /usr/src/app/target/*.jar /app.jar

EXPOSE 8448
LABEL maintainer="Clé(ment)"

ENTRYPOINT ["java"]
CMD ["-jar", "/app.jar"]
