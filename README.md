Инструкция по использованию Gatling
===================================

<details>
    <summary>Предварительные требования</summary>
    
###Java Version
Gatling поддерживает 64битную версию OpenJDK 8 и OpenJDK 11 с HotSpot.
    
<!-- ###Scala Version
Для Gatling 3.5 требуется Scala 2.13. Для версий Gatling с 3.0 до 3.4 требуется Scala 2.12.
-->
   
###Build Tool
В зависимости от инструмента скачайте необходимую версию демо проекта.
В данном примере мы будем использовать Maven.

[Maven](https://github.com/gatling/gatling-maven-plugin-demo)

[Sbt](https://github.com/gatling/gatling-sbt-plugin-demo)

[Gradle](https://github.com/gatling/gatling-gradle-plugin-demo)

####IDE
Советую использовать IntelliJ IDEA с совместимым Scala Plugin.

</details>

<details>
    <summary>Строение проекта</summary>    

![structure](img/structure.png)
    
    1)
    2)
    3)
    4)
    5)
    6)
    7)
    
</details> 

Simple showcase of a maven project using the gatling-maven-plugin.

To test it out, simply execute the following command:

    $mvn gatling:test -Dgatling.simulationClass=computerdatabase.BasicSimulation

or simply:

    $mvn gatling:test
