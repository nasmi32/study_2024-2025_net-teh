---
## Front matter
title: "Отчёт по лабораторной работе №4"
subtitle: "Дисциплина: Сетевые технологии"
author: "Мишина Анастасия Алексеевна"

## Generic options
lang: ru-RU
toc-title: "Содержание"

## Bibliography
bibliography: bib/cite.bib
csl: pandoc/csl/gost-r-7-0-5-2008-numeric.csl

## Pdf output format
toc: true # Table of contents
toc-depth: 2
lof: true # List of figures
lot: true # List of tables
fontsize: 14pt
linestretch: 1.5
papersize: a4
documentclass: scrreprt
## I18n polyglossia
polyglossia-lang:
  name: russian
  options:
	- spelling=modern
	- babelshorthands=true
polyglossia-otherlangs:
  name: english
## I18n babel
babel-lang: russian
babel-otherlangs: english
## Fonts
mainfont: PT Serif
romanfont: PT Serif
sansfont: PT Sans
monofont: PT Mono
mainfontoptions: Ligatures=TeX
romanfontoptions: Ligatures=TeX
sansfontoptions: Ligatures=TeX,Scale=MatchLowercase
monofontoptions: Scale=MatchLowercase,Scale=0.9
## Biblatex
biblatex: true
biblio-style: "gost-numeric"
biblatexoptions:
  - parentracker=true
  - backend=biber
  - hyperref=auto
  - language=auto
  - autolang=other*
  - citestyle=gost-numeric
## Pandoc-crossref LaTeX customization
figureTitle: "Рис."
tableTitle: "Таблица"
listingTitle: "Листинг"
lofTitle: "Список иллюстраций"
lotTitle: "Список таблиц"
lolTitle: "Листинги"
## Misc options
indent: true
header-includes:
  - \usepackage{indentfirst}
  - \usepackage{float} # keep figures where there are in the text
  - \floatplacement{figure}{H} # keep figures where there are in the text
---

# Цель работы

Установка и настройка GNS3 и сопутствующего программного обеспечения.

# Задание

1. Установить GNS3-all-in-one, GNS3 VM, проверить корректность запуска.

2. Импортировать в GNS3 образ маршрутизатора FRR.

3. Импортировать в GNS3 образ маршрутизатора VyOS.

# Выполнение лабораторной работы

## Установка GNS3

### Установка GNS3-all-in-one

Устанавливаем GNS3 с помощью менеджера пакетов Chocolatey. После запуска графического окна по установке следуем указаниям, нажимая **Next**, принимая соглашение по лицензии, выбирая отображение названия каталога в стартовом меню.
В процессе установки при выборе комплектации отмечаем MSVC Runtime (отмечено по умолчанию), GNS3-Desktop, GNS3-VM, Tools (рис. [-@fig:1]).

