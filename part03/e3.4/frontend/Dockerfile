FROM ubuntu:18.04

EXPOSE 5000

WORKDIR = /usr/app/src

COPY . . 

ENV REACT_APP_BACKEND_URL=http://localhost:8080

RUN apt-get update && apt-get install -y curl && \
    curl -sL https://deb.nodesource.com/setup_14.x | bash - && \ 
    apt-get install -y nodejs && \
    npm install && \
    npm run build && \
    npm install -g serve && \
    ls | grep -v build | xargs rm -rf && \
    apt-get purge -y --auto-remove curl && \
    rm -rf /var/lib/apt/lists/* && \
    useradd -m user

USER user

CMD ["serve", "-s", "-l", "5000", "build"]
