---
layout: post
title: OpenDNS &amp; Linux
keywords: linux,dns,opendns,security,безопасность
date: 2011-01-05 00:00
tags:
- linux
- dns
---
Для обеспечения безопасной работы в сети Интернет очень удобно использовать DNS сервера, которые предоставляются OpenDNS. В базовом пакете для домашних пользователей есть возможность защиты от фишинговых сайтов, ботнет-сетей, есть возможность блокирования определенных сетей и что самое главное -- есть возможность контентной фильтрации. То есть идет блокирование ресурсов, замеченных в порнографии, незаконной деятельности и так далее. Уровень фильтрации можно задавать в настройках своей учетной записи.

По идее, использовать базовые возможности серверов очень просто, достаточно только прописать их ip-адреса в настройках системы. А это:

    208.67.222.222
    208.67.220.220

Если же необходимо задавать индивидуальные настройки для определенных своих подсетей, необходимо пройти регистрацию и указать свой ip-адрес, который был выдан провайдером. И если ip-адрес постоянный, то проблем нет никаких. А если ip выдается каждый раз динамически, приходиться использовать специальную программу, которая обновляет значение ip-адреса в учетных данных на сервере. Но эта программа создана специально для Windows. И только недавно узнал о том, что есть возможность использования определенного демона под linux.

Устанавливаем его:

    $ sudo apt-get install ddclient

В Ubuntu сразу после установки будет произведена настройка демона, в процессе которой будут заданы вопросы. На которые следует ответить следующее:

    server=updates.opendns.com
    protocol=dyndns2
    login=opendns_username
    password=opendns_password
    opendns_network_label

Последний пункт -- это имя сети, которое было задано в процессе регистрации на сервере OpenDNS. Рекомендуется так же после настройки добавить в файл <code>/etc/ddclient.conf</code> в самое начало следующую строку:

    ssl=yes

И перезапустить демона:

    $ sudo service ddclient restart

Во время работы демон каждые пять минут проверяет внешний ip-адрес машины и сообщает его на сервер. Просто и удобно!

Задумался теперь над тем, чтобы поставить данный демон себе на роутер Asus WL-500GPv2, чтобы ip-адрес обновлялся не с работающей машины, а непосредственно с самого роутера. И еще интересно будет попробовать включить фильтрацию контента на максимум, то есть блокировать и социальные сети, чаты и файлообменники и многое другое. Интересно посмотреть на тот интернет, что получиться.

На мой взгляд OpenDNS уникальное решение для любой организации. Позволяющее очень просто фильтровать нежелательный контент в сети Интернет.
