---
## Front matter
lang: ru-RU
title: Лабораторная работа №1
subtitle: Сетевые технологии 
author:
  - Мишина А. А.
date: 13 сентября 2024

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

- Целью данной работы является изучение методов кодирования и модуляции сигналов с помощью высокоуровнего языка программирования Octave. Определение спектра и параметров сигнала. Демонстрация принципов модуляции сигнала на примере аналоговой амплитудной модуляции. Исследование свойства самосинхронизации сигнала.

# Выполнение лабораторной работы

# Построение графиков в Octave

## График y1

![Листинг файла plot_sin.m](image/1.png){ #fig:001 width=60% }

## График y1

![График функций y1 на интервале −10; 10](image/2.png){ #fig:002 width=60% }


## Проверка файлов

![Файлы .eps, .png](image/3.png){ #fig:003 width=60% }


## Графики у1 и у2

![Листинг файла plot_sin_cos.m](image/4.png){ #fig:004 width=60% }

## Графики у1 и у2

![График функций y1 и y2 на интервале −10; 10](image/5.png){ #fig:005 width=60% }

# Разложение импульсного сигнала в частичный ряд Фурье

## Меандр через косинус

:::::::::::::: {.columns align=center}
::: {.column width="70%"}

- Создадим новый сценарий meandr.m. В кодe зададим начальные значения. Вычислим амплитуду гармоник и заполним массивы гармоник и элементов ряда. Далее задаём массив значений гармоник массив элементов ряда. Также экспортируем полученный график в файл в формате .png 

:::
::: {.column width="30%"}

![Листинг файла meandr.m](image/6.png){ #fig:006 width=100% }

:::
::::::::::::::

## Результат

![Меандр через косинусы](image/7.png){ #fig:007 width=60% }

## Меандр через синус

![Листинг файла meandr.m](image/8.png){ #fig:008 width=40% }

## Результат

![Меандр через синусы](image/9.png){ #fig:009 width=60% }

# Определение спектра и параметров сигнала

## Сигналы разной частоты

![Листинг файла spectre.m](image/10.png){ #fig:010 width=40% }

## Результат

![Графики сигналов разной частоты](image/11.png){ #fig:011 width=60% }


## Спектры сигналов

![Листинг файла spectre.m](image/12.png){ #fig:012 width=30% }

## График спектра

![График спектра синусоидальных сигналов](image/13.png){ #fig:013 width=60% }

## Скорректированный график

![Исправленный график спектров синусоидальных сигналов](image/14.png){ #fig:014 width=60% }

## Спектр суммы

![Листинг файла spectre_sum.m](image/15.png){ #fig:015 width=30% }

## Сумма

![Суммарный сигнал](image/16.png){ #fig:016 width=60% }

## Спектр суммы

![Спектр суммарного сигнала](image/17.png){ #fig:017 width=60% }

# Амплитудная модуляция

## Амплитудная модуляция

![Листинг файла am.m](image/18.png){ #fig:018 width=30% }

## Результат

![Сигнал и огибающая при амплитудной модуляции](image/19.png){ #fig:019 width=60% }

## Результат

![Спектр сигнала при амплитудной модуляции](image/20.png){ #fig:020 width=60% }

# Кодирование сигнала. Исследование свойства самосинхронизации сигнала

## Подготовка

- В рабочем каталоге создадим каталог coding и в нём файлы main.m, maptowave.m, unipolar.m, ami.m, bipolarnrz.m, bipolarrz.m, manchester.m, diffmanc.m, calcspectre.m.

- В окне интерпретатора команд проверяем, установлен ли пакет расширений signal: pkg list. Так как он не установлен, то устанавливаем его: pkg list -forge и pkg install control signal 

![Проверка правильности установки пакета signal](image/21.png){ #fig:021 width=50% }

## Файл main.m

![Задаем входные кодовые последовательности](image/22.png){ #fig:022 width=60% }

## Файл main.m

![Вызовы функций для посторения модуляций кодированных сигналов кодовой последовательности data](image/23.png){ #fig:023 width=30% }

## Файл main.m

![Вызовы функций для посторения модуляций кодированных сигналов кодовой последовательности data_sync](image/24.png){ #fig:024 width=30% }

## Файл main.m

![Вызовы функций для посторения графиков спектров](image/25.png){ #fig:025 width=30% }


## Файл maptowave.m

![Листинг файла maptowave.m](image/26.png){ #fig:026 width=60% }

## Файл unipolar.m

![Листинг файла unipolar.m](image/27.png){ #fig:027 width=60% }

## Файл ami.m

![Листинг файла ami.m](image/28.png){ #fig:028 width=60% }

## Файл bipolarnrz.m

![Листинг файла bipolarnrz.m](image/29.png){ #fig:029 width=60% }

## Файл bipolarrz.m

![Листинг файла bipolarrz.m](image/30.png){ #fig:030 width=60% }

## Файл manchester.m

![Листинг файла manchester.m](image/31.png){ #fig:031 width=60% }

## Файл diffmanc.m

![Листинг файла diffmanc.m](image/32.png){ #fig:032 width=60% }

## Файл calcspectre.m

![Листинг файла calcspectre.m](image/33.png){ #fig:033 width=60% }

## График кодированного сигнала

![Униполярное кодирование](image/34.png){ #fig:034 width=60% }

## График кодированного сигнала

![Кодирование AMI](image/35.png){ #fig:035 width=60% }

## График кодированного сигнала

![Кодирование NRZ](image/36.png){ #fig:036 width=60% }

## График кодированного сигнала

![Кодирование RZ](image/37.png){ #fig:037 width=60% }

## График кодированного сигнала

![Манчестерское кодирование](image/38.png){ #fig:38 width=60% }

## График кодированного сигнала

![Дифференциальное манчестерское кодирование](image/39.png){ #fig:039 width=60% }

## Иллюстрация свойства самосинхронизации

![Униполярное кодирование: нет самосинхронизации](image/40.png){ #fig:040 width=60% }

## Иллюстрация свойства самосинхронизации

![Кодирование AMI: самосинхронизация при наличии сигнала](image/41.png){ #fig:041 width=60% }

## Иллюстрация свойства самосинхронизации

![Кодирование NRZ: нет самосинхронизации](image/42.png){ #fig:042 width=60% }

## Иллюстрация свойства самосинхронизации

![Кодирование RZ: есть самосинхронизация](image/43.png){ #fig:043 width=60% }

## Иллюстрация свойства самосинхронизации

![Манчестерское кодирование: есть самосинхронизация](image/44.png){ #fig:044 width=60% }

## Иллюстрация свойства самосинхронизации

![Дифференциальное манчестерское кодирование: есть самосинхронизация](image/45.png){ #fig:045 width=60% }

## Графики спектра сигнала

![Униполярное кодирование: спектр сигнала](image/46.png){ #fig:046 width=60% }

## Графики спектра сигнала

![Кодирование AMI: спектр сигнала](image/47.png){ #fig:047 width=60% }

## Графики спектра сигнала

![Кодирование NRZ: спектр сигнала](image/48.png){ #fig:048 width=60% }

## Графики спектра сигнала

![Кодирование RZ: спектр сигнала](image/49.png){ #fig:049 width=60% }

## Графики спектра сигнала

![Манчестерское кодирование: спектр сигнала](image/50.png){ #fig:050 width=60% }

## Графики спектра сигнала

![Дифференциальное манчестерское кодирование: спектр сигнала](image/51.png){ #fig:051 width=60% }

## Вывод

- В ходе выполнения данной лабораторной работы я изучила методы кодирования и модуляции сигналов с помощью высокоуровнего языка программирования Octave. Определила спектр и параметры сигнала. Продемонстрировала принципы модуляции сигнала на примере аналоговой амплитудной модуляции. Исследовала свойства самосинхронизации сигнала.