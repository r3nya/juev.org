---
layout: post
title: Использование тегов в Jekyll
description: 
keywords: jekyll, tags, web
gplus: https://plus.google.com/116661482374124481456/posts/aeK7vt9huCa
published: true
date: 2013-04-20 15:29
tags:
- jekyll
---
Так уж получилось, что Jekyll, как впрочем и Octopress не имеют поддержки тегов. Для того, чтобы добавить теги на свой сайт мне приходилось использовать отдельные Rake-задачи, каждая из которых выполняла свою определенную задачу: одна формировала список статей по каждому тегу, а вторая готовила код для вставки на страницу облака тегов.

Наконец нашел отдельное расширение, которое позволило значительно упростить работу с тегами в Jekyll. Называется оно [pattex/jekyll-tagging][1].

[1]: https://github.com/pattex/jekyll-tagging "pattex/jekyll-tagging"

Для установки расширения добавляем следующую строку в `Gemfile`:

    gem 'jekyll-tagging'

И затем устанавливаем с помощью команды:

    bundle install

После чего прописываем в файл `_plugins/ext.rb` строчку:

    require "jekyll/tagging"

Все готово к началу работы. Осталось только в `_config.yml` определить настройки расширения и затем создать шаблон страницы с тегами.

Добавляем в файл `_config.yml` две строки:

    tag_page_layout: tag_page
    tag_page_dir: tags

Первая отвечает за имя файла с шаблоном страницы, на которой будут перечислятся статьи под определенным тегом, а вторая отвечает за имя директории, в которой теги будут располагаться.

Теперь в директории `_layouts` создаем файл `tag_page.html`, пример кода данной страницы есть на странице расширения, я же использовал следующий вариант:

{% raw %}
    ---
    layout: default
    title: "Tag page"
    syntax-highlighting: yes
    ---
    <h1 class="title">Tagged by {{ page.tag }}</h1>
    {% for post in page.posts %}<div class="list"><a href="{{ post.url }}">{{ post.title }}</a></div>{% endfor %}
{% endraw %}

Страницы теперь будут генерироваться в том виде, который мы ожидаем. И остается только добавить облако тегов. Для этого можно использовать отдельную страницу, создав в корне сайта файл `tags.html` со следующим содержимым:

{% raw %}
    ---
    layout: default
    title: Теги
    permalink: tags.html
    ---
    <h1 class="title">Теги</h1>
    <div id="tag-cloud">
      {{ site | tag_cloud }}
    </div>
{% endraw %}

При генерации облака тегов будут использоваться предопределенные стили оформления, которые нужно будет добавить в свой CSS-файл, чтобы задать необходимые размеры шрифтов, интервалы. За это будет отвечать классы от `.set-1` (минимальная частота) до `.set-5` (максимальная частота использования тега).

Так же, если это необходимо, можно игнорировать определенные теги при генерации, для этого в `_config.yml` достаточно поместить строку:

    ignored_tags: [tags,to,ignore]

При написании статьи, чтобы добавить тег, достаточно в yaml-заголовок в начале файле добавить следующие строки:

    tags:
    - jekyll
    - еще_один_тег
    - и_так_далее
    ---

или

    tags: [jekyll,еще_один_тег,и_так_далее]

Результат использования данного расширения можно увидеть на странице моего сайта: [Теги](/tags.html "Теги").
