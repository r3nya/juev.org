---
layout: post
title: Размещение подкаста в интернете
keywords: amazon,hosting,internet,services,podcast,хостинг
date: 2010-03-14 00:00
tags:
- amazon
- hosting
- internet
- services
---
Нет, я не собираюсь пока записывать подкасты. Я просто хочу рассмотреть вариант создания собственной "площадки" для ведения подкастов.

Основная сложность заключается в скорости отдачи файлов сервером. Поэтому часто при использовании бесплатных площадок возникают проблемы с получением потока. Мы же воспользуемся Amazon для хранения файлов и еще одним сервисом для создания плеера.

Amazon позволяет без проблем отдавать файлы в режиме реального времени, практически не думая о нагрузке на сервер. При этом стоимость использования его ресурсов минимальна (о чем я уже указывал). Для начала работы создадим отдельный Bucket, который будет предназначен только для хранения файлов. Для работы с Amazon воспользуемся программой CloudBerry Explorer, о которой я уже рассказывал в предыдущих статьях.

<img class="aligncenter size-full wp-image-954" title="create_bucket" src="https://static.juev.org/2010/03/create_bucket.png" alt="" width="340" height="225" />

Какой использовать сервер -- зависит только от вас. Европейский чуть дороже, но в то же время он самый быстрый для России, так как расположен ближе. Теперь, так как все файлы, которые мы будем загружать, должны быть доступны всем, задаем для Bucket права доступа:

<img class="aligncenter size-full wp-image-955" title="ACL" src="https://static.juev.org/2010/03/ScreenShot001.png" alt="" width="381" height="391" />

<a href="https://static.juev.org/2010/03/ScreenShot002.png"><img class="aligncenter size-medium wp-image-956" title="ScreenShot002" src="https://static.juev.org/2010/03/ScreenShot002-300x181.png" alt="" width="300" height="181" /></a>

Для All Users ставим галочку в столбце Read. После чего файлы данного Bucket будут по умолчанию доступны для чтения всем пользователям. Теперь загружаем нужный нам файл на сервер и получаем ссылку на него (для этого щелкаем правой кнопкой мыши на нужном файле и выбираем пункт меню Web URL):

<a href="https://static.juev.org/2010/03/web-url.png"><img class="aligncenter size-medium wp-image-957" title="web-url" src="https://static.juev.org/2010/03/web-url-300x242.png" alt="" width="300" height="242" /></a>

Никаких дополнительных параметров тут устанавливать не нужно. Просто копируем текст ссылки
для дальнейшего использования. И теперь нам необходимо использовать данную ссылку для
того, чтобы создать плеер, с помощью которого будем играть наш podcast. Я выбрал для этой
цели сервис <a href="http://muzicons.com" rel="nofollow">muzicons.com</a>

Необходимо пройти процедуру регистрации для того, чтобы иметь доступ к своим созданным плеерам в дальнейшем. После чего переходим по ссылке "Создать музикон" и заполняем поля формы:

<a href="https://static.juev.org/2010/03/muzicons.png"><img class="aligncenter size-medium wp-image-958" title="muzicons" src="https://static.juev.org/2010/03/muzicons-290x300.png" alt="" width="290" height="300" /></a>

Иконку и внешний вид, цвет выбираем по вкусу, главное здесь -- это указать URL нашего файла, который мы получили на предыдущем шаге во втором пункте формы. После нажатия на кнопку Ok, в разделе "Результат" можно проверить то, что получилось. При нажатии на кнопку "Воспроизвести" вы должны услышать звуки своего подкаста.

По сути данный сервис еще должен предоставлять статистику прослушиваний, но сколько я не пытался, постоянно натыкался на нули. Хотя прекрасно знаю, что мой мини-подкаст прослушали минимум несколько человек.

Если вы знаете другой сервис по созданию веб-плееров, подскажите пожалуйста? Буду благодарен!

Ну а для полноценного подкастинга, конечно же лучше всего воспользоваться сервисами типа <a href="http://rpod.ru" rel="nofollow">rpod.ru</a>.
