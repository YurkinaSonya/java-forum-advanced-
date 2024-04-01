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