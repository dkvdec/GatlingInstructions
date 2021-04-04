Инструкция по использованию Gatling
===================================

<details>
    <summary>Предварительные требования</summary>
    
### Java Version
Gatling поддерживает 64битную версию OpenJDK 8 и OpenJDK 11 с HotSpot.
    
<!-- ###Scala Version
Для Gatling 3.5 требуется Scala 2.13. Для версий Gatling с 3.0 до 3.4 требуется Scala 2.12.
-->
   
### Build Tool
В зависимости от инструмента скачайте необходимую версию демо проекта.
В данном примере мы будем использовать Maven.

[Maven](https://github.com/gatling/gatling-maven-plugin-demo)

[Sbt](https://github.com/gatling/gatling-sbt-plugin-demo)

[Gradle](https://github.com/gatling/gatling-gradle-plugin-demo)

### IDE
Советую использовать IntelliJ IDEA с совместимым Scala Plugin.

</details>

<details>
    <summary>Строение проекта</summary>    

![structure](img/structure.png)
    
1) Проект Demo Maven.
2) Основные ресурсы проекта.
3) Основные настройки:
  - `gatling.conf` основные настройки Gatling.
  - `logback-test.xml` настройки логирования и интерфейсов вывода логов.
4) Директория scala содержит пакеты с тестами. Так же есть несколько дополнительных файлов для совместимости с IDE.
5) Директория для хранения собранного проекта.
6) В директории генерируются отчеты по логу запуска (тот что вы видите в консоли).
7) Настройки Maven.
    
</details> 

<details>
    <summary>Строение симуляции</summary>
    
Обычно симуляция состоит из 4 частей.

### Протокол
Здесь происходит описание протокола в виде объявления URL и заголовков.
Gatling HTTP позволяет загружать тестовые веб-приложения, веб-службы или веб-сайты. Он поддерживает HTTP и HTTPS практически со всеми существующими функциями распространенных браузеров, такими как кеширование, файлы cookie, перенаправление и т. Д.

[Подробнее](https://gatling.io/docs/current/http/http_protocol/)

<details>
    <summary>Пример протокола</summary>
    
```
val httpProtocol = http
    .baseUrl("http://computer-database.gatling.io") // Here is the root for all relative URLs
    .acceptHeader("text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8") // Here are the common headers
    .acceptEncodingHeader("gzip, deflate")
    .acceptLanguageHeader("en-US,en;q=0.5")
    .userAgentHeader("Mozilla/5.0 (Macintosh; Intel Mac OS X 10.8; rv:16.0) Gecko/20100101 Firefox/16.0")
```
</details>
### Сценарий
Сценарий выполнения запросов.
```
val scn = scenario("Scenario Name") // A scenario is a chain of requests and pauses
    .exec(http("request_1")
      .get("/"))
    .pause(7) // Note that Gatling has recorder real time pauses
    .exec(http("request_2")
      .get("/computers?f=macbook"))
    .pause(2)
    .exec(http("request_3")
      .get("/computers/6"))
    .pause(3)
    .exec(http("request_4")
      .get("/"))
    .pause(2)
    .exec(http("request_5")
      .get("/computers?p=1"))
    .pause(670.milliseconds)
    .exec(http("request_6")
      .get("/computers?p=2"))
    .pause(629.milliseconds)
    .exec(http("request_7")
      .get("/computers?p=3"))
    .pause(734.milliseconds)
    .exec(http("request_8")
      .get("/computers?p=4"))
    .pause(5)
    .exec(http("request_9")
      .get("/computers/new"))
    .pause(1)
    .exec(http("request_10") // Here's an example of a POST request
      .post("/computers")
      .formParam("""name""", """Beautiful Computer""") // Note the triple double quotes: used in Scala for protecting a whole chain of characters (no need for backslash)
      .formParam("""introduced""", """2012-05-30""")
      .formParam("""discontinued""", """""")
      .formParam("""company""", """37"""))
```

### Действие
Запрос.
```
.exec(http("request_1")
  .get("/"))
```
```
.exec(http("request_10") // Here's an example of a POST request
  .post("/computers")
  .formParam("""name""", """Beautiful Computer""") // Note the triple double quotes: used in Scala for protecting a whole chain of characters (no need for backslash)
  .formParam("""introduced""", """2012-05-30""")
  .formParam("""discontinued""", """""")
  .formParam("""company""", """37"""))
```

### Инжектор
```

```

</details>

<details>
    <summary>Поключение Influx + Grafana</summary>
    
</details>

Simple showcase of a maven project using the gatling-maven-plugin.

To test it out, simply execute the following command:

    $mvn gatling:test -Dgatling.simulationClass=computerdatabase.BasicSimulation

or simply:

    $mvn gatling:test
