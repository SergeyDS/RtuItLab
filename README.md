# RtuItLab
Проект релизован в качестве демонстрации работы микросервисов, контейнеров docker, брокера сообщений RabbitMQ. 

Схема взаимодействия микросервисов в проекте.  
![Scheme](https://user-images.githubusercontent.com/19944637/169509046-83fa02c4-4c2a-48ea-be8e-8ba8f723057d.png)
Порты, на которых располагаются микросервисы:
* Identity - 7001
* Purchases - 7002
* Shops - 7003
* Factories - 7004
* RabbitMQ - 15672 & 5672
* ApiGateway - 5000
## Стек проекта:
* Asp Net Core Web Api
* [Entity Framework Core](https://docs.microsoft.com/ru-ru/ef/core/)
* Unit Tests
* [Docker](https://www.docker.com/)
* [RabbitMQ](https://www.rabbitmq.com/)
* [Api Gateway (Ocelot)](https://ocelot.readthedocs.io/en/latest/features/configuration.html)
## Содержание
1. [Функциональность проекта](#Функциональность-проекта)
2. Описание микросервисов
   1. [Identity](#Identity) 
   2. [Purchases](#Purchases)  
   3. [Shops](#Shops)  
   4. [Factories](#Factories)  
3. [Базы данных](#Базы-данных)
4. [RabbitMQ](#RabbitMQ)
5. [API Gateway (Ocelot)](#Api-Gateway-Ocelot)
6. [Docker](#Docker)
7. [UnitTests](#UnitTests)
#
### Функциональность проекта
Возможности клиента:
1. На микросервисе Identity:
  - зарегистрироваться
  - авторизоваться
  - узнать информацию о себе
2. На микросервисе Purchases:
  - посмотреть список своих покупок
  - добавить в этот список самописную покупку
  - узнать детальную информацию по конкретной покупке
  - изменить информацию по покупке
3. На микросервисе Shops:
  - посмотреть список магазинов
  - посмотреть список товаров в магазине
  - посмотреть список продуктов по категории в магазине
  - купить список товаров в одном магазине

Микросервис Factories в свою очередь каждые 20 секунд пополняет "склады" магазинов. А микросервис Shops при покупке клиентом товаров добавляет покупку в список
покупок пользователя на микросервисе Purchases.
### Микросервисы

Каждый микросервис выполняет определённую роль. Рассмотрим их отдельно.

В каждом из микросервисов, кроме Factories используется swagger. 
