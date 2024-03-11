FROM openjdk:21-bullseye AS builder

WORKDIR /build_dir

COPY .mvn .mvn

COPY src src
COPY mvnw .
COPY pom.xml .

RUN ./mvnw package -Dmaven.test.skip=true


# RUN
FROM openjdk:21-bullseye 

WORKDIR /app

COPY --from=builder /build_dir/target/diovbear-0.0.1-SNAPSHOT.jar app.jar


ENV PORT=8080  INSTANCE_NAME="my Java name " INSTANCE_HASH="HASH"

EXPOSE ${PORT}

HEALTHCHECK --interval=30s --timeout=30s --retries=3  \
CMD curl -s http://localhost:${PORT} > dev/null || exit 1

ENTRYPOINT java -jar app.jar


