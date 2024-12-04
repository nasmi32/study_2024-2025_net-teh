---
## Front matter
lang: ru-RU
title: Лабораторная работа №7
subtitle: Сетевые технологии
author:
  - Мишина А. А.
date: 4 декабря 2024

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

## Цель работы

Получить навыки настройки службы DHCP на сетевом оборудовании для распределения адресов IPv4 и IPv6.

# Выполнение лабораторной работы

# Настройка DHCP в случае IPv4

## Топология сети

![Топология моделируемой сети в GNS3](image/1.png){#fig:1 width=70%}

## VyOS

![Настройка образа VyOS. Вход в систему под созданным пользователем](image/2.png){#fig:2 width=70%}

## Системный пользователь

![Удаление системного пользователя, заданного по умолчанию](image/3.png){#fig:3 width=70%}

## Настройка

![Настройка адресации IPv4 и добавление конфигурации DHCP-сервера](image/4.png){#fig:4 width=70%}

## Статистика

![Просмотр статистики DHCP-сервера и выданных данных](image/5.png){#fig:5 width=70%}

## PC1

![Настройка PC1](image/6.png){#fig:6 width=30%}

## PC1

![Результат настройки PC1](image/7.png){#fig:7 width=70%}

## Статистика

![Просмотр статистики DHCP-сервера и выданных адресов](image/8.png){#fig:8 width=70%}

## Журнал

![Журнал работы DHCP-сервера](image/9.png){#fig:9 width=30%}

## Wireshark

![Захваченные пакеты в Wireshark](image/10.png){#fig:10 width=70%}

# Настройка DHCP в случае IPv6

## Установка

![Установка Kali Linux](image/11.png){#fig:11 width=70%}

## Топология

![Топология моделируемой сети](image/12.png){#fig:12 width=70%}

## Настройка

![Настройка адресации IPv6 на маршрутизаторе](image/13.png){#fig:13 width=60%}

## Router Advertisements

![Настройка RA](image/14.png){#fig:14 width=70%}

## Настройка

![Добавим конфигурации DHCP-сервера](image/15.png){#fig:15 width=70%}

## Результат

![Результат настройки DHCPv6 без отслеживания состояния](image/16.png){#fig:16 width=30%}

## ifconfig

![ifconfig нп PC2](image/17.png){#fig:17 width=40%}

## Проверка

![route на PC2. Пингование маршрутизатора. Проверка настроек DNS](image/18.png){#fig:18 width=70%}

## Получение адреса

![Получение адреса по DHCPv6. Пингование маршрутизатора](image/19.png){#fig:19 width=50%}

## Проверка

![Просмотр выданных адресов](image/20.png){#fig:20 width=70%}

## Wireshark

![Захваченный трафик](image/21.png){#fig:21 width=70%}

## Router Advertisements

![Настройка RA](image/22.png){#fig:22 width=70%}

## Настройка

![Добавление конфигурации DHCP-сервера](image/23.png){#fig:23 width=70%}

## Результат

![Результат настройки DHCPv6 с отслеживания состояния](image/24.png){#fig:24 width=45%}

## ifconfig

![Команда ifconfig в терминале PC3](image/25.png){#fig:25 width=40%}

## Получение адреса

![Получение адреса по DHCPv6](image/26.png){#fig:26 width=70%}

## ifconfig

![Команда ifconfig в терминале PC3](image/27.png){#fig:27 width=70%}

## Проверка

![Команды route, ping, cat](image/28.png){#fig:28 width=70%}

## Проверка

![Выданные адреса](image/29.png){#fig:29 width=70%}

## Wireshark

![Информация по захваченным пакетам](image/30.png){#fig:30 width=70%}

## Выводы

В процессе выполнения лабораторной работы я получила навыки настройки службы DHCP на сетевом оборудовании для распределения адресов IPv4 и IPv6.