# Алгоритмы исследования операций, лабораторная работа 2

## ТЗ:

Реализовать и сравнить алгоритмы для решения knapsack 0-1 problem.

1) 2-approx алгоритм.
2) ДП на весах или ДП на стоимостях (был выбран ДП на весах).
3) Метод ветвей и границ используя задачу LP или используя только 1 предмет (был выбран алгоритм используя 1 предмет).
4) PTAS или FPTAS (был выбран PTAS).

Необходимо сравнить время работы алгоритма, количество промежуточных решений и итоговый profit рюкзака.

## Структура файлов

- tests - тесты (в директориях тесты, в tests.py парсинг этих тестов)
- two_approx.py - реализация 2-approximation
- dp_on_weights.py - реализация ДП на весах
- ptas.py - реализация PTAS
- branch_and_bound.py - реализация алгоритма, используя 1 предмет на каждой итерации.
- main.py - запускает тестов и выводит метрики для каждого алгоритма.

## Итоги

|                                                 | p01                            | p02                    | p03                    | p04                    | p05                      | p06                    | p07                                           |
|:------------------------------------------------|:-------------------------------|:-----------------------|:-----------------------|:-----------------------|:-------------------------|:-----------------------|:----------------------------------------------|
| Capacity                                        | 165                            | 26                     | 190                    | 50                     | 104                      | 170                    | 750                                           |
| Optimal profit                                  | 309                            | 51                     | 150                    | 107                    | 900                      | 1735                   | 1458                                          |
| Optimal choice                                  | [1, 1, 1, 1, 0, 1, 0, 0, 0, 0] | [0, 1, 1, 1, 0]        | [1, 1, 0, 0, 1, 0]     | [1, 0, 0, 1, 0, 0, 0]  | [1, 0, 1, 1, 1, 0, 1, 1] | [0, 1, 0, 1, 0, 0, 1]  | [1, 0, 1, 0, 1, 0, 1, 1, 1, 0, 0, 0, 0, 1, 1] |
| DP on weights profit                            | 309                            | 51                     | 150                    | 107                    | 900                      | 1735                   | 1458                                          |
| DP on weights weight                            | 165                            | 26                     | 190                    | 50                     | 104                      | 169                    | 749                                           |
| DP on weights choice                            | [1, 1, 1, 1, 0, 1, 0, 0, 0, 0] | [0, 1, 1, 1, 0]        | [1, 1, 0, 0, 1, 0]     | [1, 0, 0, 1, 0, 0, 0]  | [1, 0, 1, 1, 1, 0, 1, 1] | [0, 1, 0, 1, 0, 0, 1]  | [1, 0, 1, 0, 1, 0, 1, 1, 1, 0, 0, 0, 0, 1, 1] |
| DP on weights number of intermediate solutions  | 1826                           | 162                    | 1337                   | 408                    | 945                      | 1368                   | 12016                                         |
| DP on weights time                              | 0.00018401145935058593         | 1.8167495727539063e-05 | 0.0001320362091064453  | 4.801750183105469e-05  | 0.00011119842529296874   | 0.00013980865478515624 | 0.0014986515045166016                         |
| 2-approx profit                                 | 309                            | 47                     | 146                    | 102                    | 858                      | 1478                   | 1441                                          |
| 2-approx weight                                 | 165                            | 23                     | 179                    | 48                     | 97                       | 140                    | 740                                           |
| 2-approx choice                                 | [1, 1, 1, 1, 0, 1, 0, 0, 0, 0] | [1, 1, 0, 0, 0]        | [1, 1, 0, 1, 0, 0]     | [1, 1, 0, 0, 1, 1, 0]  | [1, 1, 0, 1, 1, 1, 1, 1] | [1, 1, 1, 0, 0, 0, 0]  | [1, 1, 1, 1, 1, 1, 1, 0, 0, 1, 0, 0, 0, 0, 0] |
| 2-approx number of intermediate solutions       | 2                              | 2                      | 2                      | 2                      | 2                        | 2                      | 2                                             |
| 2-approx time                                   | 3.4809112548828124e-06         | 1.5735626220703124e-06 | 1.3828277587890625e-06 | 1.7642974853515626e-06 | 2.002716064453125e-06    | 1.811981201171875e-06  | 3.1948089599609376e-06                        |
| PTAS approx profit                              | 309                            | 51                     | 150                    | 107                    | 900                      | 1735                   | 1448                                          |
| PTAS approx weight                              | 165                            | 26                     | 190                    | 50                     | 104                      | 169                    | 749                                           |
| PTAS approx choice                              | [1, 1, 1, 1, 0, 1, 0, 0, 0, 0] | [0, 1, 1, 1, 0]        | [1, 1, 0, 0, 1, 0]     | [1, 0, 0, 1, 0, 0, 0]  | [1, 0, 1, 1, 1, 0, 1, 1] | [0, 1, 0, 1, 0, 0, 1]  | [1, 1, 1, 1, 0, 0, 0, 0, 1, 0, 0, 1, 0, 1, 1] |
| PTAS approx number of intermediate solutions    | 385                            | 30                     | 56                     | 98                     | 162                      | 98                     | 1940                                          |
| PTAS approx time                                | 0.00031580924987792967         | 2.6607513427734374e-05 | 4.978179931640625e-05  | 9.698867797851563e-05  | 0.00021224021911621095   | 9.160041809082031e-05  | 0.0031976222991943358                         |
| Branch and cut profit                           | 309                            | 51                     | 150                    | 107                    | 900                      | 1735                   | 1458                                          |
| Branch and cut weight                           | 165                            | 26                     | 190                    | 50                     | 104                      | 169                    | 749                                           |
| Branch and cut choice                           | [1, 1, 1, 1, 0, 1, 0, 0, 0, 0] | [0, 1, 1, 1, 0]        | [1, 1, 0, 0, 1, 0]     | [1, 0, 0, 1, 0, 0, 0]  | [1, 0, 1, 1, 1, 0, 1, 1] | [0, 1, 0, 1, 0, 0, 1]  | [1, 0, 1, 0, 1, 0, 1, 1, 1, 0, 0, 0, 0, 1, 1] |
| Branch and cut number of intermediate solutions | 456                            | 36                     | 56                     | 32                     | 78                       | 160                    | 5600                                          |
| Branch and cut time                             | 0.0005254268646240235          | 4.477500915527344e-05  | 5.76019287109375e-05   | 3.933906555175781e-05  | 8.296966552734375e-05    | 0.00019164085388183593 | 0.0075496196746826175                         |
