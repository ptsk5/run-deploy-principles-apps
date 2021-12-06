FROM registry.access.redhat.com/redhat-openjdk-18/openjdk18-openshift AS builder

WORKDIR /app-build

COPY mvnw .
COPY .mvn .mvn

COPY pom.xml .
COPY src src

RUN ./mvnw clean compile package


FROM registry.access.redhat.com/redhat-openjdk-18/openjdk18-openshift

WORKDIR /app-root
COPY --from=builder /app-build/target/greeting-*.jar ./app.jar

EXPOSE 5000

ENTRYPOINT ["java","-jar","./app.jar"]