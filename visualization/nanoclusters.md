---
title: Симуляция нанокластеров
description: 
published: true
date: 2022-03-17T18:03:48.646Z
tags: 
editor: markdown
dateCreated: 2022-02-12T15:04:31.017Z
---

# Условие

Многие в детстве проводили опыт: сильно солили воду(получали пересыщенный раствор) и опускали в нее нитку(центр кристаллизации) на несколько дней, после чего на ней наращивались кристаллы соли, которые потом можно достать.

Наша программа, хоть и не в точности, но будет имитировать этот процесс. Пусть есть поле(наша среда), поделенное на клетки. В каждой клетке может находиться молекула $NaCl$. Течение времени в нашей симуляции поделено на "ходы". Каждый "ход" происходит следующее:
1) Молекулы могут подвинуться(влево, вверх, вправо, вниз), или **не двигаться**. Движение выбирается случайно.
2) Когда две молекулы становятся соседями - они перестают двигаться и застывают. Таким образом кристалл "наращивается"

Симуляция завершается по команде от юзера(когда он закроет приложение)

### Дополнительные требования

1) желательно построение структуры классов(класс под клетку, класс под поле, у которого метод "совершить шаг")
2) всю работу с библиотекой визуализации лучше инкапсулировать в отдельную функцию
