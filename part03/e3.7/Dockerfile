FROM openjdk:8-alpine AS build-env

WORKDIR /usr/src/app

COPY . . 

RUN ./mvnw package

FROM openjdk:8-jre-alpine

EXPOSE 8080

WORKDIR /usr/src/app

COPY --from=build-env /usr/src/app /usr/src/app

RUN adduser -D user

USER user

CMD ["java","-jar","./target/docker-example-1.1.3.jar"]
