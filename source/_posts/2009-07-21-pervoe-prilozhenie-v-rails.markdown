---
layout: post
title: Первое приложение в Rails
keywords: rails,tutorial
date: 2009-07-21 00:00
tags:
- rails
---
Сегодня я покажу, как создать первую заготовку в Rails.

Для начала установим веб-сервер Thin. Этот веб-сервер, как и Mongrel, написан на Ruby, но является более быстрым и масштабируемым. Thin позволяет быстро создавать кластеры приложений и в отличие от Mongrel позволяет работать в несколько потоков. В возможностях веб-сервера я могу ошибаться, потому как только сегодня с ним познакомился и особо глубоко в него не погружался...

Для установки thin выполняем команду:

    $ sudo gem install thin

У меня данная команда закончилась ошибкой. Требуется более новая версия Raсk. Если у вас появиться подобная ошибка, просто выполняем команду:

    $ sudo gem install rack

После чего повторяем предыдущую команду для установки thin.

Теперь нам необходимо создать наше первое приложение на Rails. Переходим в какую-нибудь директорию, в которой будем проводить свои разработки и выполняем команду:

    $ rails myapplication

На что будет создана директория myapplication,  в которой будет содержаться несколько подкаталогов и куча файлов. Каркас веб-приложения готов. Попробуем запустить его. Для этого переходим в нашу директорию и запускаем thin:

    $ cd myapplication
    $ thin -a 127.0.0.1 start

В качестве параметров у thin можно передавать и адрес, с которого он будет слушать сеть и работающий порт и много чего еще, справка по параметрам доступна по команде:

    $ thin --help

Теперь открываем браузер и переходим по адресу <a href="http://127.0.0.1:3000">127.0.0.1:3000</a>, именно порт 3000 используется по умолчанию. После открытия страницы можно прочитать краткую инструкцию о том что делать дальше...

Просто? Не то слово! Каркас нашего приложения готов!