![Установка GNS3: выбор комплектации](image/1.png){#fig:1 width=70%}

Далее следуем инструкциям установщика, нажимая **Next**. Дожидаемся установки GNS3 и пакетов, принимаем соглашение по лицензии и завершаем установку  (рис. [-@fig:2]).

![Завершение установки](image/2.png){#fig:2 width=70%}

###  Установка GNS3 VM для VirtualBox

Скачиваем архив с образом виртуальной машины GNS3 VM с официального сайта, распаковываем его. Запустив VirtualBox, выбираем *Файл* -> *Импорт конфигураций*. Указываем месторасположение распакованного образа `GNS3 VM.ova`. В следующем окне в параметрах импорта выбираем в политике MAC-адреса «Сгенерировать новые MAC-адреса всех сетевых адаптеров» и дожидаемся конца импорта (рис. [-@fig:3]). 

![Настройка параметров импорта конфигураций ВМ](image/3.png){#fig:3 width=70%}

Переходим к настройке ВМ. Для этого в VirtualBox выбираем импортированную виртуальную машину и переходим в меню *Машина* -> *Настроить*. Следуем рекомендациям из сообщения об обнаружении неправильных настроек и исправляем ошибки. Проверяем минимальные ресурсы (2048 МБ основной памяти, 2 процессора). Настраиваем вложенную виртуализацию в опции *Система*, вкладка *Процессор*. В графическом интерфейсе нет возможности отметить флажок *Включить Nested VT-x/AMD-V*. Для включения используем команду (рис. [-@fig:4]): vboxmanage modifyvm "GNS3 VM" --nested-hw-virt on.

![Включение вложенной виртуализации](image/4.png){#fig:4 width=70%}

Проверяем, что галочка появилась (рис. [-@fig:5]). 

![Настройка параметров ВМ: включение вложенной виртуализации](image/5.png){#fig:5 width=70%}

Настраиваем сетевой адаптер, убедившись, что выбран режим *Виртуальный адаптер хоста* (рис. [-@fig:6]).

![Настройка параметров ВМ: сетевой адаптер](image/6.png){#fig:6 width=70%}

### Запуск экземпляра GNS3 в VirtualBox

Запускаем виртуальную машину GNS3 VM (рис. [-@fig:7]).

![Запуск GNS3 VM ](image/7.png){#fig:7 width=80%}

Запускаем приложение GNS3 и в мастере настройки выбираем способ работы, настройки локального сервера. Выбираем IP-адрес привязки хоста. После успешного подсоединения появляется окно с итоговыми настройками (рис. [-@fig:8]). 

![Успешное подсоединение к серверу в GNS3](image/8.png){#fig:8 width=80%}

В списке серверов видим GNS3 VM (рис. [-@fig:9]).

![Рабочее пространство GNS3: список серверов](image/9.png){#fig:9 width=80%}

Для выключения GNS3 используем *File* -> *Quit*. Выключается также виртуальная машина.

## Подключение образа оборудования в GNS3

### Добавление образа маршрутизатора FRR

В рабочем пространстве GNS3 на левой боковой панели выбираем просмотр маршрутизаторов, затем нажимаем *+ New template*. В открывшемся окне указываем установку образа с GNS3-сервера, нажимаем  *Next*, оставляем эмулятор по умолчанию. Далее в списке роутеров выбираем FRR (рис. [-@fig:10]) и нажимаем *Install*. Скачиваем и импортируем необходимые файлы, завершаем установку (рис. [-@fig:11]).

![Установка образа устройства FRR](image/10.png){#fig:10 width=70%}

![Скачивание и импорт файлов образа устройства FRR, завершение установки](image/11.png){#fig:11 width=70%}

Для настройки образа щелкаем правой кнопкой на образе и выбираю *Configure template*. В открывшемся окне во вкладке *General settings* в поле *On close* выбираем *Send the shutdown signal (ACPI)* (рис. [-@fig:12]). Во вкладке *HDD* ставим галочку *Automatically create a config disk on HDD* (рис. [-@fig:13]).

![Настройка образа маршрутизатора FRR](image/12.png){#fig:12 width=70%}

![Настройка образа маршрутизатора FRR](image/13.png){#fig:13 width=70%}

### Добавление образа маршрутизатора VyOS

Скачав установочный файл VyOS, переходим в *File* -> *Import appliance* и импортируем его. Далее производим аналогичные настройке FRR шаги, скачиваем необходимые файлы и импортирем их, завершаем установку  (рис. [-@fig:14])

![Установка образа маршрутизатора VyOS: скачивание и импорт файлов](image/14.png){#fig:14 width=70%}

Для настройки образа маршрутизатора VyOS щелкаем правой кнопкой на образе и выбираю *Configure template*. В открывшемся окне во вкладке *General settings* в поле *On close* выбираем *Send the shutdown signal (ACPI)*. Во вкладке *HDD* ставим галочку *Automatically create a config disk on HDD*. Также изменем отображаемый символ устройства, перейдя в *General settings* -> *Symbol* (рис. [-@fig:15]). В рабочем пространстве GNS3 теперь отображаются два разных образа маршрутизаторов рис. ([-@fig:16]).

![Изменение отображаемого символа устройства VyOS](image/15.png){#fig:15 width=70%}

![Добавленные образы маршрутизаторов в GNS3](image/16.png){#fig:16 width=70%}

# Выводы

В результате выполнения работы была произведена установка и настройка GNS3 и сопутствующего программного обеспечения.