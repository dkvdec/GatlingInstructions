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
    
</details>

<details>
    <summary>Поключение Influx + Grafana</summary>
    
</details>

Simple showcase of a maven project using the gatling-maven-plugin.

To test it out, simply execute the following command:

    $mvn gatling:test -Dgatling.simulationClass=computerdatabase.BasicSimulation

or simply:

    $mvn gatling:test
