# Отчёт по лабораторной работе №11 по курсу «Фундаментальная информатика»

<b>Студент группы:</b> <ins>М8О-108Б-22, Немкова Анастасия Романовна, № по списку 14</ins>

<b>Контакты e-mail:</b> <ins>nastya.nemkova.04@mail.ru<ins>

<b>Работа выполнена:</b> «12» <ins>ноября</ins> <ins>2022</ins>

<b>Преподаватель:</b> <ins>асп. каф.806 Сахаров Никита Александрович</ins>

<b>Отчет сдан</b> «12» <ins>ноябрь</ins> <ins>2022</ins> г., <b>итоговая оценка</b> <ins>

<b>Подпись преподавателя:</b> ___________

**1. Тема**
  
Обработка последовательности литер входного текстового файла. Простейшие приёмы лексического анализа. Диаграммы состояний и переходов. 

**2. Цель работы**

Составить программу на языке Си, выполняющую анализ и обработку вводимого текста в соответствии с заданием.

**3. Задание**

Подсчитать контрольные суммы всех слов исходного текста.

**4. Оборудование**

Процессор: AMDRYZEN 7 5800H 3.20GHz ОП 16 ГБ

НDD: 952 ГБ

Монитор: 3840 × 2400

**5. Программное обеспечение**

Операционная система семейства: LinuxUbuntu, версия 22.04.1 LTS

Интерпретатор команд: bash, версия 5.0.17(1)

Система программирования: gcc

Редактор текстов: emacs

**6. Идея, метод, алгоритм решения задачи**



**7. Сценарий выполнения работы**


Код программы:

```
#include <stdio.h>
#include <ctype.h>
#include <stdlib.h>

unsigned int max_size = 100;

unsigned long big_num() {
    unsigned long factor = 1;
    factor = factor * 1103515245;
    return (factor);
}

unsigned long control_sum(const unsigned char word[], unsigned int length) {
    unsigned long res = 0;
    for (int i = 0; i < length; i++) {
        res += word[i] * big_num() % 15250;
    }
    return res;
}

void print(const unsigned char word[], unsigned int length) {
    for (unsigned int i = 0; i < length; ++i) {
        printf("%c", word[i]);
     }
    printf(": %lu\n", control_sum(word, length));
}

void processing_string() {
    unsigned char *curr_word = malloc(sizeof(char) * max_size); // текущее слово
    unsigned int len = 0; // длина слова (от 0)
    int sym;
    sym = getchar();
    while (sym != EOF) {
        if ( sym == '\n' || sym == '\r' || sym == ' ' || sym == '.' || sym == ',' ) {
            if (len) {
                print(curr_word, len);
                len = 0;
            }
        } else {
            if (len == max_size) {
                curr_word = realloc(curr_word, max_size * 2);
                max_size *= 2;
            }
            curr_word[len] = sym;
            ++len;
        }
        if ((sym = getchar()) == EOF) {
            if (len) {
                printf("%s:%lu", curr_word, control_sum(curr_word, len));
                break;
            }
        } else {
            continue;
        }
    }
}

int main() {
    processing_string(); 
    return 0;
}
```

**8. Распечатка протокола**

```

```

**9. Дневник отладки**

| № | Лаб.ИлиДом. | Дата | Время | Событие | Действие по исправлению | Примечание |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | Дом. | 12.11.22 | 13:48 | Написание программы на Си | - | - |

**10. Замечания автора по существу работы**

**11. Выводы**

В ходе выполнения лабораторной работы были получены навыки по написанию программы для анализа вводимого текста. Были изучены создание массивов, функции malloc и realloc, управляющие символы. Было освоено написание кода для вычесления контрольной суммы слов вводимого текста без использования особых хнш-функций 

<b>Подпись студента:</b> ___________