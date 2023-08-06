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
![ip_a][https://github.com/RSafin12/neoflex-linux-rsafin-task1/blob/main/Screenshots/docker_%20screens/3_network.png]

## Задание 4