# Дипломный проект профессии «Тестировщик»

Дипломный проект представляет собой автоматизацию тестирования комплексного сервиса.

## Документы
* [План автоматизации](https://github.com/ViktoriyaBelova/Diploma_QA_Belova/blob/main/Plan.md)
* [Отчет по итогам тестирования](https://github.com/ViktoriyaBelova/Diploma_QA_Belova/blob/main/Report.md)
* [Отчет по итогам автоматизированного тестирования](https://github.com/ViktoriyaBelova/Diploma_QA_Belova/blob/main/Summary.md)

На локальном компьютере заранее должны быть установлены IntelliJ IDEA и Docker.

## Процедура запуска авто-тестов:

**1.** Склонировать на локальный репозиторий [Дипломный проект](https://github.com/ViktoriyaBelova/Diploma_QA_Belova).

**2.** Запустить Docker Desktop

**3.** Открыть проект в IntelliJ IDEA

**4.** Запускаем контейнеры в Docker. Для этого в терминале IntelliJ Idea вводим команду docker compose up -d

**5.** Запустить целевое приложение с помощью команды в терминале:

    для postgresgl:
     java "-Dspring.datasource.url=jdbc:postgresql://localhost:5432/app" -jar artifacts/aqa-shop.jar

     для mySQL: 
    java "-Dspring.datasource.url=jdbc:mysql://localhost:3306/app" -jar artifacts/aqa-shop.jar 

**6.** Открыть вторую вкладку терминала

**7.** Во втором терминале запустить тесты командой:

    для mySQL:
    ./gradlew clean test -DurlDB="jdbc:mysql://localhost:3306/app"

    для postgresgl: 
    ./gradlew clean test -DurlDB="jdbc:postgresql://localhost:5432/app"

**8.** Создать отчёт Allure и открыть в браузере с помощью команды в терминале:

    ./gradlew allureServe

**9.** Для завершения работы allureServe выполнить команду:

    Ctrl+C

**10.** Для остановки работы контейнеров выполнить команду:

    docker-compose down
