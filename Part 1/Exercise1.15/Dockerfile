FROM openjdk:15-alpine

# Install dependencies
RUN apk add unzip
RUN wget https://services.gradle.org/distributions/gradle-6.8-bin.zip
RUN mkdir /opt/gradle
RUN unzip -d /opt/gradle gradle-6.8-bin.zip
RUN rm gradle-6.8-bin.zip

ENV PATH="/opt/gradle/gradle-6.8/bin:${PATH}"

# Download project
RUN wget https://github.com/Jonne-Sotala/TiraChess/archive/refs/tags/v1.0.zip
RUN unzip v1.0.zip
RUN rm v1.0.zip

WORKDIR /TiraChess-1.0

CMD gradle run --quiet --console plain
