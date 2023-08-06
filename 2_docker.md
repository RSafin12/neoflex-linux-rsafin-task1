## Задание 1  
```
FROM maven:3.6-jdk-8-alpine AS build

WORKDIR /app

COPY pom.xml .
COPY src ./src
RUN mvn -e -B package

FROM tomcat:8.5
COPY --from=build /app/target/demo.war /usr/local/tomcat/webapps/demo.war

RUN echo "export JAVA_OPTS=\"-Dapp.env=staging\"" > /usr/local/tomcat/bin/setenv.sh

EXPOSE 8080

CMD ["catalina.sh", "run"]
```
![demo](https://github.com/RSafin12/neoflex-linux-rsafin-task1/blob/main/Screenshots/docker_%20screens/1_demo.png)
![logs](https://github.com/RSafin12/neoflex-linux-rsafin-task1/blob/main/Screenshots/docker_%20screens/1_inter.png)
![inter](https://github.com/RSafin12/neoflex-linux-rsafin-task1/blob/main/Screenshots/docker_%20screens/1_logs.png)

## Задание 2
```bash
docker run \
--name test_db \
--mount src=/tmp,dst=/var/lib/postgresql/data,type=bind \
--env POSTGRES_PASSWORD=1234pass \ 
postgres:13 env
```
## Задание 3
`docker run -it -d --network host -- name iowa alpine`
![ip_a](https://github.com/RSafin12/neoflex-linux-rsafin-task1/blob/main/Screenshots/docker_%20screens/3_network.png)

## Задание 4
Dockerfile_prod  
```
FROM golang:1.17.0-alpine3.13 AS builder

RUN apk update && apk add git
ENV USER=appuser
ENV UID=10001

RUN adduser \
--disabled-password \
--gecos "" \
--home "/nonexistent" \
--shell "/sbin/nologin" \
--no-create-home \
--uid "${UID}" \
"${USER}"

WORKDIR /go/delivery

COPY . .

RUN go mod download
RUN go mod verify
RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -ldflags="-w -s" -o /go/bin/main

FROM scratch

COPY --from=builder /etc/passwd /etc/passwd
COPY --from=builder /etc/group /etc/group
COPY --from=builder /go/bin/main /go/bin/main

USER appuser:appuser

EXPOSE 9001
ENTRYPOINT ["/go/bin/main"]
```

Dockerfile_dev
```FROM golang:1.17.0-alpine3.13 AS build

RUN apk update && apk add git
#WORKDIR /go/delivery
WORKDIR /
COPY ./go.mod .
COPY ./main.go .

RUN go mod download
RUN go mod verify
RUN CGO_ENABLED=0 go get -ldflags "-s -w -extldflags '-static'" github.com/go-delve/delve/cmd/dlv
RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -ldflags="-w -s" -o ./app

FROM scratch
COPY --from=build /go/bin/dlv /dlv
COPY --from=build /app app

EXPOSE 9001
ENTRYPOINT [ "/go/bin/main","/dlv" , "--listen=:9001", "--headless=true", "--api-version=2", "--accept-multiclient", "exec", "/app"]
# ENTRYPOINT ["/go/bin/main"]
```
