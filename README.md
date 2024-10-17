# ed-regex-theory

![type-of-regex-PhpStorm](https://github.com/user-attachments/assets/c69980c1-79e8-47f7-8cdd-bff8eda5d274)


Виды Lookbehind и Lookahead:

- Positive Lookbehind ```(?<=...)```
- Negative Lookbehind ```(?<!...)```
- Positive Lookahead ```(?=...)```
- Negative Lookahead ```(?!...)```

## Подробно о каждом с примерами:

### 1. Positive Lookbehind ```(?<=...)```

Ищет совпадение, только если перед ним есть указанный паттерн.

- Пример: Найти слово "world", которое следует после "hello".

- Регулярное выражение: (?<=hello\s)world
        Строка: "hello world" — Совпадение будет, потому что "world" следует после "hello ".
        Строка: "hi world" — Совпадения не будет, потому что перед "world" нет "hello".

 Использование: Полезно, когда нужно убедиться, что перед текущим совпадением есть определённый текст, но сам этот текст не включать в результат.

### 2. Negative Lookbehind (?<!...)

Ищет совпадение, только если перед ним нет указанного паттерна.

- Пример: Найти слово "world", которое не следует после "hello".

- Регулярное выражение: (?<!hello\s)world
        Строка: "hi world" — Совпадение будет, так как перед "world" нет "hello".
        Строка: "hello world" — Совпадения не будет, потому что "world" следует за "hello".

    Использование: Полезно, когда нужно найти совпадение, если определённого текста перед ним нет.

### 3. Positive Lookahead (?=...)

Ищет совпадение, только если за ним следует указанный паттерн.

- Пример: Найти "hello", за которым следует "world".

- Регулярное выражение: hello(?=\sworld)
        Строка: "hello world" — Совпадение будет, так как за "hello" следует "world".
        Строка: "hello everyone" — Совпадения не будет, так как за "hello" нет "world".

    Использование: Используется, когда нужно убедиться, что за текущим совпадением идёт определённый текст, но сам этот текст не включать в результат.

### 4. Negative Lookahead (?!...)

Ищет совпадение, только если за ним не следует указанный паттерн.

- Пример: Найти "hello", за которым не следует "world".

- Регулярное выражение: hello(?!\sworld)
        Строка: "hello everyone" — Совпадение будет, так как за "hello" нет "world".
        Строка: "hello world" — Совпадения не будет, так как за "hello" идёт "world".

    Использование: Полезно, когда нужно найти совпадение, если определённого текста за ним нет.

## Примеры с практическими задачами:

### Пример 1: Positive Lookbehind

- Найти числа, которые идут после знака #.

- Регулярное выражение: (?<=#)\d+
        Строка: "The product code is #1234" — Найдёт 1234, так как оно идёт после #.

### Пример 2: Negative Lookbehind

- Найти все слова, которые не следуют за @.

- Регулярное выражение: (?<!@)\b\w+\b
        Строка: "Send email to @user and contact support" — Найдёт and, contact, support, но не user.

### Пример 3: Positive Lookahead

- Найти все цифры, за которыми следует буква a.

- Регулярное выражение: \d(?=a)
        Строка: "1a 2b 3a" — Найдёт 1 и 3, так как они стоят перед a.

### Пример 4: Negative Lookahead

- Найти все слова, за которыми не следует !.

- Регулярное выражение: \b\w+\b(?!\!)
        Строка: "Hello! How are you" — Найдёт How, are, и you, но не Hello.

## Особенности и Ограничения:

Lookbehind утверждения могут иметь ограничения в некоторых движках регулярных выражений (например, в некоторых случаях не поддерживают переменную длину шаблона).

Lookahead утверждения обычно более гибкие и поддерживаются во многих движках регулярных выражений, включая JavaScript, Python, PHP, и другие.
