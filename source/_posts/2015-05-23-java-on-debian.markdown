---
layout: post
title: How To Install Java on Debian
date: 2015-05-23 14:51
tags:
- debian
- java
- soft
- tips
---

Потребовалось установить на сервер Java. Стал рассматривать варианты:

1. Установка из репозитория.
1. Установка из неофициального репозитория.
1. Установка версии с сайта Oracle.

Первый вариант меня не устроил ввиду того, что устанавливается OpenJDK, и все бы ничего, но при этом ставится максимум 7-ая версия и при этом тянется еще масса дополнительных зависимостей, которые я использовать не планировал.

Второй вариант оказался более продвинутым, так как дает больше возможностей, но добавлять сторонние репозитории мне не хотелось, поэтому остановился на третьем варианте: который давал мне возможность полного контроля.

**Нюанс**: дистрибутивы Java размещаются на серверах Oracle ([Download Page](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html "Java SE DEvelopment Kit 8 Downloads")), где перед загрузкой необходимо принять лицензионное соглашение. Для того, чтобы провести загрузку непосредственно со своего сервера, необходимо использовать команду:

    wget --no-check-certificate -c --header "Cookie: oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jdk/8u45-b14/jdk-8u45-linux-x64.tar.gz

Ссылку можно взять на указанной выше странице загрузки.

После загрузки необходимо распаковать полученный файл в предполагаемую директорию:

    tar zxf jdk-8u45-linux-x64.tar.gz -C /target/directory

Архив после распаковки можно удалить. В директории `/target/directory` будет создана поддиректория `jdk1.8.0_45`. При необходимости ее можно перенести или переименовать.

Единственное, что осталось сделать, это задать переменные среды. В зависимости от того, какая командная оболочка используется на компьютере и от того, для всех пользователей будет устанавливаться Java или только для определенных, вносятся изменения в файлы:

1. Для всех пользователей в файле `/etc/profile`
1. Для определенного пользователя в файле `~/.bash_profile`, либо в `~/.bashrc`, в зависимости от того, какой файл используется для конфигурирования bash.

Достаточно определить две переменные:

    export JAVA_HOME=/target/directory/jdk1.8.0_45
    export PATH=$PATH:$JAVA_HOME/bin

Переменная `JAVA_HOME` указывает на директорию нашей установки. Теперь осталось только применить нашу конфигурацию, для этого используем команду:

    source ~/.bash_profile

И теперь можно проверять, все ли у нас работает:

    $ java -version
    java version "1.8.0_45"
    Java(TM) SE Runtime Environment (build 1.8.0_45-b14)
    Java HotSpot(TM) 64-Bit Server VM (build 25.45-b02, mixed mode)

Вот так просто мы получили на своем сервере рабочую Java, не устанавливая при этом массу ненужных зависимостей.

При этом получили еще одно преимущество: таким образом можно установить одновременно несколько версий Java, и перед запуском программы просто переопределять переменную `JAVA_HOME`, указывая, где располагается требуемая версия.
