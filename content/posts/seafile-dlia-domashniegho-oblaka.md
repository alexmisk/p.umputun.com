---
title: "Seafile для домашнего облака"
date: 2013-03-26T14:20:40-05:00
draft: false
tags: ["технические темы"]
---

После того, как я распробовал Dropbox и особенно после того, как все мы стали понимать, что Dropbox [далеко не идеален](/p/2011/04/28/msg-/) и личные данные там держать опасно, возникли разные мысли и в том числе о том, как поднять свой собственный, личный заменитель/дополнитель Dropbox. Время от времени а пробовал разные подобные системы, разной степени готовности и дружественности и убеждался, что все это типичное не то.

Либо эта штука нереально тормозила, либо глючила, либо обе эти проблемы одновременно. После выхода свежей, "сильно переработанной и улучшенной" 5й версии [ownCloud](http://owncloud.org), которая была не легче 4й и даже менее стабильной, я было уже сел писать сам такую штуку, как натолкнулся на [Seafile](http://seafile.com/en/home/), a точнее говоря, меня навели добрые люди в комментариях к [радио-т](http://www.radio-t.com).

Еще одна идея фикс была запустить свой заменитель dropbox на [одном из моих RPi](http://p.umputun.com/p/2012/12/27/raspberry-pi/). То, как ownCloud работал на RPi достойно всякого порицания и вырывания рук разработчиков из тех мест, где эти руки по недоразумению выросли. Хотя удивляться тут особенно и нечего - и на более настоящем компьютере ownCloud не блистал (мягко говоря) стабильность и скоростью.

Однако, вернемся к нашему герою и сразу дадим вывод: Seafile хорош, очень хорош, где-то близко к прекрасен. Есть [версии сервера](http://seafile.com/en/download/) для Linux вообще и для RPi в частности. Установив версию серверной части на RPi и проделав ряд простых и подробно документированных шагов по установке и конфигурированию, я получил полностью рабочий сервер хранения, доступа и синхронизации за пару минут. Процесс действительно очень и очень простой и доступен всякому, кого не пугает командная строка линукса.

![](/images/posts/Seafile.jpg)
Кстати, чтоб попробовать Seafile в деле вовсе не надо устанавливать сервер. На [cloud.seafile.com](http://cloud.seafile.com) дают доступ (5г максимум) к такому серверу и это точно та система, что бы получите при установке у себя. Конечно, для личного сервера никаких 5г ограничений нет и вы можете там хранить сколько влезет на диск сервера.

В принципе, после установки сервера вы уже вполне можете это использовать. Единственный способ работы с компьютера будет через web интерфейс. Способ вполне рабочий, особенно если надо что-то быстро посмотреть или загрузить. Кстати, интерфейс хотя и очень лаконичный, но вполне функционалый. Все то, что вы ожидаете тут будет работать. К файлам тех форматов, что можно показать, будет показываться превью, загрузка/выгрузка доступна как отдельных файлов, так и каталогов и даже целых библиотек. Библиотеки это в seafile такие разделы. Переводя на язык Dropbox – каждая библиотека это свой отдельный dropbox к которому не нужен дополнительный экаунт.

![](/images/posts/Seafile-hist.jpg#floatright)
Seafile поддерживает историю/версионность. В отличии от Dropbox, степень и глубина этой истории может регулироваться на уровне библиотеки и позволяет задать то, что вам удобно. На практике это весьма полезная возможность и позволяет достаточно гибко управлять размером таких исторических версий в зависимости от вашей ситуации, размера диска на сервере и степенью паранойи. Кстати, при желании можно ограничить и максимальный размер того, что пользователь займет на диске. Насколько я понимаю, это работает на уровне пользователя а не конкретной библиотеки.

И да, эта штука поддерживает многих пользователей, т.е. нечто вроде dropbox для рабочих групп. В Seafile есть возможность управлять пользователями, объединять их в группы, делиться файлами в группах и даже обмениваться некими сообщениями. Я об этом мало что могу сказать, т.к. в моем случае есть только один user и никакая компания мне тут пока не нужна. Однако, судя по обсуждениям в их форуме, подобное использование черезвычайно популярно в мелких и даже крупных группах и организациях.


![](/images/posts/seafile-rpi.jpg#floatright)
Теперь что касается клиентской части. Она есть, и ее много разной. Есть клиенты под все, что захотите и даже под мобильные платформы. Клиент для Mac, который я использую, обеспечивает синхорнизацию тех библиотек, которые вам хочется иметь локально. Клиент простой и очень легкий. В отличии от dropbox и многих прочих, его работу трудно заметить по внезапному завыванию вентиляторов. Даже в режиме самого активной работы seafile клиент очень и очень скромный в использовании системных ресурсов. Кстати, и по серверным ресурсам даже на очень скромном RPi Seafile ведет себя превосходно. Даже в пиках загрузка CPU не прыгает выше 60-70% и памяти оно ест совсем не много (я не замечал более 5% на 512M RPi).

Синхронизация клиентов работает, в отличии от прочих заменителей dropbox, т.е. работает всегда, надежно и быстро. У меня сейчас около 50G данных хранится и синхорнизируется через Seafile и никаких проблем я не наблюдал. Работает это на 3х маках и работает просто отлично. Скорость в районе 5Мбайт/с и, я подозреваю, что тут упирается в специфику реализации ethernet через usb на RPi, тот же usb на котором сидит внешний диск.

Интерфейс к клиенту несколько странный. Он совмещает забавную иконку в меню с управлением через браузер.

![](/images/posts/SeafileClient.jpg#floatright}
При всей его гиковости все, что надо тут есть. Можно посмотреть текущий статус, можно добавить новую библиотеку, можно перезапустить, в чем пока не было нужды. Справедливости ради, способ добавления новой библиотеки вызывает по началу вопрос "а как тут добавлять?". Явного места нигде не видно, однако я догадался даже без чтения инструкции - в web интерфейсе надо кликнуть на Download библиотеки и вас перекинет в web интерфейс клиента, где спросит куда и как синхронизировать. Непривычно - да, но вполне понятно и удобно.

Теперь о дополнительных возможностях. Тут есть шаринг, но только через web интерфейс. Насколько я понимаю, прямых ссылок (т.е. ссылок прямо на файл) в один клик оно не дает и ссылка ведет на страницу с пред-просмотром и Download, но при необходимости эту ссылку легко извлечь.

![](/images/posts/seafile-finder.jpg#floatright)
После установки клиент пытается интегрироваться в Finder, но у него это получается не сразу. На всех 3х моих маках надо было перезапустить клиента, чтоб Finder стал показывать библиотеки и прятать служебную информацию. Никакой глубокой интеграции с Finder тут нет (пока?) только самое базовое.

Пару слов о процессе синхронизации. Я не изучал как оно там сделано, но есть впечатление, что синхронизция происходит последовательно. Т.е. если вы добавили файлы, то они будут загружаться один за другим. При этом, если появились новые файлы на сервере, клиент их не начнет брать пока не закончит текущую загрузку. Трудно сказать, насколько это недостаток, но наверное при работе с далеким сервером может захотеться параллельной и неблокирующей работы. Лично мне это неважно, в локальной сети это практически незаметно. Еще одна специфика в том, что результат синхорнизации доставляется не по частям, а одним ударом. В dropbox при появлении нескольких новых или обновленных файлов они будут появляться на клиенте один за другим. Тут иначе - вначале Seafile доставит все и только потом покажет. На практике это немного непривычно (ничего, ничего и вдруг все), но никакого дискомфорта это у меня не вызывает.

Подводя итог - это хорошая, правильная программа и она ближе всего к тому, что мне надо для организации локального "облачного" хранилища. Последние 3 дня я гоняю Seafile в хвост и гриву и процентов на 80% убежден в том, что Seafile станет моей основной системой домашнего облака.