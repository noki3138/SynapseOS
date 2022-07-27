# Стиль кода, документации и коммитов

## Содержание

1. Код
2. Документация
3. Коммиты

## Код

### Комментарии

Вы можете использовать либо // либо /**/, однако // намного предпочтительнее.
Всегда отделяйте // от тела комментария одним пробелом.
Комментарии должны быть на русском языке.
В начало каждого файла вставляйте шапку с лицензией ("Авторы" используется когда авторов много):

```C
/*
    Автор: Арен Елчинян. Распространяется по лицензии GNU GPL 3.0
    Имя файла:  char.c
    Описание:   Программа для теста ввода
*/
```

Комментарии к объявлению функции должны описывать использование функции (кроме самых очевидных случаев). 
Комментарии к определению функции описывают реализацию.
Ко всем глобальным переменным следует писать комментарий о их назначении и (если не очевидно) почему они должны быть глобальными. Например:

```C
// Максимальный размер строки для имени пользователя
const uint8_t username_max_name_lenght = 255;
```

Комментируйте реализацию функции или алгоритма в случае наличия неочевидных, интересных, важных кусков кода.

Обращайте внимание на пунктуацию, орфографию и грамматику: намного проще читать грамотно написанные комментарии.

### Переменные

Название переменной должно четко описывать назначение.
Названия переменных записываются в нижнем регистре, а слова в названиях отделяются нижним подчеркиванием.
Название глобальных переменных имеет синтаксис: %имя файла%_%имя переменной%.
Объявляйте переменные в начале функции. Если это глобальные переменные, то в начале файла.
По возможности инициализируйте переменные при объявлении. Численные с помощью нуля, указатели — NULL.
Лучше использовать явные размеры: вместо int - int32_t, вместо char - int8_t и тд.

```C
// Правильное объявление переменных

uint32_t hello_size = 14; // Размер строки + 0 в конце
const uint8_t hello_string[] = "Hello, World!";
void *hello_ptr = NULL;
```

```C
// Неправильное объявление переменных

int q; // Не понятно, что за q
long myvar[] = "1234567"; // Тип данных слишком большой
void *trash; // В указателе при инициализации будет мусор
```

### Циклы

i, j, k — стандартные названия для итераторов цикла.
Соблюдайте однородность переноса скобок.
Тип данных используемых в цикле for должен быть указан в самом цикле.

```C
// Правильный цикл

uint8_t my_array[256];  // Массив для тестирования циклов

// Заполняем массив значениями
for (uint8_t i = 0; i < 256; ++i) {
    my_array[i] = i;    // Записываем в массив по индексу i данные
}
```

```C
// Неправильный цикл

int my_array[256];  // Тип данных не соответствует

size_t i;   // 1. Неявный размер 2. Объявление вне цикла

for (
    ; i < 1000; i = i + 1
) { // Выход за пределы массива, убогая реализация инкремента
    my_array[i] = i * 40; // Выход за пределы типа данных
    }
```

## Документация

Документация должна давать описание каждой функции, константы, глобальной переменной, типа данных, системной функции и тд.
Документирование в комментариях приветствуется, так как используется doxygen.
Документацию желательно хранить в виде markdown.

## Коммиты