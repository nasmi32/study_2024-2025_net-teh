---
## Front matter
lang: ru-RU
title: Лабораторная работа №3
subtitle: Сетевые технологии
author:
  - Мишина А. А.
date: 12 октября 2024

## i18n babel
babel-lang: russian
babel-otherlangs: english

## Formatting pdf
toc: false
toc-title: Содержание
slide_level: 2
aspectratio: 169
section-titles: true
theme: metropolis
header-includes:
 - \metroset{progressbar=frametitle,sectionpage=progressbar,numbering=fraction}
 - '\makeatletter'

 - '\makeatother'
---

## Цели и задачи

- Изучение посредством Wireshark кадров Ethernet, анализ PDU протоколов транспортного и прикладного уровней стека TCP/IP.

# Выполнение лабораторной работы

# MAC-адресация

## ipconfig

![Команда ipconfig](image/1.png){#fig:1 width=45%}

## ipconfig /all

![Команда ipconfig /all](image/2.png){#fig:2 width=45%}

#  Анализ кадров канального уровня в Wireshark

## Wireshark

![Запуск захвата трафика](image/3.png){#fig:3 width=70%}

## Пинг

![Пинг шлюза по умолчанию](image/4.png){#fig:4 width=70%}

## Фильтр ICMP

![Кадр ICMP - эхо-запрос: информация о длине кадра, типе Ethernet и MAC-адресах](image/5.png){#fig:5 width=70%}

## Фильтр ICMP

![Кадр ICMP - эхо-ответ: информация о длине кадра, типе Ethernet, MAC-адресах](image/6.png){#fig:6 width=80%}

## Фильтр ARP

![Кадр ARP: информация о длине кадра, типе Ethernet, MAC-адресах](image/7.png){#fig:7 width=50%}

## Пинг

![Пинг сайта www.yandex.ru](image/8.png){#fig:8 width=80%}

## Фильтр ICMP

![Запрос протокола ICMP](image/9.png){#fig:9 width=80%}

## Фильтр ICMP

![Ответ протокола ICMP](image/10.png){#fig:10 width=80%}

## Фильтр ICMP

![Кадр ARP - эхо-ответ](image/20.png){#fig:20 width=50%}

# Анализ протоколов транспортного уровня в Wireshark

## http://info.cern.ch/

![Кадр http - запрос](image/11.png){#fig:11 width=70%}

## http://info.cern.ch/

![Кадр http - ответ](image/12.png){#fig:12 width=70%}

## Фильтр dns

![Кадр dns - запрос](image/13.png){#fig:13 width=70%}

## Фильтр dns

![Кадр dns - ответ](image/14.png){#fig:14 width=50%}

## Фильтр quic

![Кадр quic - запрос](image/15.png){#fig:15 width=70%}

# Анализ handshake протокола TCP в Wireshark

## handshake

![Первая ступень handshake TCP](image/16.png){#fig:16 width=70%}

## handshake

![Вторая ступень handshake TCP](image/17.png){#fig:17 width=70%}

## handshake

![Третья ступень handshake TCP](image/18.png){#fig:18 width=70%}

## График потока

![График потока](image/19.png){#fig:19 width=70%}

## Вывод

- В результате выполнения работы были изучены посредством Wireshark кадры Ethernet, произведен анализ PDU протоколов транспортного и прикладного уровней стека TCP/IP.