Wallet Summary
===
В данном репозитории находится решение кейса от Zerion для финала хакатона Definition 19-20 февраля 2022, разработанное командой Comet

Содержание
---
+ [**Инструкция по установке**](#инструкция-по-установке)  
+ [**Проблема**](#проблема)  
+ [**Решение**](#решение)   
+ [**Use Cases**](#use-cases)  
  + [Подключение кошелька](#1-подключение-кошелька)  
  + [Просмотр summary](#2-просмотр-summary)  
  + [Поделиться summary](#3-поделиться-summary)  
+ [**Архитектура**](#архитектура)  
  + [Мобильное приложение](#мобильное-приложение)
  + [Веб-версия](#веб-версия)
  + [Бекенд](#бэкенд)
  + [Что мы сделали за хакатон](#что-мы-сделали-за-хакатон)
+ [**Демонстрация решения**](#демонстрация-решения)
+ [**Направления дальнейшей разработки**](#направления-дальнейшей-разработки)  

Инструкция по установке
---
### С использование Docker
Посмотреть рабочий прототип сайта можно увидеть по ссылке. Однако, в нем нет логики. Чтобы протестировать логику необходимо выполнить следующие действия:

Установить Docker на свой компьютер. Его можно скачать здесь;
Склонировать этот репозиторий любым из способов;
Перейти в директорию с репозиторием и запустить команду docker-compose up или docker-compose up --build. 

Проблема
---
На хакатоне команда выбрала кейс от компании Zerion и работала над новым способом социального взаимодействия в Web3.0. Мы выделили проблему использования DeFi небольшим числом потенциальных пользователей, которые относятся к числу инноваторов. Так что мы стремились расширить базу пользователей путём привлечения ранних последователей в DeFi. Их отличительной чертой является то, что им нужно одобрение экспертов, чтобы начать пользоваться новой технологией. 
![.](https://github.com/Alena-Vasileva/ClientServerApp/blob/master/CustDevStatistics.png)

Решение
---
С помощью интеграции Zerion API мы разработали сервис анализа транзакций пользователя и подведение итогов по его кошельку, которыми можно поделиться в социальных сетях. Такии образом представители ранних последователей, которые следят за профилями инноваторов, захотят повторить успех последних и начнут пользоваться DeFi.

Use Cases 
---

### **(1)** Подключение кошелька
**Название:** Подключение кошелька

**Описание:** Пользователь подключает свой кошелёк, чтобы получить доступ к функционалу системы. 

**Предусловия:** Приложение установлено. 

**Результат:** Кошелёк подключен. 

**Триггер:** Пользователь открывает приложение. 

**Успешный сценарий:**

1. Пользователь вводит токен кошелька и нажимает на кнопку “->”. 

2. Система отправляет запрос на сервер. 

3. Система получает ответ и выводит информацию о подключенном кошельке. 

**Альтернативные сценарии:**  

**(2.1)** *Если поле токена не заполнено, то система выводит сообщение об ошибке.* 

**(3.1)** *Если кошелёк не найден, то система выводит сообщение об ошибке в токене.* 

### **(2)** Просмотр Summary
**Название:** Просмотр Summary

**Описание:** Пользователь просматривает Summary по своему кошельку. 

**Предусловия:** Кошелёк подключен. 

**Результат:** Пользователь просмотрел summary. 

**Триггер:** Пользователь переходит на страницу summary. 

**Успешный сценарий:**

1. Пользователь перешёл на страницу summary. 

2. Система отправляет запрос на сервер. 

3. Система получает ответ и выводит summary по кошельку. 

**Альтернативные сценарии:**  

**(2.1)** *Если кошелёк не подключен, то система выводит сообщение об ошибке и предлагает подключить кошелёк.* 

### **(3)** Поделиться Summary
**Название:** Поделиться Summary

**Описание:** Пользователь отправляет сообщение/делает пост в выбранной социальной сети. 

**Предусловия:** Кошелёк подключен. 

**Результат:** Пользователь отправил сообщение/сделал пост. 

**Триггер:** Пользователь нажимает на кнопку/иконку "Поделиться". 

**Успешный сценарий:**

1. Пользователь нажал на кнопку. 

2. Система предложила одну из установленных социальных сетей / приложений с подобным функционалом в мобильном приложении.
2. Система предложила перейти на ВКонтакте / Facebook / Instagram / Twitter в веб-версии  

3. Пользователь выбран нужное приложение.

4. Система перенаправила его в выбранное приложение

Архитектура
---
### Мобильное приложение
Клиентская часть приложения будет разработана с использованием технологии Xamarin  Forms, которая была выбрана благодаря её кроссплатформенности. При проектировании будет применяться шаблон MVVM, так как он соответствует современным стандартам и рекомендуется [Microsoft](https://docs.microsoft.com/ru-ru/xamarin/xamarin-forms/enterprise-application-patterns/mvvm).
![.](https://github.com/Alena-Vasileva/FarmerCyberAssistant/blob/main/img/Image_2.jpg)
В приложении есть две страницы:
+ Для подключения кошелька по его токену
+ Для просмотра summary по кошельку и возможности им поделиться в социальных сетях (использованы встроенные технологии Android)

Разработка и тестирование проводились на версии Android 10, работоспособность на IOS и других версиях Android не проверялась.

### Веб-версия
Сайт разрабатывался на JavaScript и содержит функционал, аналогичный мобильному приложению:
+ Страница для подключения кошелька по его токену
+ Страница просмотра summary по кошельку и возможности им поделиться в социальных сетях (использованы технологии блока "Поделиться от Яндекса"

### Бекенд
Состоит из сервера подключения к API Zerion и транзитного сервера.

### Что мы сделали за хакатон
+ В мобильном приложении и веб-версии:
  + Подключение кошелька
  + Просмотр summary о кошельке
  + Возможность поделиться summary
+ В бекенде:
  + Подключение к API Zerion
  + Обработка полученной информации по кошельку

Демонстрация решения
---
*В разработке*

Направления дальнейшей разработки
---
*В разработке*
