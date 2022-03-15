## Web-market
Pet-проект, в котором попытался собрать и применить большую часть знаний, полученных по Spring.  
Приложение представляет собой бекэнд для интернет магазина с простейшим фронтом для тестирования.  
Реализована микросервисная архитектура, для упрощения каждый МС сделан отдельным модулем в одном общем проекте.  

#### [API](https://github.com/Loredan15/Web-market/tree/master/api/src/main/java/ru/maxol/web/api)
В данном модуле собраны DTO для обмена информацией между МС.  
Так же свои реализации exception'ов тоже включил сюда.

#### [Auth-service](https://github.com/Loredan15/Web-market/tree/master/auth-service/src/main/java/ru/maxol/web/auth)
MC для авторизации пользователей. Реализация через Jwt-токены.  
Данные о пользователях хранятся в отдельной БД. База разворачивается из скрипта при старте приложения.
##### Использованные технологии: Flyway, H2 db, jjwt, WebSecurity  

#### [Cart-service](https://github.com/Loredan15/Web-market/tree/master/cart-service/src/main/java/ru/maxol/web/cart)
MC отвечает за работу с корзинами. Реализация на базе Redis'a.
Корзины привязаны к UUID на стороне пользователя. Товары можно добавлять, в том числе и без авторизации, а после логина корзины объединяются.
##### Использованные технологии: Redis

#### [Core-service](https://github.com/Loredan15/Web-market/tree/master/core-service/src/main/java/ru/maxol/web/core)
Вся основная логика работы с заказами сосредоточена в данном МС.
Для имитации работы с платежной системой подключена песочница paypal. (Сейчас не работает, т.к. PayPal заблокировал песочницу)  
у МСа есть документация на базе swagger'a.
##### Использованные технологии: PayPal SDK, Swagger, flyway, H2, WebClient, Spring Specification

#### [Front-service](https://github.com/Loredan15/Web-market/tree/master/front-service/src/main)
MC для отрисовки фронта приложения. Упор делается на функционал, поэтому никаких красивостей нет.
##### Использованные технологии: Angular.js, ngStorage

#### [Gateway](https://github.com/Loredan15/Web-market/tree/master/gateway/src/main/java/ru/maxol/web/gateway)
Вся валидация токенов вынесена в отдельный MC. Если пользователь авторизовался, то общение между MCами ведется уже по имени пользователя.
##### Использованные технологии: jakarta, jjwt, Spring Cloud

#### Общие технологии для проекта: Lombok, Spring Boot
