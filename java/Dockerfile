FROM maven:3.8-openjdk-8 AS builder

WORKDIR /usr/src/app

COPY . .

RUN mvn clean package -DskipTests=true -DstripVersion=true

FROM openjdk:8-jdk

LABEL maintainer="Antoine Laguette"

WORKDIR /usr/src/app

COPY --from=builder /usr/src/app/target/java-*.jar DSjava.jar

EXPOSE 8448

CMD ["java", "-jar", "DSjava.jar"]