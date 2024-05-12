<img src="https://github.com/DmitriMAI/DmitriMAI.github.io/assets/106885046/087ccc17-880c-4f59-96c0-d6db0784745e" width="50%" height="50%">

Документация к языку Friren. Написан на основе языка F#  
Данный язык основан на японском фильме   
"Встреча Фриры в ее бесповоротном пути"  
Вольный перевод от : 葬送のフリーレン  
  
# Авторы проекта  
  
| ФИО | Группа | Вклад  |
|---|---|---|
| Овчинников Дмитрий  | М8О-306Б-21  | Документация, архитектура языка    |
| Лохматов Никита  | М8О-306Б-21  |  Парсер, расширение для vsc, отчёт  |
| Устинов Денис  | М8О-306Б-21  | Интерпретатор  |
| Егор Аббдуллаев  | М8О-306Б-21  | Синтаксическое дерево  |
| Егор Белоусов  | М8О-30*Б-21  |   |

***
Для более удобной работы с языком разработано расширение vs code для подсветки синтаксиса и всплывающих подсказок при наведении.  
## Порядок установки  
![image](https://github.com/DmitriMAI/DmitriMAI.github.io/assets/106885046/fdfde1cf-3da6-4a6a-9d54-b6513372a0e4)  

В `расширениях/extention` выбрать `...`    
В выпадающем окне выбрать `install from VSIX`  
Файл расширения находится по [ссылке](https://github.com/MAILabs-Edu-2024/fp-compiler-lab-team-3/blob/main/frieren/frieren-0.0.1.vsix)

# Блоки
Абсолютно все конструкции в языке Frieren (кроме комментариев) должны быть обёрнуты в
блоки `()`:

```
~
  Возможны несколько вариантов размещения (), выбор зависит от удобства прочтения,
  однако мы советуем оборачивать простые конструкции вроде `cast` в виде `(cast n)`,
  а более сложные в виде:
  (
    for i [0 .. 10] =>
      (cast i)
  )
~


~ № 1 ~
(
    someFunction
)

~ № 2 ~
(someFunction)
```

# Комментарии 
Не все маги способны запомнить всю информацию.  
Важно оставлять заметки  
>Знания — это сила, но понимание — это еще более глубокая сила.

```
~ Line Comment ~

~

Block Comment

~
```

# Вывод в консоль 
Маги должны уметь применять заклинания. Для этого используется функция `cast`

```
(
    cast "Frieren"
)
```

**Вывод:**

```
Frieren
```

# Переменные 
Можно использовать `=`, либо `:` для объявления переменной  
`lt` - Link Trinket. Прикрепить волшебный брелок с магической силой внутри.   
(Теперь он будет висеть вместе с нами)

```
(lt NAME = VALUE)
(lt a = 4.0)
(lt b : 5.0)
(lt str = "str")
(lt boolean = true)

(cast a)
(cast b)
(cast str)
(cast boolean)
```

**Вывод:**

```
4.000000
5.000000
"str"
true
```

# Изменения переменных
Помочь с изменением способен `mut`  
Что означает мутацию состояния нашего брелка.

```
(
  mut a = 10
)

(cast a)
```

**Вывод:**

```
10.000000
```

# Поддержка базовой арифметики
Можно по разному объединять брелки  
Поддерживаются такие операции как :  `+`, `-`, `*`, `/`, `%`

```
(
    cast (+ a b)
)

(
    cast (* a a)
)
```

**Вывод:**

```
15
100.000000
```

# Префиксная запись
Для успешного освоения языка Frieren вы должны привыкнуть к префиксной записи выражений

```
(
    cast (+ 1 4)
)
```

**Вывод:**

```
5.000000
```

# Поддержка базовых булевый операций
Особый тип логических брелков.  
Для операций с ним нужны определенные инструменты.   
Доступны такие как: `&` и `|`

```
(
    cast (& true false)
)

(
    cast (| 1 0)
)
```

**Вывод:**

```
false
true
```

# Поддержка операторов сравнения
Естественно некоторые брелки могут обладать большей силой.  
Необходимо сравнивать магическую силу.  
Есть варианты: `>`, `<`, `==`, `!=`, `>=`, `<=`

```
cast(>= a b)
cast(== 1 2)
cast(!= 1 2)
```

**Вывод:**

```
false
false
true
```

# Поддержка оператора if else  
Маг должен предусмотреть все варианты развития событий. В помощь ему магический разветвлитель
> Будущее формируется выборами, сделанными сегодня

```
(
    if (> a b) =>
        (cast "a > b")
    else =>
        (cast "a < b")
)

/~  if может использоваться в одиночку ~/
(
    if (>= 1 1) =>
        (cast "true")
)
```

**Вывод:**

```
"a > b"
"true"
```

# Поддержка цикла for и while
Возможно мы хотим сделать четкий порядок обряда.  
И знаем, что придется повторять несколько действий снова и снова.  
Для таких случаев есть заклинения в помощь нам.  
Убейте цикл с помощью `kill`    
Поддерживайте цикл в рабочем состоянии с помощью `heal`

```
(
    for i [0 .. 3] =>
        (cast i)
)

(
    while true =>
        ((cast "STOP!")
        kill)
)
```

**Вывод:**

```
0.000000
1.000000
2.000000
"STOP!"
```

# Cоставление сложных функций
Конечно же из собранных ингредиентов можно подготовить намного более сильное `spell` для следующего приключения.

```
(
    spell printNum {num} =>
        (cast num)
)

~ Можно использовать дальше в коде с помощью ~
(printNum 100)
```

**Вывод:**

```
100.000000
```

# Поддержка работы с файлами
>Опытные маги всегда знают все наперед. Поэтому у них составлены магические гримуары.  
>Именно те маги, которые ими пользовались, остались жить дольше других.

```
~ Получение выходных данных ~
(cast (readGrim "./tests/input.txt") )

~ Перенаправление вывода ~
(writeGrim "./tests/output.txt" "Wow!")
```

**Вывод:**

```
"Hello, World!"
```

# Самая красивая магия
Создайте поле цветов

```
(flowerField)
```

**Вывод:**

```
🌻🪻🌹🪻🌻🪻🌷🪻🌹🪻🌻🪻🌷
```

# Факториал через рекурсию

```
(
    spell factRec {n1} =>
    (
        if (== n1 0) =>
            1
        else =>
            (* n1 (factRec (- n1 1)))
    )
)

(cast (factRec 5))
```

**Вывод:**

```
120.000000
```

# Проверка числа на чётность

```
(
    spell isEven {n2} =>
    (
        if (== (% n2 2) 0) =>
            true
        else =>
            false
    )
)

(cast (isEven 152))
```

**Вывод:**

```
true
```

# Сумма чисел с помощью рекурсии

```
(
    spell sumRec {n3} =>
    (
        if (== n3 1) =>
            1
        else =>
            (+ n3 (sumRec (- n3 1)))
    )
)

(cast (sumRec 10))
```

**Вывод:**

```
55.000000
```
