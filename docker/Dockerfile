FROM maven:3.6.3-jdk-13 AS BUILDSTAGE

LABEL product=example-ms \
      git=https:https://github.com/Hemantkumar-Chigadani/example-ms \
      author=hemanthic@gmail.com

USER root
WORKDIR /output

COPY . .

RUN mvn clean package

RUN find /output/example-service/target

FROM openjdk:13.0.2-jdk

RUN groupadd -g 1000 appuser && \
    useradd -r -u 1000 -g appuser appuser
USER appuser

WORKDIR /app

COPY --from=BUILDSTAGE /output/example-service/target/example-service-*.jar ./app.jar

RUN ls -l
ENTRYPOINT ["java", "-jar", "app.jar"]
