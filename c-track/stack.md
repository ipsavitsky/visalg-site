---
title: Стек
description: 
published: true
date: 2022-03-17T18:03:42.859Z
tags: 
editor: markdown
dateCreated: 2022-02-10T10:30:11.140Z
---

# Условие
> Стек -  абстрактный тип данных, представляющий собой список элементов, организованных по принципу LIFO (англ. last in — first out, «последним пришёл — первым вышел»).
{.is-info}

(взято из [соответствующей статьи на Википедии](https://ru.wikipedia.org/wiki/%D0%A1%D1%82%D0%B5%D0%BA))
Требуется реализовать **библиотеку**, программный интерфейс которой состоит из операций `push()` и `pop()`, которые в соответствии со стратегией LIFO добавляют и убирают элемент из стека соответственно. Можно считать стек типа `int`. Размер стека задается при создании, но потом может уменьшаться/расширяться автоматически в зависимости от того, сколько элементов сейчас находится в стеке.

## Дополнительные механизмы безопасности в стеке
### Канарейки
Пусть в какой-то памяти лежит стек. Какая-то другая программа затирает часть нашего стека какими-то своими данными. Самый простой способ обнаружить такое нарушение - поставить какой-то заданный набор байт слева и справа от стека. Т.е. с канарейками ваш стек будет выглядеть как-то так:
```
канарейка | элемент1 | элемент2 | элемент3 | канарейка
```
Добавление канарейки лежит соответственно на функциях управления стеком(`push()`, `pop()` и прочие непотребства). Для проверки наличия канареек можно добавить функцию `bool verify_canary(stack*)`. Значение канарейки можно хранить в самом стеке


### Хеш
Для того, чтобы вычислить последующие непотребства, которые с нашим стеком могли произойти - можно использовать хеш-функции. В нашем курсе достаточно понимать, что это функции, которые создают что-то, что называется хеш(число или последовательность букв и чисел) из сообщений(в нашем случае сообщения это стеки). Важно понимать, что для *похожих* стеков хеш функция может давать сильно разнящийся результат. При любом изменении стека надо бновлять значение хеша и сохранять его в стеке. Также, стоит добавить функцию `bool verify_hash(stack*)`, которая вычисляет хеш текущего состояния стека и сравнивает его с сохраненным значением 
# Ввод

```c
#include <stdio.h>
#include "stack.h" // ваш стек

int main(){
	stack *st = init_stack(5); // создали стек на 5 элементов
	stack_push(st, 13); // запушили 13
	stack_push(st, 20); // запушили 20, стек выглядит как | 13 | 20 | 
	int res = stack_pop(st); // попаем последний элемент, т.е. 20
	print("%d", &res);
	if(!stack_verify(st)){ // stack_verify() проверяет сразу и канарейку, и стек
		return 1;
	}
	return 0;
}
```

# Вывод

```
20
```