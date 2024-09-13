---
## Front matter
title: "Отчёт по лабораторной работе №1"
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

Целью данной работы является изучение методов кодирования и модуляции сигналов с помощью высокоуровнего языка программирования Octave. Определение спектра и параметров сигнала. Демонстрация принципов модуляции сигнала на примере аналоговой амплитудной модуляции. Исследование свойства самосинхронизации сигнала.

# Выполнение лабораторной работы

## Построение графиков в Octave

Запускаем Octave, создаем новый сценарий под названием plot_sin.m. В окне редактора повторяем листинг по построению графика функции y = sin x + 1/3 sin 3x + 1/5 sin 5x на интервале [−10; 10] (рис. [-@fig:001]).

![Листинг файла plot_sin.m](image/1.png){ #fig:001 width=80% }

Запускаем сценарий на выполнение, открывается окно с графиком (рис. [-@fig:002]). В рабочем каталоге появляются файла с графиками в форматах .eps, .png (рис. [-@fig:003]).

![График функций y1 на интервале −10; 10](image/2.png){ #fig:002 width=80% }

![Файлы .eps, .png](image/3.png){ #fig:003 width=80% }

Сохраним сценарий под названием plot_sin_cos.m и изменим его так, чтобы наодном графике располагались отличающиеся по типу линий графики функций y1 = sin x + 1/3 sin 3x + 1/5 sin 5x, y2 = cos x + 1/3 cos 3x + 1/5 cos 5x. Итоговый листинг (рис. [-@fig:004]).

![Листинг файла plot_sin_cos.m](image/4.png){ #fig:004 width=80% }

Запускаем, получаем еще один график (рис. [-@fig:005]).

![График функций y1 и y2 на интервале −10; 10](image/5.png){ #fig:005 width=80% }

## Разложение импульсного сигнала в частичный ряд Фурье

Создадим новый сценарий meandr.m. В кодe зададим начальные значения. Вычислим амплитуду гармоник и заполним массивы гармоник и элементов ряда. Далее задаём массив значений гармоник массив элементов ряда. Для построения в одном окне отдельных графиков меандра с различным количеством гармоник реализуем суммирование ряда с накоплением и воспользуемся функциями subplot и plot для построения графиков. Также экспортируем полученный график в файл в формате .png (рис. [-@fig:006]), (рис. [-@fig:007]).

![Листинг файла meandr.m](image/6.png){ #fig:006 width=80% }

![Меандр через косинусы](image/7.png){ #fig:007 width=80% }

Также реализуем меандр через синусы (рис. [-@fig:008]), (рис. [-@fig:009]).

![Листинг файла meandr.m](image/8.png){ #fig:008 width=80% }

![Меандр через синусы](image/9.png){ #fig:009 width=80% }


## Определение спектра и параметров сигнала

Создадим в рабочем каталоге каталог spectre1 и в нем новый сценарий spectre.m. В коде сценария зададим начальные значения, а также два синусоидальных сигнала разной частоты, построим графики сигналов (рис. [-@fig:010]), (рис. [-@fig:011]).

![Листинг файла spectre.m](image/10.png){ #fig:010 width=80% }

![Графики сигналов разной частоты](image/11.png){ #fig:011 width=80% }

Затем с помощью быстрого преобразования Фурье найдем спектры сигналов, добавив в файл spectre.m код из мануала в ТУИСе. Учитывая реализацию преобразования Фурье, скорректируем график спектра (рис. [-@fig:012]): отбросим дублирующие отрицательные частоты, а также примим в расчёт то, что на каждом шаге вычисления быстрого преобразования Фурье происходит суммирование амплитуд сигналов.

![Листинг файла spectre.m](image/12.png){ #fig:012 width=80% }

Получим следующие графики: график спектров синусоидальных сигналов (рис. [-@fig:013]) и исправленный график спектров синусоидальных сигналов (рис. [-@fig:014]).

![График спектра синусоидальных сигналов](image/13.png){ #fig:013 width=80% }

![Исправленный график спектров синусоидальных сигналов](image/14.png){ #fig:014 width=80% }

Найдем спектр суммы рассмотренных сигналов, создадим каталог spectr_sum и в нем spectre_sum.m (рис. [-@fig:015]), (рис. [-@fig:016]).

![Листинг файла spectre_sum.m](image/15.png){ #fig:015 width=80% }

![Суммарный сигнал](image/16.png){ #fig:016 width=80% }

В результате должен получится аналогичный предыдущему результат (рис. [-@fig:017]), т.е. спектр суммы сигналов должен быть равен сумме спектров сигналов, что вытекает из свойств преобразования Фурье.

![Спектр суммарного сигнала](image/17.png){ #fig:017 width=80% }

## Амплитудная модуляция

В рабочем каталоге создадим каталог modulation и в нём новый сценарий с именем am.m. Добавим в него код из мануала (рис. [-@fig:018]).

![Листинг файла am.m](image/18.png){ #fig:018 width=80% }

В результате получаем, что спектр произведения представляет собой свертку спектров (рис. [-@fig:019]), (рис. [-@fig:020]).

![Сигнал и огибающая при амплитудной модуляции](image/19.png){ #fig:019 width=80% }

![Спектр сигнала при амплитудной модуляции](image/20.png){ #fig:020 width=80% }

## Кодирование сигнала. Исследование свойства самосинхронизации сигнала

В рабочем каталоге создадим каталог coding и в нём файлы main.m, maptowave.m, unipolar.m, ami.m, bipolarnrz.m, bipolarrz.m, manchester.m, diffmanc.m, calcspectre.m.

В окне интерпретатора команд проверяем, установлен ли пакет расширений signal: pkg list. Так как он не установлен, то устанавливаем его: pkg list -forge и pkg install control signal (рис. [-@fig:021]).

![Проверка правильности установки пакета signal](image/21.png){ #fig:021 width=80% }

В файле main.m подключаем пакет signal и задаем входные кодовые последовательности (рис. [-@fig:022]).

![Задаем входные кодовые последовательности](image/22.png){ #fig:022 width=80% }

Затем в этом же файле пропишем вызовы функций для построения графиков модуляций кодированных сигналов для кодовой последовательности data (рис. [-@fig:023]).

![Вызовы функций для посторения модуляций кодированных сигналов кодовой последовательности data](image/23.png){ #fig:023 width=80% }

Пропишем вызовы функций для построения графиков модуляций кодированных сигналов для кодовой последовательности data_sync (рис. [-@fig:024]).

![Вызовы функций для посторения модуляций кодированных сигналов кодовой последовательности data_sync](image/24.png){ #fig:024 width=80% }

Далее в этом же файле пропишем вызовы функций для построения графиков спектров (рис. [-@fig:025]).

![Вызовы функций для посторения графиков спектров](image/25.png){ #fig:025 width=80% }

В файле maptowave.m пропишем функцию, которая по входному битовому потоку строит график сигнала (рис. [-@fig:026]).

![Листинг файла maptowave.m](image/26.png){ #fig:026 width=80% }

В файлах unipolar.m (рис. [-@fig:027]), ami.m (рис. [-@fig:028]), bipolarnrz.m (рис. [-@fig:029]), bipolarrz.m (рис. [-@fig:030]), manchester.m (рис. [-@fig:031]), diffmanc.m (рис. [-@fig:032]) пропишем соответствующие функции преобразования кодовой последовательности data с вызовом функции maptowave для построения соответствующего графика.

![Листинг файла unipolar.m](image/27.png){ #fig:027 width=80% }

![Листинг файла ami.m](image/28.png){ #fig:028 width=80% }

![Листинг файла bipolarnrz.m](image/29.png){ #fig:029 width=80% }

![Листинг файла bipolarrz.m](image/30.png){ #fig:030 width=80% }

![Листинг файла manchester.m](image/31.png){ #fig:031 width=80% }

![Листинг файла diffmanc.m](image/32.png){ #fig:032 width=80% }

В файле calcspectre.m пропишем функцию построения спектра сигнала (рис. [-@fig:033]).

![Листинг файла calcspectre.m](image/33.png){ #fig:033 width=80% }

Запустим главный скрипт main.m. В каталоге signal должны быть получены файлы с графиками кодированного сигнала (рис. [-@fig:034]-[-@fig:039]), в каталоге sync — файлы с графиками, иллюстрирующими свойства самосинхронизации (рис. [-@fig:040]-[-@fig:045]), в каталоге spectre — файлы с графиками спектров сигналов (рис. [-@fig:046]-[-@fig:051]).

![Униполярное кодирование](image/34.png){ #fig:034 width=80% }

![Кодирование AMI](image/35.png){ #fig:035 width=80% }

![Кодирование NRZ](image/36.png){ #fig:036 width=80% }

![Кодирование RZ](image/37.png){ #fig:037 width=80% }

![Манчестерское кодирование](image/38.png){ #fig:38 width=80% }

![Дифференциальное манчестерское кодирование](image/39.png){ #fig:039 width=80% }

![Униполярное кодирование: нет самосинхронизации](image/40.png){ #fig:040 width=80% }

![Кодирование AMI: самосинхронизация при наличии сигнала](image/41.png){ #fig:041 width=80% }

![Кодирование NRZ: нет самосинхронизации](image/42.png){ #fig:042 width=80% }

![Кодирование RZ: есть самосинхронизация](image/43.png){ #fig:043 width=80% }

![Манчестерское кодирование: есть самосинхронизация](image/44.png){ #fig:044 width=80% }

![Дифференциальное манчестерское кодирование: есть самосинхронизация](image/45.png){ #fig:045 width=80% }

![Униполярное кодирование: спектр сигнала](image/46.png){ #fig:046 width=80% }

![Кодирование AMI: спектр сигнала](image/47.png){ #fig:047 width=80% }

![Кодирование NRZ: спектр сигнала](image/48.png){ #fig:048 width=80% }

![Кодирование RZ: спектр сигнала](image/49.png){ #fig:049 width=80% }

![Манчестерское кодирование: спектр сигнала](image/50.png){ #fig:050 width=80% }

![Дифференциальное манчестерское кодирование: спектр сигнала](image/51.png){ #fig:051 width=80% }

# Выводы

В ходе выполнения данной лабораторной работы я изучила методы кодирования и модуляции сигналов с помощью высокоуровнего языка программирования Octave. Определила спектр и параметры сигнала. Продемонстрировала принципы модуляции сигнала на примере аналоговой амплитудной модуляции. Исследовала свойства самосинхронизации сигнала.



