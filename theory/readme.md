# Теория Spring Boot 3 и Java 17

## Лекции

Лекции представлены в формате мастер-класса по определённым темам. К каждой лекции прилагаются ссылки, которые
студенту рекомендовано изучать после просмотра лекции.

<h4>Spring Boot 3 - Hello World</h4>

[Лекция на youtube](https://youtu.be/AfbWXUqYrpc) <br>
Создание проекта и пример контроллеров для загрузки файлов. Забегающий вперёд материал для самостоятельного
освоения технологии перед курсом. <br>
Ссылки: <br>
https://spring.io/guides/gs/uploading-files <br>
https://www.baeldung.com/spring-file-upload <br>

<h4>Spring Boot 3 - Core</h3>

[Лекция на youtube](https://youtu.be/dawLHBQlmek) <br>
Основа Spring Boot - коротко о компонентах, как они создаются в спринге, как связываются, как создаются конфигурации. <br>
Ссылки по теме: <br>
https://habr.com/ru/articles/490586/ <br>

<h4>Spring Boot 3 - Web</h4>

[Лекция на youtube](https://youtu.be/CeitFLb5_-Q) <br>
Написание рест-контроллеров в спринге. <br>
Ссылки по теме: <br>
https://spring.io/guides/gs/rest-service <br>
https://www.baeldung.com/spring-boot-configure-tomcat <br>
https://www.baeldung.com/exception-handling-for-rest-with-spring <br>
Последняя ссылка полезна в плане обработки ошибок и выдачи клиенту понятных сообщений и
http-статусов, т.к. по дефолту ваши исключения будут всегда на контроллере превращаться
в 500 статус. Обращаем внимание на ControllerAdvice 

<h4>Spring Boot 3 - JPA, лекция 1</h4>

[Лекция на youtube](https://youtu.be/RbuL8Wk3wHE) <br>
Первые шаги с ORM. <br>
Ссылки по теме: <br>
https://docs.spring.io/spring-data/jpa/reference/jpa.html - здесь можно 
читать хоть все подразделы, подробная документация <br>
https://www.baeldung.com/the-persistence-layer-with-spring-data-jpa - здесь краткое описание технологии<br>

<h4>Minio и Spring Boot</h4>

> Лекция с прошлого года, где spring boot и java были ниже версиями, однако, сам подход не изменился

[Лекция на youtube](https://youtu.be/KHIXDJKVoRk) <br>
Ссылки по теме<br>
Как поднять сам minio: https://min.io/docs/minio/container/index.html <br>

## Материалы для изучения

- Liquibase
  - https://contribute.liquibase.com/extensions-integrations/directory/integration-docs/springboot/using-springboot-with-maven/
  - https://www.baeldung.com/liquibase-refactor-schema-of-java-app <br>
    _Тут разделы: 1, 2, 4 и 5 интересны_
- Spring Security
  - https://www.baeldung.com/get-user-in-spring-security
  - https://www.baeldung.com/spring-security-method-security
  - https://struchkov.dev/blog/ru/jwt-implementation-in-spring/

## Установка Apache Kafka

Можно воспользоваться удобным способом поднятия кафки через docker-compose:
<details>
  <summary>Развернуть, docker-compose.yml</summary>

```yaml
version: "3"

services:
  kafka:
    image: 'bitnami/kafka:latest'
    container_name: kafka
    ports:
      - '9092:9092'
    environment:
      - KAFKA_CFG_NODE_ID=0
      - KAFKA_CFG_PROCESS_ROLES=controller,broker
      - KAFKA_CFG_LISTENERS=PLAINTEXT://:9092,CONTROLLER://:9093,EXTERNAL://:9094
      - KAFKA_CFG_ADVERTISED_LISTENERS=PLAINTEXT://localhost:9092,EXTERNAL://localhost:9094
      - KAFKA_CFG_LISTENER_SECURITY_PROTOCOL_MAP=CONTROLLER:PLAINTEXT,EXTERNAL:PLAINTEXT,PLAINTEXT:PLAINTEXT
      - KAFKA_CFG_CONTROLLER_QUORUM_VOTERS=0@kafka:9093
      - KAFKA_CFG_CONTROLLER_LISTENER_NAMES=CONTROLLER
      - KAFKA_CFG_MESSAGE_MAX_BYTES=33554432

  akhq:
    image: tchiotludo/akhq
    environment:
      AKHQ_CONFIGURATION: |
        akhq:
          connections:
            docker-kafka-server:
              properties:
                bootstrap.servers: "kafka:9092"
              connect:
                - name: "connect"
                  url: "http://connect:8083"
    ports:
      - 8080:8080
    links:
      - kafka
```
</details>

Если кафка физически будет расположена на иной машине, то в KAFKA_CFG_ADVERTISED_LISTENERS вместо localhost указывать
IP этой машины.

На 8080 порту, как указано в примере docker.compose.yml, поднимается GUI, в котором можно смотреть топики кафка 
и отправлять сообщения в них